# Ǩ��

<p class="uk-article-lead">���в����װ������ʱʹ��Ǩ��</p>

���(������)�������ã����û򲻰�װ����״̬�ı�ʱ���������Ҫ�޸�������ݿ�ģʽ�������������Զ������Ҫ��������һ�㣬�������������԰����㡣

| ����  | ����         |
|--------|-------------|
| `enable`     | ��װ���������ʱ���� |
| `disable`    | �����ں�̨���ò��ʱ��������������ʱ���� |
| `uninstall`  | ����Ӻ�̨д�ڲ��ʱ���� |

## ����

��ȷ�����Ĳ����һ�������� `Pagekit\Extension\Extension` ������ `enable` Ĭ�ϲ����κζ�����ͨ������ `enable` �������Լ��Ĵ���

```php
<?php

namespace Pagekit\Hello;

use Pagekit\Extension\Extension;


class HelloExtension extends Extension
{
    public function enable()
    {
        // your migration code here
    }
}
```

������������ĳЩ����������£�ʹ��`Migrator`�Զ�����������κ�Ǩ�ƽű�

```php
public function enable()
{
  if ($version = $this['migrator']->run('extension://hello/migrations', $this['option']->get('hello:version'))) {
    $this['option']->set('hello:version', $version);
  }
}
```

Ǩ�ƹ��߻���`/migrations`�в�����Ĳ��, �����еĲ�����µ���`hello:version`���ߵĵȼ�, ����������Щ�ű�����`$version`������ֵ����ͱ�ʾǨ���Ѿ����

### Ǩ���ļ� 

Ǩ���ļ�ͨ��λ��������� `/migrations` �ļ����ﲢ����һ����˳�� A Ǩ���ļ�ͨ����ʱ��+�Զ������Ƶķ�ʽ����: `YYYY-MM-DD_some_name.php` (���� `0000-00-00_init.php`).

��Ǩ���ļ���, ������Ϊ���Ĵ��뽨��һ����`up` �� `down`�հ����������飬ͨ��ʹ�� `use ($app)`,�����Է������е�Ӧ�÷���, ��������`db`����������ݿ⡣

```php
<?php

return [

    'up' => function() use ($app) {
        // your code here ...
    },

    'down' => function() use ($app) {
        // your code here ...
    }

];

```

�ںܶ�����£��㲻��ִ�� `down` ����,��������ʵ�ֽ����Ĳ�����

## ����

Pagekit�����޸����������ı������������չ�ں�̨��*disabled*��*removed*ʱ���㽫���ò��޸����ݿ⣬�����������Լ��ı䡣

�����Ĳ��������ʱ(�û���������������), ��������`Extension` �������� `disable` ����, ��������`enable`�����ķ���һ��.

```php
<?php
namespace Pagekit\Hello;

use Pagekit\Extension\Extension;

class HelloExtension extends Extension
{
    public function disable()
    {
        // your code here
    }
}
```

## ж��

��ж�ز��ʱ����Ӧ��ɾ�����иò���½������ݱ�����ĳЩ����£����ϣ������ԭ�������ݲ����°�װ�����������Σ��������ľ�����

�������Ѿ��µ���һ�����п��Կ���ֱ�ӽ��� `uninstall` �ķ���

```php

class HelloExtension extends Extension
{
    public function uninstall()
    {
        $util = $this['db']->getUtility();
        $util->dropTable('@hello_greetings');
    }
}
```
