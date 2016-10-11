    一，首先（Linux环境）

    （1）：先来记录一下最近的一个项目，登录注册注销

            1: 首先我们需要建立一个工程，前提是你已经安装了Django and Python，使用如下命令创建：

                    django-admin startproject mylogin

            2: OK，这样你就在当前路径下创建了mylogin，其结构如下，使用 tree mylogin 查看：

                    mylogin/
                    ├── manage.py
                    └── mylogin
                    ├── __init__.py
                    ├── settings.py
                    ├── urls.py
                    └── wsgi.py
                    1 directory, 5 files

            3: 接下来我们来创建app，对就是app，只不过我们这样创建：

                    cd mylogin

                    python manage.py startapp online

            4:  恩的，来看下online目录结构 tree online：

                    online/
                    ├── admin.py
                    ├── apps.py
                    ├── __init__.py
                    ├── migrations
                    │   └── __init__.py
                    ├── models.py
                    ├── tests.py
                    └── views.py
                    1 directory, 7 files

            5: 上面的步骤结束后，请确保你是跟我一样的，然后我们打来 mylogin/settings.py  添加一些东西：        

            INSTALLED_APPS = [
                'django.contrib.admin',
                'django.contrib.auth',
                'django.contrib.contenttypes',
                'django.contrib.sessions',
                'django.contrib.messages',
                'django.contrib.staticfiles',
                'online',    # 对就是添加的这个
            ]

            6: 这里我们提前加入一些东西，还是在settings.py中：

                        首先在你的online文件夹下新建文件夹templates：mkdir  templates

            TEMPLATES = [
                {
                    'BACKEND': 'django.template.backends.django.DjangoTemplates',
                    'DIRS': [os.path.join(BASE_DIR), 'online/templates'],    # 这里，这是将你的模板引进来
                    ....

            7: 这里我们不动数据库的选项，默认使用sqlite3数据库，等会我们需要生成数据库，名字是db.sqlite3，在同manage.py同路径下的目录中;


            8:  打开mylogin目录下的urls.py，改成这个样子：

            from django.conf.urls import url, include
            from django.contrib import admin

            urlpatterns = [
                url(r'^admin/', include(admin.site.urls)),
                url(r'^online/', include('online.urls', namespace="online")),
            ]

            9: 在online目录下新建一个urls.py, 添加如下内容：

            from django.conf.urls import url
            from online import views

            urlpatterns = [
                url(r'^$', views.mylogin, name='mylogin'),    # 登录页面网址
                url(r'^login/$', views.mylogin, name='mylogin'),    # 登录页面网址
                url(r'^logout/$', views.logout, name='logout'),    # 注销页面网址
                url(r'^account/$', views.account, name='account'),    # 注销页面网址
                url(r'^index/$', views.index, name='index'),    # 登录成功页面网址
            ]

            10: 接下来是在online/models.py中添加数据库(这里我们只添加用户名和密码):

            from __future__ import unicode_literals
            from django.db import models

            # Create your models here.


            class MyUser(models.Model):
                username = models.CharField(max_length=50)
                password = models.CharField(max_length=50)

                def __unicode__(self):
                    return self.username

            11: 最后我们要在视图中添加urls.py对应的函数了online/views.py：

            # coding=utf-8
            from django.shortcuts import render, redirect, render_to_response
            from django.http import HttpResponse, HttpResponseRedirect
            from django import forms
            from django.template import RequestContext

            from models import MyUser
            # Create your views here.


            # 表单
            class UserForm(forms.Form):
                username = forms.CharField(label='用户名', max_length=100)
                password = forms.CharField(label='密  码', widget=forms.PasswordInput())


            # 登录
            def mylogin(request):
                if request.method == 'POST':
                    uf = UserForm(request.POST)
                    if uf.is_valid():
                        # 获取表单用户密码
                        username = uf.cleaned_data['username']
                        password = uf.cleaned_data['password']
                        # 获取的表单数据与数据库进行比较
                        user = MyUser.objects.filter(username__exact=username, password__exact=password)
                        if user:
                            # 比较成功，跳转index
                            response = HttpResponseRedirect('/online/index/')
                            # 将username写入浏览器cookie,失效时间为3600
                            response.set_cookie('username', username, 3600)
                            return response
                        else:
                            # 比较失败，还在login
                            return HttpResponseRedirect('/online/login/')
                else:
                    uf = UserForm()
                return render(request, 'login.html', {'uf': uf})


            # 注册
            def account(request):
                if request.method == 'POST':
                    uf = UserForm(request.POST)
                    if uf.is_valid():
                        # 获得表单数据
                        username = uf.cleaned_data['username']
                        password = uf.cleaned_data['password']
                        # 添加到数据库
                        MyUser.objects.create(username= username, password=password)
                        # return HttpResponse('注册成功!!')
                        return render(request, 'account.html', {'uf': uf, 'success_message': "注册成功!!"})
                else:
                    uf = UserForm()
                    return render(request, 'account.html', {'uf': uf})


            # 登录成功
            def index(request):
                username = request.COOKIES.get('username')
                if bool(username):
                    return render_to_response('index.html', {'username': username})
                else:
                    uf = UserForm()
                    return render(request, 'login.html', {'uf': uf})


            # 注销
            def logout(request):
                response = HttpResponse('Logout!!')
                # 清理cookie里保存username
                response.delete_cookie('username')
                # response.delete_cookie('sessionid')
                return response


