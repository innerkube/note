


Hugo 블로그를 GitHub Pages로 호스팅하는 것은 가능합니다. 그러나 Hugo는 Jekyll과 달리 GitHub Pages에서 기본적으로 지원되지 않습니다. GitHub Pages는 Jekyll을 통해 자동으로 정적 사이트를 빌드하지만, Hugo 사이트를 빌드하려면 몇 가지 추가 작업이 필요합니다.

### Hugo 블로그를 GitHub Pages에 호스팅하는 방법

Hugo 블로그를 GitHub Pages에 호스팅하려면 GitHub Actions를 사용하여 Hugo 사이트를 자동으로 빌드하고 배포할 수 있습니다. 이렇게 하면 로컬에 Hugo와 Go를 설치하지 않고도 블로그를 관리할 수 있습니다. 아래 단계에 따라 진행하세요:

#### 1. Hugo 블로그 레포지토리 설정

1. **Hugo 블로그 포크**: Hugo 블로그 템플릿을 포크하여 자신의 레포지토리를 만듭니다.
2. **포크한 레포지토리 클론**:
    ```sh
    git clone https://github.com/yourusername/your-hugo-repo.git
    cd your-hugo-repo
    ```

#### 2. GitHub Pages 설정

1. **GitHub Pages 활성화**: GitHub에서 포크한 레포지토리의 "Settings" > "Pages"로 이동합니다. "Source"를 `gh-pages` 브랜치로 설정하고 저장합니다.

#### 3. GitHub Actions 설정

1. **GitHub Actions 워크플로우 파일 추가**:
    레포지토리 루트에 `.github/workflows/gh-pages.yml` 파일을 생성합니다.
    ```yaml
    name: GitHub Pages

    on:
      push:
        branches:
          - main  # 또는 당신의 기본 브랜치 이름

    jobs:
      deploy:
        runs-on: ubuntu-latest

        steps:
        - name: Checkout
          uses: actions/checkout@v2

        - name: Setup Hugo
          uses: peaceiris/actions-hugo@v2
          with:
            hugo-version: '0.92.2'  # 원하는 Hugo 버전

        - name: Build
          run: hugo --minify

        - name: Deploy
          uses: peaceiris/actions-gh-pages@v3
          with:
            github_token: ${{ secrets.GITHUB_TOKEN }}
            publish_dir: ./public
    ```

2. **커밋 및 푸시**:
    ```sh
    git add .github/workflows/gh-pages.yml
    git commit -m "Add GitHub Actions workflow for Hugo"
    git push origin main
    ```

#### 4. GitHub Actions 워크플로우 실행

이제 커밋이나 푸시를 하면 GitHub Actions가 자동으로 실행되어 Hugo 사이트를 빌드하고 `gh-pages` 브랜치에 배포합니다. 이후 GitHub Pages가 이 브랜치의 내용을 호스팅하게 됩니다.

### GitHub에서 직접 수정

GitHub에서 직접 블로그 콘텐츠를 수정하려면 다음을 참고하세요:

1. **GitHub 웹 UI를 통해 파일 수정**:
    - GitHub 저장소로 이동하여 원하는 파일을 찾아 수정합니다.
    - "Commit changes" 버튼을 클릭하여 변경 사항을 커밋합니다.

2. **새 게시물 작성**:
    - `content/posts` 디렉토리에 새로운 마크다운 파일을 추가합니다.
    - 게시물 내용을 작성하고 커밋합니다.

이 방법을 통해 로컬 환경에 Hugo나 Go를 설치하지 않고도 GitHub Pages에서 Hugo 블로그를 호스팅하고 관리할 수 있습니다. 모든 작업을 GitHub의 웹 인터페이스를 통해 수행할 수 있으며, 변경 사항은 GitHub Actions를 통해 자동으로 배포됩니다.
