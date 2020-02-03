## 프레임 워크

### 1. 자주 사용되는 코드를 체계화 하여 사용할 수 있도록 하는 코드 집합

### 2. 라이브러리 보단 더 규모가 크며, 프로젝트의 기반이 됨

## Django Docs

### https://docs.djangoproject.com/ko/3.0

## [MVC] Pattern

### Model : Django는 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 추상적인 계층("모델")을 제공

### View : Django는 사용자의 요청을 처리하고 결과를 반환하기 위한 로직을 캡슐화한 "뷰"의 개념을 갖고 있음

### Template : 템플릿 계층은 사용자에게 표시할 정보를 표현하기 위해 디자이너에게 친숙한 문법을 제공

### install virtualenv

```shell
$ virualenv 'venv name'
```

### active venv

```shell
(mac) $ source venv_name/bin/activate
(window) $ call venv_name/bin/activate
```

### install django

```shell
$ pip3 install django
```

### project 생성

```shell
$ django-admin startproject 'project_name'
```

### app 생성

```shell
django-admin startapp 'app_name'
```

### MVC(MTV)
