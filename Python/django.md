## 프레임 워크

1. 자주 사용되는 코드를 체계화 하여 사용할 수 있도록 하는 코드 집합
2. 라이브러리 보단 더 규모가 크며, 프로젝트의 기반이 됨

## Django Docs

> https://docs.djangoproject.com/ko/3.0

## [MVC] Pattern

1. Model : Django는 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 추상적인 계층("모델")을 제공

2. View : Django는 사용자의 요청을 처리하고 결과를 반환하기 위한 로직을 캡슐화한 "뷰"의 개념을 갖고 있음

3. Template : 템플릿 계층은 사용자에게 표시할 정보를 표현하기 위해 디자이너에게 친숙한 문법을 제공

### install virtualenv

```shell
$ virualenv '<venv name>'
```

### active venv

```shell
(mac) $ source venv_name/bin/activate
(window) $ <your_path>\venv\Script\activate.bat
```

### install django

```shell
$ pip3 install django
```

### project 생성

```shell
$ django-admin startproject '<project_name>'
```

### app 생성

```shell
django-admin startapp '<app_name>'
```

### MVC(MTV)

-   Django 에서는 T(templates)에 해당되는 디렉터리가 자동으로 생성 되지 않기 때문에 app 내 templates 폴더를 생성 해주어야 함

### project에 app 등록

```python
# poject_name/setting.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    '<app_name>'
]
```

-   위와 같이 해당 app_name를 추가해주어야함

### Model

> 참고 : https://docs.djangoproject.com/ko/3.0/ref/models/fields/

-   Django Docs에 의하면 Django는 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 추상적인 계층("모델")을 제공한다 고함
-   사용할 DB 테이블 설정을 해준다고 생각하면 편함 (ORM)

```python
# <app_name>/models.py
from django.db import models

class ModelName(models.Model):
    name = models.CharField(max_length=100,
                            verbose_name='이름')
    age = models.IntegerField(default=0,
                              verbose_name='나이')
    regist_dttm = models.DateTimeField(auto_now_add=True,
                                       verbose_name='등록일자')
```

-   CharField : 제한된 문자열 필드 타입 (max_length필 필요)
-   IntegerField : 32 비트 정수형 필드
-   DateTimeField : 날짜와 시간을 갖는 필드. 날짜만 가질 경우는 DateField, 시간만 가질 경우는 TimeField를 사용
