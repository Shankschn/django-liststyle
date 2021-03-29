## 说明
在使用前版本时，不清楚是由于还是个人理解错误，还是 Django 或 Python 版本的原因。最终，始终无法设置行颜色。

此次修改：
× 添加 c-color.css 文件，内含了个人常用的颜色代码。
× 修改 change_list_results.html 模板，调用静态文件 c-color.css。

如果需自定义颜色，请修改 c-color.css。
## 环境
支持 Python 3.7
支持 Django 2.2
与 django-simpeui 兼容

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
### 颜色代码


## 其他说明
Note: If you have your own change_list_results.html; you'll need to 
incorporate the changes from the one here. An example of a custom template
from the "grappelli" package is included in templates/admin/ dir.
