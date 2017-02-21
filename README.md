# Magallanes TYPO3 Tasks #

[![Build Status](https://travis-ci.org/teamneusta/magallanes-task-typo3.svg?branch=master)](https://travis-ci.org/teamneusta/magallanes-task-typo3)
[![Coverage Status](https://coveralls.io/repos/github/teamneusta/magallanes-task-typo3/badge.svg?branch=master)](https://coveralls.io/github/teamneusta/magallanes-task-typo3?branch=master)

### What's Magallanes TYPO3 Tasks? ###

**Magallanes TYPO3 Tasks** are tasks for easy deployment with Magallaes 3.

### Installing ###

Simply add the following dependency to your project’s composer.json file:

```json
    "require": {
        "teamneusta/magallanes-task-typo3": "^1.0"
    }
```
Finally you can use **Magallanes TYPO3 Tasks** in your mage.yml


## Tasks ##

### Permission task ###

This task set all necessary permission for TYPO3

```yaml
   post-release:
       - 'TeamNeusta\Magallanes\Task\TYPO3\PermissionsTask'
```

### TYPO3 console tasks ###

Set path to console:

```yaml
    typo3:
        console: vendor/helhum/typo3-console/Scripts/typo3cms
```

#### TYPO3 cache flush task ####

This task flushed the TYPO3 cache by [helhum/typo3-console](https://github.com/helhum/typo3_console)

Default usage:
```yaml
    on-deploy:
        - 'TeamNeusta\Magallanes\Task\TYPO3\Console\CacheFlushTask'
```

Force flush by inline definition:
```yaml
    on-deploy:
        - 'TeamNeusta\Magallanes\Task\TYPO3\Console\CacheFlushTask': { force-flush-cache: true }
```

Force flush by global definition:
```yaml
    typo3:
        force-flush-cache: true
    on-deploy:
        - 'TeamNeusta\Magallanes\Task\TYPO3\Console\CacheFlushTask'
```

#### TYPO3 database update schema task ####

This task update the database schema for TYPO3 by [helhum/typo3-console](https://github.com/helhum/typo3_console)

Default usage (\*.add,\*.change):
```yaml
    on-deploy:
        - 'TeamNeusta\Magallanes\Task\TYPO3\Console\DatabaseUpdateSchemaTask'
```

Update database schema by inline definition:
```yaml
    on-deploy:
        - 'TeamNeusta\Magallanes\Task\TYPO3\Console\DatabaseUpdateSchemaTask': { database-update-schema-mode: 'destructive' }
```

Update database schema by global definition:
```yaml
    typo3:
        database-update-schema-mode: 'destructive'
    on-deploy:
        - 'TeamNeusta\Magallanes\Task\TYPO3\Console\DatabaseUpdateSchemaTask'
```
