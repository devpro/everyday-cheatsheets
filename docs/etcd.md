# etcd (CNCF incubating project)

> A distributed, reliable key-value store for the most critical data of a distributed system

Reference: [etcd.io](https://etcd.io/), [GitHub](https://github.com/etcd-io/etcd), [docs](https://etcd.io/docs/v3.4.0/), [API](https://etcd.io/docs/v3.4.0/learning/api/)

## Quick start

### Installation

Several options:

- Grab a pre-built binary from the [releases page](https://github.com/etcd-io/etcd/releases/)

```bash
cd etcd-v3.4.12
etcd
```

- Build from the source (written in Go)

```bash
# make sure Go is installed

# clone the repository
git clone https://github.com/etcd-io/etcd.git
cd etcd

# use the build script
./build
```

- Docker (review latest version from [releases page](https://github.com/etcd-io/etcd/releases/))

```bash
# In Windows we can't set the data directory (--mount type=bind,source=//d/ProgramData/etcd-data.tmp,destination=/etcd-data) because etcd checks folder permissions (700 versus 777), see https://github.com/etcd-io/etcd/blob/release-3.4/pkg/fileutil/fileutil.go

docker run -p 2379:2379 -p 2380:2380 --name etcd-gcr-v3.4.12 gcr.io/etcd-development/etcd:v3.4.12 /usr/local/bin/etcd --name s1 --data-dir /etcd-data --listen-client-urls http://0.0.0.0:2379 --advertise-client-urls http://0.0.0.0:2379 --listen-peer-urls http://0.0.0.0:2380 --initial-advertise-peer-urls http://0.0.0.0:2380 --initial-cluster s1=http://0.0.0.0:2380 --initial-cluster-token tkn --initial-cluster-state new --log-level info --logger zap --log-outputs stderr

docker exec etcd-gcr-v3.4.12 /bin/sh -c "/usr/local/bin/etcd --version"
docker exec etcd-gcr-v3.4.12 /bin/sh -c "/usr/local/bin/etcdctl version"
docker exec etcd-gcr-v3.4.12 /bin/sh -c "/usr/local/bin/etcdctl endpoint health"
docker exec etcd-gcr-v3.4.12 /bin/sh -c "/usr/local/bin/etcdctl put foo bar"
docker exec etcd-gcr-v3.4.12 /bin/sh -c "/usr/local/bin/etcdctl get foo"
docker exec etcd-gcr-v3.4.12 /bin/sh -c "/usr/local/bin/etcdctl del foo"

docker stop etcd-gcr-v3.4.12
docker rm etcd-gcr-v3.4.12
```

### CLI

Command | Action
------- | ------
`etcdctl member list` | Lists all members in the cluster

## Recipes

### Backup & restore

```bash
# for Windows
SET ETCDCTL_API=3

# see https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/
etcdctl snapshot save etcd_snapshot.db
etcdctl --write-out=table snapshot status etcd_snapshot.db

# see https://github.com/etcd-io/etcd/blob/master/Documentation/op-guide/recovery.md#restoring-a-cluster
etcdctl snapshot restore etcd_snapshot.db --name m1 --initial-cluster m1=http://0.0.0.0:2380 --initial-cluster-token etcd-cluster-1 --initial-advertise-peer-urls http://0.0.0.0:2380 # will create m1.etcd folder
etcd --name m1 --data-dir m1.etcd --listen-client-urls http://0.0.0.0:2379 --advertise-client-urls http://0.0.0.0:2379 --listen-peer-urls http://0.0.0.0:2380
```
