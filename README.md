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


            8: 
