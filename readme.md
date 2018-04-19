# MySQL2Phinx

A simple cli php script to generate a [phinx](https://github.com/robmorgan/phinx) migration from an existing MySQL database.

## Usage

```
$ php mysql2phinx.php [database] [user] [password] > migration.php
```

Will create an initial migration class in the file `migration.php` for all tables in the database passed. 

## Example

```
$table = $this->table('downs', ['collation' => 'utf8mb4_unicode_ci']);
$table
    ->addColumn('category_id', 'integer', ['limit' => MysqlAdapter::INT_SMALL, 'signed' => false, 'default' => 0])
    ->addColumn('title', 'string', ['limit' => 100])
    ->addColumn('text', 'text', ['null' => true])
    ->addColumn('user_id', 'integer')
    ->addColumn('created_at', 'integer')
    ->addColumn('type', 'enum', ['values' => ['ban','unban','change']])
    ->addColumn('count_comments', 'integer', ['limit' => MysqlAdapter::INT_MEDIUM, 'signed' => false, 'default' => 0])
    ->addColumn('rating', 'integer', ['limit' => MysqlAdapter::INT_MEDIUM, 'signed' => false, 'default' => 0])
    ->addColumn('rated', 'integer', ['limit' => MysqlAdapter::INT_MEDIUM, 'signed' => false, 'default' => 0])
    ->addColumn('loads', 'integer', ['limit' => MysqlAdapter::INT_MEDIUM, 'signed' => false, 'default' => 0])
    ->addColumn('active', 'boolean', ['default' => 0])
    ->addColumn('updated_at', 'integer', ['null' => true])
    ->addIndex('category_id')
    ->addIndex('created_at')
    ->addIndex('text', ['type' => 'fulltext'])
    ->addIndex('title', ['type' => 'fulltext'])
    ->addIndex(['user_id', 'created_at'], ['name' => 'user_created'])
    ->create();
```

