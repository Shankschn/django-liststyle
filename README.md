## 博客
www.yudelei.com/242.html
## 说明
在使用前版本时，不清楚是由于还是个人理解错误...还是 Django 或 Python 版本的原因，始终无法设置行颜色。

此次修改，使用了笨办法...在 furkankykc 的基础上，添加了静态文件 c-color.css。
如需自定义颜色，可自行请修改该文件。
## 环境
Python 3.7.9
Django 2.2.17
django-simpeui 2021.4.1
## 安装
~~~
pip install git+https://github.com/Shankschn/django-liststyle.git
~~~
## 使用
### settings.py
添加 'liststyle' 到 INSTALLED_APPS 中，放于 'django.contrib.admin' 之前，若使用 'simpleui' 可取消其注释，类似如下：
~~~
INSTALLED_APPS = [
    'liststyle',
    #'simpleui',
    'django.contrib.admin',
	...
]
~~~
### admin.py
~~~
from liststyle import ListStyleAdminMixin


class MyModelAdmin(admin.ModelAdmin, ListStyleAdminMixin):
	pass
	
	def get_row_css(self, obj, index):
		if obj.active:
			return ''
		return ''
~~~
## 其他说明
Note: If you have your own change_list_results.html; you'll need to 
incorporate the changes from the one here. An example of a custom template
from the "grappelli" package is included in templates/admin/ dir.
