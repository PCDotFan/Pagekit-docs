#С���

<p class="uk-article-lead">����վ�Ĳ�ͬλ��ʹ��С���������һ�������ݡ�</p>

Ϊ�˾���С�����������������֣�����Ա������һ�� *С���* ���������ⶨ����ض�λ�ù���С�������չ��������Ժ�С�����ͬ���ڣ��ڿ���ʱû������

##�����ṹ

С�����Ϊ������λ������һ����չ `Pagekit\Widget\Model\Type` �����ж���ġ�

**ע��** �ڵ���˫�»��߹���ʱ���һ���ַ��� `__(...)` ʹ�����ɷ��롣�������������[�����½�](translation.md)��

`hello/src/HelloWidget.php`:

```php
<?php

namespace Pagekit\Hello;

use Pagekit\Widget\Model\Type;
use Pagekit\Widget\Model\WidgetInterface;

class HelloWidget extends Type
{
    /* unique identifier */
    public function getId()
    {
        return 'widget.hello';
    }

    /* name displayed in admin area */
    public function getName()
    {
        return __('Hello Widget!');
    }

     /* description displayed in admin area */
    public function getDescription(WidgetInterface $widget = null)
    {
        return __('Hello Demo Widget');
    }

    /* returns information representing the current configuration
    of the widget. A weather widget would return the configured
    location for example. Displayed in the widget listing in
    Settings > Dashboard.
    */
    public function getInfo(WidgetInterface $widget)
    {
        return __('Hello Demo Widget');
    }

    /* Rendering the widget. Will usually render a view */
    public function render(WidgetInterface $widget, $options = [])
    {
        return $this['view']->render('extension://hello/views/widget.razr');
    }

    /* Define a form for the Advanced section in the widget admin settings */
    public function renderForm(WidgetInterface $widget)
    {
        return __('Hello Widget Form.');
    }
}
```

* *��Ҫ* * Ϊ�����ʾ������ȷ������һ�������������ݵ���ͼ�ļ� `hello/views/widget.php` ��

```HTML
Hello Widget!
```

## ����дС���������

������������`getInfo`, `render` �� `renderForm` ��Щ������ӵ�� `WidgetInterface` ����Ľ� `$widget` �Ĳ��������������ʾ��С��������ã���ʵ�����ݴ��������ݿ��е�
`system_widget`���У���ʹ�����������дС��������á�


�Ķ����ԣ�

| ����            | ����                 |
|-----------------|----------------------|
| `getId()`       | ���С������ض�ID�� |
| `getTitle()`    | ���С����ı��⡣ |
| `getType()`     | ���С��������࣬ �����ǵ�ʵ������ `widget.hello` �� |
| `getPosition()` | ��÷����С�����λ�á� |
| `getStatus()`   | ���С�����״̬( `WidgetInterface::STATUS_ENABLED` �� `WidgetInterface::STATUS_DISABLED` )��|
| `getSettings()` | ���С������������С� |

��д�����������ԣ�
|  ����         | ����        |
|---------------|-------------|
| `get($name, $default = null)`|����ض���С������á�|
| `set($name, $value)`         |��д�ض���С������á�|
| `remove($name)`              |�Ƴ��ض���С������á�|

## ע��С���
��Ȼ������С�����Ϊ�Ѿ����壬������Ҫע��һ��С���ʵ����������� `extension.php` �� `theme.php` ����ɡ�

```php
<?php

namespace Pagekit\Hello;

use Pagekit\Extension\Extension;
use Pagekit\Framework\Application;
use Pagekit\Widget\Event\RegisterWidgetEvent;

class HelloExtension extends Extension
{

    public function boot(Application $app)
    {
        parent::boot($app);

        $app->on('system.widget', function(RegisterWidgetEvent $event) {
            $event->register(new HelloWidget);
        });

    }
}
```

�����ǵ���չ����ʱȷ����Դͷ���� `boot` ������Ȼ�����ǿ������ɵ�ʹ�ûص���������Ӧ�õ� `system.widget` �¼���ͨ���ص��������������ڿ���ʹ������Ӧ��ʵ���� `widgets` ������ע��
���ǵ� `HelloWidget` �����������������ʵ�������п����ģ�ע�⵽`register`�����Ҫ�Ѹ�����ȥִ��`TypeInterface`��

##�������ǵ�С���

ȥ����Ա����ȷ����չ��ִ�С���������г����� `HelloExtension` ����������� `HelloWidget` ��

�л��� *Widget* ��ǩ������ *Add Widget* ��ť��ѡ�� *Hello Widget Form.* ������ע������չ�ֵ���ʽ����һ�� *Advanced* ������ *Hello Widget Form.* ���ݡ�
�������������������� `HelloWidget::renderForm` �����ġ�

Ϊ���С���ѡ��һ�� *����* ��ȷ�� *״̬* ���ò�ѡ��һ��λ�ã����� *���Ϸ�* �������λ�þ��������λ�á��л��� *Assignment* ��ǩ��ѡ������С���Ӧ���ֵ�ҳ�档
���������������ѡ�� *��ҳ* �� *����* ���С�����Ȼ��ȥ��ҳ�鿴��е�С�����

##����һ���Ǳ��С���

��Ҳ����Ϊ����Ա����� *�Ǳ��* ����С������������̼�����ͬ��Ψһ��������С�����Ӧ����ע��ķ�ʽ�����ô����� `system_user` ���У�
��Ϊ�Ǳ������ÿ���û����Ǳ����˵���ض��ģ���

```php
<?php

namespace Pagekit\Hello;

use Pagekit\Extension\Extension;
use Pagekit\Framework\Application;
use Pagekit\Widget\Event\RegisterWidgetEvent;

class HelloExtension extends Extension
{

    public function boot(Application $app)
    {
        parent::boot($app);

        $app->on('system.dashboard', function(RegisterWidgetEvent $event) {
            $event->register(new HelloWidget);
        });
    }
}
```

�鿴��е�С�����������ӵ���Ĺ���Ա�Ǳ���У�

1.�ڹ���Ա���� *���� > �Ǳ��* ��
2.���� *���С���* ѡ�� *���С���* ��
3.���棬ȥ����Ա�Ǳ��鿴С�����