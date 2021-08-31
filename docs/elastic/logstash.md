# Logstash

## Configure

### Plugins

* [Redis](https://www.elastic.co/guide/en/logstash/current/plugins-inputs-redis.html)

## Run

### Running on Docker

- Official doc on Running Logstash on Docker on [elastic.co](https://www.elastic.co/guide/en/logstash/current/docker.html)
- Example of a working Docker configuration on [github.com/devpro](https://github.com/devpro/docker-files/tree/master/elastic-stack)
- Configuring Logstash for Docker on [elastic.co](https://www.elastic.co/guide/en/logstash/current/docker-config.html)

### Recipes

#### Replace Timestamp by another field

```json
filter {
  date {
    match => ["@t", "yyyy-MM-dd'T'HH:mm:ss.SSSSSSS'Z'"]
    target => "@timestamp"
  }
}
```

See [plugins-filters-date](https://www.elastic.co/guide/en/logstash/current/plugins-filters-date.html)

### Grok

- [grokdebug](https://grokdebug.herokuapp.com/)

### Examples

- [Logstash Configuration Examples](https://www.elastic.co/guide/en/logstash/current/config-examples.html)
