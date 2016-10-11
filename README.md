<h1># 作者：single430
时间：2016.10.11</h1>

<p>
    &nbsp; &nbsp; <span style="color: rgb(12, 12, 12); font-size: 20px;"><strong>一，首先（Linux环境）</strong></span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;<span style="font-size: 18px; color: rgb(31, 73, 125);">（1）：先来记录一下最近的一个项目，登录注册注销</span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">1: 首先我们需要建立一个工程，前提是你已经安装了Django and Python，使用如下命令创建：</span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(255, 0, 0);">django-admin startproject mylogin</span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">2: OK，这样你就在当前路径下创建了mylogin，其结构如下，使用 <span style="color: rgb(255, 0, 0);">tree mylogin </span>查看：</span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;mylogin/<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── manage.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── mylogin<br/>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── __init__.py<br/>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── settings.py<br/>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── urls.py<br/>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── wsgi.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1 directory, 5 files
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">3: 接下来我们来创建app，对就是app，只不过我们这样创建：</span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(255, 0, 0);">&nbsp;cd mylogin</span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(255, 0, 0);">python manage.py startapp online</span>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">&nbsp;4:&nbsp; 恩的，来看下online目录结构<span style="color: rgb(255, 0, 0);"> tree online</span>：</span>
</p>
<p>
    <span style="color: rgb(0, 176, 240);">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 0, 0);">online/<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── admin.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── apps.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── __init__.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── migrations<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp; └── __init__.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── models.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── tests.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── views.py<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1 directory, 7 files</span></span>
</p>
<p>
    <span style="color: rgb(0, 176, 240);">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5: 上面的步骤结束后，请确保你是跟我一样的，然后我们打来 <span style="color: rgb(255, 0, 0);">mylogin/settings.py</span>&nbsp; 添加一些东西：&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;</span>
</p>
<pre style="background-color:#ffffff;color:#000000;font-family:&#39;DejaVu Sans Mono&#39;;font-size:9.0pt;">            INSTALLED_APPS = [                
                                    &#39;django.contrib.admin&#39;,
                                    &#39;django.contrib.auth&#39;,
                                    &#39;django.contrib.contenttypes&#39;,                
                                    &#39;django.contrib.sessions&#39;,                
                                    &#39;django.contrib.messages&#39;,                
                                    &#39;django.contrib.staticfiles&#39;,                
                                    &#39;online&#39;,    # 对就是添加的这个            
                                    ]</pre>
<p>
    <span style="color: rgb(0, 176, 240);">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6: 这里我们提前加入一些东西，还是在<span style="color: rgb(255, 0, 0);">settings.py</span>中：</span>
</p>
<p>
    <span style="color: rgb(0, 176, 240);">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;首先在你的online文件夹下新建文件夹templates：<span style="color: rgb(255, 0, 0);">mkdir&nbsp; templates</span></span>
</p>
<p>
    <span style="color: rgb(0, 176, 240);">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后在<span style="color: rgb(255, 0, 0);">templates</span>目录下新建三个html文件：</span>
</p>
<p>
    <span style="color: rgb(0, 176, 240);">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(255, 0, 0);">account.html：</span></span>
</p>
<pre style="background-color:#ffffff;color:#000000;font-family:&#39;DejaVu Sans Mono&#39;;font-size:12px">            &lt;!DOCTYPE html&gt;
            &lt;html lang=&quot;en&quot;&gt;
            &lt;head&gt;    
            &lt;meta charset=&quot;UTF-8&quot;&gt;    
            &lt;title&gt;注册&lt;/title&gt;
            &lt;/head&gt;
            &lt;body&gt;
            &lt;h1&gt;注册页面：&lt;/h1&gt;
            &lt;form method = &#39;post&#39; enctype=&quot;multipart/form-data&quot;&gt;    
            {% csrf_token %}    
            {{uf.as_p}}    
            &lt;input type=&quot;submit&quot; value = &quot;注 册&quot; /&gt;    
            {% if success_message %}&lt;p&gt;&lt;strong style=&quot;color: red&quot;&gt;{{ success_message }}&lt;/strong&gt;&lt;/p&gt;{% endif %}
            &lt;/form&gt;&lt;br&gt;&lt;a href=&quot;{% url &#39;online:mylogin&#39; %}&quot;&gt;登 陆&lt;/a&gt;
            &lt;/body&gt;&lt;/html&gt;
            
            
            index.html            
            &lt;!DOCTYPE html&gt;
            &lt;html lang=&quot;en&quot;&gt;
            &lt;head&gt;    
            &lt;meta charset=&quot;UTF-8&quot;&gt;    
            &lt;title&gt;登录成功&lt;/title&gt;
            &lt;/head&gt;&lt;body&gt;
            &lt;h1&gt;welcome {{username}} !&lt;/h1&gt;&lt;br&gt;
            &lt;a href=&quot;{% url &#39;online:logout&#39; %}&quot;&gt;注 销&lt;/a&gt;
            &lt;/body&gt;
            &lt;/html&gt;     


            login.html           
            &lt;!DOCTYPE html&gt;
            &lt;html lang=&quot;en&quot;&gt;
            &lt;head&gt;    
            &lt;meta charset=&quot;UTF-8&quot;&gt;   
             &lt;title&gt;登录&lt;/title&gt;
             &lt;/head&gt;
             &lt;body&gt;
             &lt;h1&gt;登陆页面：&lt;/h1&gt;
             {% if success_message %}&lt;p&gt;&lt;strong style=&quot;color: red&quot;&gt;{{ success_message }}&lt;/strong&gt;&lt;/p&gt;{% endif %}
             &lt;form method = &#39;post&#39; enctype=&quot;multipart/form-data&quot;&gt;    
             {% csrf_token %}    
             {{uf.as_p}}    
             &lt;input type=&quot;submit&quot; value = &quot;登 录&quot; /&gt;&lt;/form&gt;&lt;br&gt;
             &lt;a href=&quot;{% url &#39;online:account&#39; %}&quot;&gt;注 册&lt;/a&gt;
             &lt;/body&gt;
             &lt;/html&gt;</pre>

            settings.py
<pre style="background-color:#ffffff;color:#000000;font-family:&#39;DejaVu Sans Mono&#39;;font-size:9.0pt;">            TEMPLATES = [
                {
                    &#39;BACKEND&#39;: &#39;django.template.backends.django.DjangoTemplates&#39;,
                    &#39;DIRS&#39;: [os.path.join(BASE_DIR), &#39;online/templates&#39;],    # 这里，这是将你的模板引进来
                    ....</pre>
<p>
    &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">&nbsp;7: 这里我们不动数据库的选项，默认使用sqlite3数据库，等会我们需要生成数据库，名字是<span style="color: rgb(255, 0, 0);">db.sqlite3，在同manage.py同路径下的目录中</span>;</span>
</p>
<p>
    <br/>
</p>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">8:&nbsp; 打开<span style="color: rgb(255, 0, 0);">mylogin目录下的urls.py</span>，改成这个样子：</span>
</p>
<pre style="background-color:#ffffff;color:#000000;font-family:&#39;DejaVu Sans Mono&#39;;font-size:9.0pt;">            from django.conf.urls import url, include
            from django.contrib import admin

            urlpatterns = [
                url(r&#39;^admin/&#39;, include(admin.site.urls)),
                url(r&#39;^online/&#39;, include(&#39;online.urls&#39;, namespace=&quot;online&quot;)),
            ]</pre>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">9: 在<span style="color: rgb(255, 0, 0);">online目录下新建一个urls.py</span>, 添加如下内容：</span>
</p>
<pre style="background-color:#ffffff;color:#000000;font-family:&#39;DejaVu Sans Mono&#39;;font-size:9.0pt;">            from django.conf.urls import url
            from online import views

            urlpatterns = [
                url(r&#39;^$&#39;, views.mylogin, name=&#39;mylogin&#39;),    # 登录页面网址
                url(r&#39;^login/$&#39;, views.mylogin, name=&#39;mylogin&#39;),    # 登录页面网址
                url(r&#39;^logout/$&#39;, views.logout, name=&#39;logout&#39;),    # 注销页面网址
                url(r&#39;^account/$&#39;, views.account, name=&#39;account&#39;),    # 注销页面网址
                url(r&#39;^index/$&#39;, views.index, name=&#39;index&#39;),    # 登录成功页面网址
            ]</pre>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">10: 接下来是在<span style="color: rgb(255, 0, 0);">online/models.py</span>中添加数据库(这里我们只添加用户名和密码):</span>
</p>
<pre style="background-color:#ffffff;color:#000000;font-family:&#39;DejaVu Sans Mono&#39;;font-size:9.0pt;">            from __future__ import unicode_literals
            from django.db import models

            # Create your models here.


            class MyUser(models.Model):
                username = models.CharField(max_length=50)
                password = models.CharField(max_length=50)

                def __unicode__(self):
                    return self.username</pre>
<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: rgb(0, 176, 240);">&nbsp;11: 最后我们要在视图中添加urls.py对应的函数了<span style="color: rgb(255, 0, 0);">online/views.py</span>：</span>
</p>
<pre style="background-color:#ffffff;color:#000000;font-family:&#39;DejaVu Sans Mono&#39;;font-size:9.0pt;">            # coding=utf-8
            from django.shortcuts import render, redirect, render_to_response
            from django.http import HttpResponse, HttpResponseRedirect
            from django import forms
            from django.template import RequestContext

            from models import MyUser
            # Create your views here.


            # 表单
            class UserForm(forms.Form):
                username = forms.CharField(label=&#39;用户名&#39;, max_length=100)
                password = forms.CharField(label=&#39;密  码&#39;, widget=forms.PasswordInput())


            # 登录
            def mylogin(request):
                if request.method == &#39;POST&#39;:
                    uf = UserForm(request.POST)
                    if uf.is_valid():
                        # 获取表单用户密码
                        username = uf.cleaned_data[&#39;username&#39;]
                        password = uf.cleaned_data[&#39;password&#39;]
                        # 获取的表单数据与数据库进行比较
                        user = MyUser.objects.filter(username__exact=username, password__exact=password)
                        if user:
                            # 比较成功，跳转index
                            response = HttpResponseRedirect(&#39;/online/index/&#39;)
                            # 将username写入浏览器cookie,失效时间为3600
                            response.set_cookie(&#39;username&#39;, username, 3600)
                            return response
                        else:
                            # 比较失败，还在login
                            return HttpResponseRedirect(&#39;/online/login/&#39;)
                else:
                    uf = UserForm()
                return render(request, &#39;login.html&#39;, {&#39;uf&#39;: uf})


            # 注册
            def account(request):
                if request.method == &#39;POST&#39;:
                    uf = UserForm(request.POST)
                    if uf.is_valid():
                        # 获得表单数据
                        username = uf.cleaned_data[&#39;username&#39;]
                        password = uf.cleaned_data[&#39;password&#39;]
                        # 添加到数据库
                        MyUser.objects.create(username= username, password=password)
                        # return HttpResponse(&#39;注册成功!!&#39;)
                        return render(request, &#39;account.html&#39;, {&#39;uf&#39;: uf, &#39;success_message&#39;: &quot;注册成功!!&quot;})
                else:
                    uf = UserForm()
                    return render(request, &#39;account.html&#39;, {&#39;uf&#39;: uf})


            # 登录成功
            def index(request):
                username = request.COOKIES.get(&#39;username&#39;)
                if bool(username):
                    return render_to_response(&#39;index.html&#39;, {&#39;username&#39;: username})
                else:
                    uf = UserForm()
                    return render(request, &#39;login.html&#39;, {&#39;uf&#39;: uf})


            # 注销
            def logout(request):
                response = HttpResponse(&#39;Logout!!&#39;)
                # 清理cookie里保存username
                response.delete_cookie(&#39;username&#39;)
                # response.delete_cookie(&#39;sessionid&#39;)
                return response</pre>
<p>
    <br/>
</p>
