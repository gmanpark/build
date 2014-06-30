Heroku Buildpack for Node.js & Phantomjs
==========================================

## Introduction

- [heroku-buildpack-nodejs](https://github.com/heroku/heroku-buildpack-nodejs) 와 phantomjs 결합
- phantomjs 한글깨짐 현상 조치

## 핵심소스

`bin/compile` 파일만 참조하면 됨


## 배경

- heroku buildpack 은 `BUILD_DIR, CACHE_DIR` 2개를 이해하는 것이 핵심
- phantomjs 설치 되어있지 않음.
- heroku fc-list 에는 한글 기본 폰트가 포함되어 있지 않음
- 그래서, phantomjs screen capture 기능에 문제소지가 있음


## buildpack 지정

```sh
# Create a new Heroku app that uses your buildpack
heroku create --buildpack <your-github-url>

# Configure an existing Heroku app to use your buildpack
heroku config:set BUILDPACK_URL=<your-github-url>

# You can also use a git branch!
heroku config:set BUILDPACK_URL=<your-github-url>#your-branch
```

## 한글 깨짐 방지 방법

- 어플리케이션 디렉토리에 `vendor/fonts` 디렉토리를 만들고, ttf 파일 복사
- git add ~ push
