# ѡ��

`option`�����ṩ��һ�ּ򵥵ķ�ʽ�����ݿ��д�ȡֵ


## ����ѡ���ֵ

ʹ�� `set($key, $value, $autoload=null)` ������ѡ���ֵ

| ����   | ���� |
|---------|-------------|
| `$key`           | string����,��Ϊѡ���Ψһ��ʶ. Ϊ�˷�ֹ����������չ������ͻ,Ӧ�������keyǰ������չ��������Ϊǰ׺, ����. `hello:version`. |
| `$value`          | ���õ�ֵ. ������`int`, `str`, `array`����. |
| `$autoload`   | ��������,��������ѡ���Ƿ�����ݿ��Զ�����. ����������ܿ�������Ϊ`false`. ��û�д�ֵ���ߴ���`null`ʱ,��ǰѡ����Զ�������Ϊ�ᱻ����. |


```
$this['option']->set('hello:message', 'Hello Universe!');
```


## ȡ��ѡ���ֵ

ʹ�� `get($name, $default = null)` ����ȡѡ���ֵ
���ѡ��û�б�����,��ô`$default`����ΪĬ�ϵķ���ֵ

```
$message = $this['option']->get('hello:message', 'Hello World!');

```
