# ����������

<p class="uk-article-lead">Pagekit�������������г����ķ�������. ������һЩ�ǳ����еķ���������.</p>

## Apache 2.2+

���ʹ��apache,��ȫ���ı�Ҫ���þ�������`.htaccess`�ļ���.
With Apache, all necessary configuration comes with the included `.htaccess` file. 

ȷ��apache�Ѿ�����`mod_rewrite`ģ��. �����ģ�鲻����, Pagekit��Ȼ����,��url����ʽ��������:`http://example.com/index.php/page/welcome`.

## nginx

���ʹ�õ���nginx, �ο�[PHP to Nginx](http://wiki.nginx.org/PHPFcgiExample)�������� ������location���������¹���

```nginx
location / {
    try_files $uri $uri/ /index.php?$args;
}
```
