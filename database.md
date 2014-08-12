# Database

pagekit�Ѿ��ṩ�����ݲ�ķ�װ,����Ҫ����ԭ����pdo.

## ����

���ݿ�����ö������� `config.php`�ļ���. Pagekit֧��`mysql`��`sqlite`.

```
'database' => [
    'connections' => [
      'mysql' => [
        'host' => 'localhost',
        'user' => 'root',
        'password' => 'PASSWORD',
        'dbname' => 'DATABASE',
        'prefix' => 'PREFIX_',
      ],
    ],
  ],
  ...
```

## Working with database prefixes

pagekit�ı�Ĭ���ڰ�װʱ��������ǰ׺. ����붯̬�ĵ����������ǰ׺�ı���,�����ڱ���ǰ����`@`������Ϊռλ.ͬʱ��Ϊ����,Ӧ���ڱ���ǰ������չ������, ����:`foobar`��չ��*options*����Ա�ʾΪ: `@foobar_option`

## ���ݿ�ʵ�ù���

�����ͨ��pagekit�ṩ�����ݿ������������������ݿ�(��������).

```
$util = $this['db']->getUtility();
```

## ���ĳ�ű��Ƿ����

```
if ($util->tablesExist(['@table1', '@table2'])) {
  // tables exists
}
```

## ������

ʹ�� `Utility::createTable($table, \Closure $callback)` ��������, �ص������ĵ�һ������������`Doctrine\DBAL\Schema\Table`��һ��ʵ��.

```
$util->createTable('@foobar_option', function($table) {
    $table->addColumn('id', 'integer', ['unsigned' => true, 'length' => 10, 'autoincrement' => true]);
    $table->addColumn('name', 'string', ['length' => 64, 'default' => '']);
    $table->addColumn('value', 'text');
    $table->addColumn('autoload', 'boolean', ['default' => false]);
    $table->setPrimaryKey(['id']);
    $table->addUniqueIndex(['name'], 'OPTION_NAME');
});
```

## Insert

TODO

## Select

TODO

## Joins

TODO

## Migrations

TODO

## ORM

TODO
