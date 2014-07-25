# �ܹ����¼�

<p class="uk-article-lead">�˽�Pagekit���ڲ��ṹ�Լ������������</p>

Ҫ���Pagekit���ļ����ļ��еĸ����������[�ļ��нṹ](folder-structure.md) ����Ϊһ��������Ա�����ܶ�`vendor`�ļ��и���Ȥ���ڴ��ļ��У���ᷢ�����еĴ��룬���˴������룬�磺

- JavaScript �� CSS ��, �� jQuery, UIKit ��
- ������PHP �⣬�� Symfony, Doctrine ��
- Razr ģ������, Pagekit�������Pagekit�ļܹ�

## �ܹ�

### Ӧ�ó���

Pagekit�ĺ�����Ӧ�ó���Ҳ����һ��`Pagekit\Framework\Application`Ӧ��ʵ������Ӧ�ó��������������󲢷���һ����Ӧ����������*������������*���֣�����ӵ��һ��`Router`����λ��`HttpKernel`��������������ˮƽ������

��Ӧ�ó���Ҳ�ɱ���Ϊһ��[Pimple����ע������](http://pimple.sensiolabs.org/), ��������ṩ�ߵ�λ��, �����ṩ����һ�����ĵĸ����Ϊ��������ĳЩ����Ϳ�ܵ��������ֵĹ��ܣ���ʹ��������Ӧ�ó����з��� - Ҳ�������չ�������з��ʡ�

### �����ṩ��

�����ṩ����ʵ��`register`��`boot`��һ���࣬ `register` ����Ӧ�ó���������׶α����ã�`boot`��Ӧ�ó�����յ�����ʱ�����á�`register`��Ԥ�ڵķ�������Ӧ�ó�����`$app['db']`�ṩ�Ӵ�����κ�һ���ط��������ݿ�Ĺ���

ϵͳ��ͬ���ֵ�ͨ�����¼���ʽ������������Ϣ��μ��·�*�¼�*���֡�

## �������������

Ϊ�˸������˽�Pagekit���ڲ��������̣���������������һ�����󾭹�Pagekit���еĲ�ʱ�ᷢ��ʲô��

��web��������ÿ�������б�����ʱ��`index.php`������ڵ㡣��������������׶�������ʽ������Ļ�����ȣ�`/app/app.php`�����ڲ�Pagekit���ڲ����������и�����˽⣬��������������һ�����󾭹�������Pagekit��ᷢ��ʲô�� 

�������������ڵ���`index.php`�ļ���ÿ�������Web���������á���������������׶εõ���ʽ������Ļ�����ȣ�`/Ӧ�ó���/ app.php`�����أ�����������Ӧ�ó�������������������룬�ڶ����׶���������׶Σ������Ƿֿ������������׶Ρ�

### 1. �����׶�

����������`/app/app.php`�����ȡ�� `/app/config/app.php`�е�Ĭ������, ��`config.php`����һ�������ͬ���ݸ�һ���µ�Ӧ�ó���ʵ����

Ȼ���������ж�������з���Ӧ����Ӧ�ó����б�ע�ᣬ֮���������ݿ�����Ӳ��������ɲ�����У�ʵ�ʸ��ɷ����ڵڶ��׶Σ��� 

���`config`�ļ���ʧ���޷����ӵ����ݿ⣬���˵��Pagekit��δ��װ����ʱ���صĲ��ֻ��*Installer*���⽫���°�װ�����ڵڶ��׶ν�����ʱ����ʾ��

### 2. ������׶�

����������Ӧ�ó�����run�ķ�ʽ����http�����Ӧ�ó���ĽǶ���������������Router���С�

`Router` λ�� `HttpKernel`֮��, ȡ����·�����۵Ľ���ǵ��Ⱥ��п���������ϵ�ṹ����Ͳ㡣�ں˽�����һ����Ӧ������ζ�������ṩ������ַ�����һ����Ӧ���׳�Ҫ����һ���쳣�����ַ�ӦȻ�󱻽����������޸���Ӧ��������ϲ㡣

## �¼�

ϵͳ��ͨ�ŵĺ����齨�� `EventDispatcher` ��������ͨ�� `$app['events']` (��
`$this['events']` ��ʹ��ApplicationTraitʱ)��ÿһ���ֶ��ܼ���ĳЩ�¼��ʹ���һЩ�¼���

�����¼���һ�������ʵ��`EventSubscriberInterface`��ͬ�Ͼ�̬����`getSubscribedEvents`���⽫����һ�����飬�䶩�ĵ���ͻص�������Ϊ����ֵ��

```php
<?php

namespace Pagekit\Hello\Event;

use Pagekit\Framework\Event\EventSubscriber;

class HelloListener extends EventSubscriber
{
    public function onBoot($event, $eventName, $dispatcher)
    {
        // do something
    }

    public function anyName() // omit parameters if you do not need them
    {
        // do something
    }

    public static function getSubscribedEvents()
    {
        return [

            'hello.boot' => 'onBoot',

            // use any name and add a priority int if desired
            'hello.boot' => ['anyName', 10]
        ];
    }
}
```

��������������⣩�� `boot` ����ע����ļ��������Ա������Զ����¼���

```php
$this['events']->addSubscriber(new HelloListener());
```

������ʹ��Ӧ�õ� `on` ��ݷ�ʽ�����¼�������ӦҲ����ֻ����һ���հ���

```php
$app->on('hello.boot', function($event) use ($app){
    // do something
});
```

�����¼�ʹ�������﷨��

```php
// dispatch event, optional second $event parameter
$app['events']->dispatch('hello.boot');
```

### �¼����� 

����಻ͬ���¼����ͣ��ܶ����������¼�ʵ���������ں�, ������� `Symfony\Component\HttpKernel\KernelEvents`. �ҵ����ǵ���ϸ˵��������ÿ���齨�������κθ���ʱ������¼�, ���ｫ���кܶ಻ͬ���¼�

**ע��** һ��ǿ��Ŀ��Բ鿴�����¼��Ĳ�� *profiler toolbar* ��������Pagekit��̨��������
