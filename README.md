# dog_love_web

A new Flutter project.

## 깃 허브 우베 액션 디플로이 
- 참조 사이트 
https://velog.io/@hetarho/Fluttergithub-action%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-gh-page-%EB%A1%9C-web-%ED%98%B8%EC%8A%A4%ED%8C%85%ED%95%98%EA%B8%B0


- flutter web 개발 세팅
flutter config --list
flutter config --enable-web       


Workflow permissions
Read and write permissions -- save 

Pages --> Branch 
Gh-pages, root로 세팅

GITHUB_TOKEN 토큰 생성 후 세팅

-- flutter_web_deploy.yml ( index.html 수정 필요없음)
name: Deploy Flutter Web App to GitHub Pages

on:
  push:
    branches:
      - main  # 또는 Flutter 앱의 소스 코드가 있는 브랜치 이름

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v4.1.1

    - name: Setup Flutter
      uses: subosito/flutter-action@v2.12.0
      with:
        flutter-version: '3.24.4' # 사용하는 Flutter 버전으로 변경

    - name: Build Web
      run: flutter build web --release --web-renderer html --base-href /dog_love_web/

    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3.9.3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }} # repository에서 사용할 시크릿 키 이름
        publish_dir: ./build/web




# dog_love_web
