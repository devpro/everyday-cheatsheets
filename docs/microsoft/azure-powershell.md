# Azure Powershell

## Learn

- [Overview](https://docs.microsoft.com/en-us/powershell/azure/overview)
- [Documentation](https://docs.microsoft.com/en-us/powershell/azure)

## Command lines

Command | Description
--------|------------
`Install-Module -Name Az -AllowClobber` | Install Az Module (from an Admin window)
`Get-InstalledModule -Name Az -AllVersions` | Review the installed version
`Connect-AzAccount` | Connect to your account
`Get-AzSubscription` | List available subscriptions
`Get-AzContext` | Get current context
`Select-AzSubscription -SubscriptionName "xxxx"` | Set the current subscription
`Get-AzResource -ResourceGroupName "xxxx" -ResourceName "yyyyy"` | List resources

### Recipes

- Change the current context: `Get-AzSubscription -SubscriptionId "xxxx-xxxx-xxxx-xxxx" -TenantId "yyyy-yyyy-yyyy-yyyy" | Set-AzContext`
- Get information on a web application: `Get-AzWebApp -name "xxxx" | Format-List`
