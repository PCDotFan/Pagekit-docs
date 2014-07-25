# ����

<p class="uk-article-lead"> һ�������߹����������չ�Ĺ۵㡣</p>

һ������� `theme.php` ��һ����չ�� `extension.php` ��������Զ������������ļ������˹�����ϵͳ�¼���Ƕ�����Լ��Ĵ���Ŀ����ԣ��ļ�����Ҫ�����ǰ����������ݵ��������С�

## ͨ��

�� `theme.php` �� `extension.php` ���ã�

### Main 

�����Զ�����ͼ�������ļ�֮������㻹�д��룬��Ӧ��д `Pagekit\Framework\Theme` (�� `Pagekit\Framework\Extension` )�����ࡣͨ�� `main` ������ָ�������ռ��е����ࡣ
����㲻�������ԣ�Pagekit�����ڲ�����һ�� `Theme` (�� `Extension` )�Ļ�����ʵ����

```php
'main' => Pagekit\\Hello\\HelloExtension
```

### �Զ�װ��

ʹ��[PSR-4](http://www.php-fig.org/psr/psr-4/)���Ѹ��������ռ����Զ�װ�������ࡣ

```php
'autoload' => [
    'Pagekit\\Hello\\' => 'src'
],
```

### ��Դ

 `resources` �����Ǻ��������ؼ��ʵ����С�


| Property  | Description |
|-----------|-------------|
| `export`    | ע��һ������װ��ָ��һ��Ŀ¼�� |
| `overrides` | ��д `extension://` �� `theme://` ���ԵĿ����ԣ���������ϵͳ���Զ�����ͼ�� |


```php
'resources' => [
  'overrides' => [
    ...
  ]
],
```

**ע��** �����ʹ�ÿ����������е� `@url('extension://hello/assets/images/foo.png')` �� `$app['url']->to('extension://hello/assets/images/foo.png')` 
�������ͼ������ͼƬ·����

### ����

Ϊ���������Զ���С���ѡ��������ͼ��Ϊ�����ṩ `settings` ��/�� `widgets` �ؼ�����������Ӧ����ͼ�ļ���
������������һ�����ͣ�С�����һ�� [�����½�] (widgets.md) �����͡�

```php
'settings' => [
    'system'  => 'extension://hello/views/admin/settings.razr'
],
```

## �Զ�������

����������Լ����������ԡ��� `Theme` (�� `Extension`)ʵ���У��㽫��ͨ�� `$this->config` �����������С�ͬ���������ʹ�� `$this->getConfig('colours.background')` 
ͨ����Ƿ�����Ƕ�׵��������С�

```php
'colours' => ['background' => '#ccc', 'text' => '#333'];
```

## Theme

ֻ�� `theme.php` �п��ã�

### λ��

 `positions` ����ʹ������Զ���С���������λ�á�ע�⵽���ֻ������λ�á����������ͼ������Ӧ��Ⱦ���鿴�й� [����] ���½� ��themes.md���˽������Ϣ��

```php
return [
    'positions' => [
        'logo'      => 'Logo',
        'sidebar'   => 'Sidebar',
        'footer'    => 'Footer',
        ...
    ],
    ...
```

## ��չ

ֻ�� `extension.php` �п��ã�

### ������

 `controllers` ���Զ����˿�����·���������ʹ�� [glob] �䷨ (http://php.net/glob)�������Զ�·��ע�ᡣʹ��glob�䷨��һ�����ж��·������������һ���ַ�����

```php
'controllers' => 'src/Controller/*Controller.php'
```

### �˵�

 `menu` ������һ���˵���Ŀ�����С�ÿ��Ԫ�غ���һ�����ص��ַ���ʶ���������չ����/��һ����Ч������ɣ��Է����ж���˵���Ŀ��i.e. `hello` �� `hello: settings` ��
ÿ���˵���Ŀ��һ�������������Ե�����ʶ��

| ����      | ����        |
|-----------|-------------|
| `label`   | �˵���Ŀ��ǩ�� |
| `parent`  | ���˵���Ŀ��ʶ����� |
| `access`  | �г�һ����Ŀ��һ���û��ɼ������Ȩ�ޡ�ע�⣺����Ŀ������ڲ�ִ�з��ʿ��ƣ��˵���Ŀ�Ƿ�ɼ���֮�޹ء�|
| `active`  | ʹ�� [glob](http://php.net/glob) �䷨��ƥ�䵱ǰ�� URL ������, ���һ���˵���Ŀ����Ϊ�� *��Ч��*�� |
| `priority`| ��ѡ������˳��Ĭ��Ϊ0. |

```php
'menu' => [
    'hello' => [
        'label'  => 'Hello',
        'url'    => '@hello/hello',
        'active' => '/admin/hello*',
        'access' => 'hello: manage hellos'
    ]
],
```

### Ȩ��

 `permissions` ���Զ�����һ�����Է�����û����Ȩ���б��ض�ʶ���Ӧ����չ����һ����̵�Ȩ��ʶ����⣨����ð�źͿո���ɡ�һ�������ǿ�ѡ��ģ����������ڽ�����������á�
���� *�û� > Ȩ��* ���鿴��������չʾ���û��ġ�

```php
'system: manage url aliases' => [
    'title' => 'Manage url aliases'
],
'system: manage users' => [
    'title' => 'Manage users',
    'description' => 'Warning: Give to trusted roles only; security implications.'
],
```

## ���һ��������

������뱣���������ɶ��ƣ����������չ�����ã�����Ҫ�ṩһЩ����Ҫ�޸��κδ��롢�����ױ��ı�����á�������������Լ򵥵�ָ��һ���Ӻ�����ӵ�ģ���ļ���
������Ĳ�����ӵ� `theme.php` �� `extension.php` �У���ָ����չ�ļ��У���


```php
'settings' => [
    'system'  => 'theme://mytheme/views/admin/settings.razr'
],
```

�� `/themes/mytheme/views/admin/settings.razr` λ�ô���һ���ļ���Ϊ����Ҫ��չʾ��ʽ��ӱ�ǡ�����ĳ��ģʽ���������ʽ��Ԫ��ʱ��Pagekit���Զ����沢�������á�
�����ʽӦ������һ������ѡ������У����������������򱻳��� `config[OPTION]`  ������ `OPTION` ��������Ǹ�ѡ������֡�

ȷ�������ʽ���ʵݸ� `@url('@system/themes/savesettings', ['name' => 'mytheme'])` ��Ϊһ�� `POST` ���󣬾�������������ӡ�

**ע��** ��ΪPagekit��ʼ�ṩ���ǣգɣ��������ʹ�ãգɣ�������ʽ��ǡ�

```php
<form class="uk-form uk-form-horizontal" action="@url('@system/themes/savesettings', ['name' => 'mytheme'])" method="post">

    <div class="uk-form-row">
        <label for="form-sidebar-a-width" class="uk-form-label">@trans('Show Copyright')</label>
        <div class="uk-form-controls">
            <select id="form-sidebar-a-width" class="uk-form-width-large" name="config[show_copyright]">
                <option value="1"@( $config['show_copyright'] ? ' selected' : '')>Show</option>
                <option value="0"@( !$config['show_copyright'] ? ' selected' : '')>Hide</option>
            </select>
        </div>
    </div>

    <p>
        <button class="uk-button uk-button-primary" type="submit">@trans('Save')</button>
        <a class="uk-button" href="@url('@system/themes')">@trans('Close')</a>
    </p>

</form>
```

����ֵ�ڣУȣ��пɵõ���

```php
$theme = $app['theme.site']->getConfig();
$show_copyright = $theme['show_copyright'];
```