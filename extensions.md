# ���

<p class="uk-article-lead">�½����Ϊ���Pagekit������</p>

һЩPagekit��Ĭ�Ϲ��� (ҳ�桢��װ�������������)��ʹ�ò��ʵ�ֵ�. ���⣬���̵������� *Hello Extension* ���������Ĳ��. �뿴һ��`/extensions` ���Ŀ¼

## �����ṹ 

�м������͵Ĳ���������Ƕ���ѭ��ͬ�Ļ���ģʽ�����½�Ϊ���ṩ�й�һ�㷽���ļ�Ҫ����������������һ���������й���֧�������µĲ���ĹǼ��ļ��ṹ��
```bash
pagekit extension:generate <extension_name>
```

�������½�һ��*Hello*����Կ�ʼ���ǵĽ̳�

**����** ����Դ��̵�����*Hello extension*��������

```bash
cd path/to/pagekit
pagekit extension:generate hello
```

���ᱻҪ���ṩ������Ϣ��
| ��Ϣ            | ����         |
|-----------------|-------------|
| *Title*         | ��̨��ʾ�Ĳ������,�� 'Hello Extension' |
| *Author*        | �������� |
| *Email*         | ���ĵ����ʼ���ַ |
| *PHP Namespace* | �����PHP�����ռ�, �� `Pagekit\Hello`�� |

�ⲽ������Ŀ¼`/extensions/hello`����������ļ��ṹ������㲻��ʹ�������й��ߣ��������ֶ�����һ���ļ�

| �ļ���/�ļ�    |����         |
|---------------|-------------|
| `/src` | �����еĴ�����ļ�����|
| `/src/Controller` | ��������ÿ����� |
| `/src/Controller/DefaultController.php`| Ĭ�ϵĿ������� |
| `/src/HelloExtension.php` | �������Ҫ���֣�����������ʼ���� |
| `extension.json` | ����Ԫ������ϵ���г���Ϣ |
| `extension.php` | ��Ų���������������ô��� |

**ע��**�޷�������ǰ̨�����ĸ��ģ������˴Ӻ�̨�������Ĳ��

## Ԫ����

`extension.json` �Ǵ�����Ĳ������(���֤�����ߵ�)��json�ļ�������ļ���Ҫ�������Ѳ���ϴ����̵���ʱ�����ں�̨��α�ʾ���Ĳ��ʱ�õ���

```json
{
    "name": "hello",
    "version": "0.8.0",
    "type": "extension",
    "title": "Hello",
    "description": "A blueprint to develop your own extensions.",
    "license": "MIT",
    "authors": [
        {
            "name": "Pagekit",
            "email": "info@pagekit.com",
            "homepage": "http://pagekit.com"
        }
    ],
    "extra": {
        "image": "extension.svg"
    }
}
```

## ����

`extension.php` �ǰ����Ĳ������PHP���룬������Ĭ���ļ����Զ�������Ŀ������������������ռ�����ࡣ ��Ҳ�����������Ҫ��չʵ��(`HelloExtension`�� `Pagekit\Framework\Extension`������)��

���ǽ���[Configuration](configuration.md) �����������ļ�

```php
<?php

return [

    'main' => 'Pagekit\\Hello\\HelloExtension',

	'autoload' => [
        'Pagekit\\Hello\\' => 'src'
    ],

    'controllers' => 'src/Controller/*Controller.php'

];
```
