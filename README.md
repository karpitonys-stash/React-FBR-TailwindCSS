# React + Folder-Based Routing + TailwindCSS

- [CheckList](#CheckList)
- [Usage](#Usage)
- [Actions](#Actions)

<hr />

> [!WARNING]
> - 개인용 보일러플레이트
> - 항상 패키지 버전을 잘 확인하기

- React + Vite
- TypeScript + [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc)
- [@vite-plugin-next-react-router](https://github.com/zoubingwu/vite-plugin-next-react-router)를 사용한 폴더 구조 라우터

## Checklist
- [ ] Rename name and author fields in `package.json` and `package-lock.json`
(기본 이름은 `boilerplate`)
- [ ] Change the author name in LICENSE
- [ ] Change the favicon in public
- [ ] Clean up the README's

## Usage

패키지 설치
```
npm install
```

로컬에서 미리보기 실행
```
npm run dev
```

> [!WARNING]
> plugin 'vite-plugin-next-router' uses deprecated 'enforce' option. Use 'order' option instead.
> plugin 'vite-plugin-next-router' uses deprecated 'transform' option. Use 'handler' option instead.

- 위와 같은 경고가 뜰 수도 있음
- [@vite-plugin-next-react-router](https://github.com/zoubingwu/vite-plugin-next-react-router)의 문제, 사용하는데 상관 없어보임.

## Actions

```yaml
name: Deploy

on:
    push:
        branches: ['main']

jobs:
    build:
        runs-on: ubuntu-latest
        container: pandoc/latex
        steps:
            - uses: actions/checkout@v2

            - name: Install mustache (to update the date)
              run: apk add ruby && gem install mustache

            - name: creates output
              run: sh ./build.sh

            - name: Pushes to another repository
              id: push_directory
              uses: cpina/github-action-push-to-another-repository@main
              env:
                  API_TOKEN_GITHUB: ${{ secrets.AUTO_ACTIONS }}
              with:
                  source-directory: 'output'
                  destination-github-username: 'karpitony'
                  destination-repository-name: '레포 이름만, ex)9oormdari-Frontend-Deploy'
                  user-email: ${{ secrets.EMAIL }}
                  commit-message: ${{ github.event.commits[0].message }}
                  target-branch: main

            - name: Test get variable exported by push-to-another-repository
              run: echo $DESTINATION_CLONED_DIRECTORY
```
-  Vercel에 무료 배포를 위한 조직 레포에서 개인 레포로 변경사항 동기화 해주는 깃허브 액션
- `.github/workflows/deploy.yml`에 붙여넣기
- 레포지토리 이름 바꿔서 입력하고, 시크릿 입력하기
- - EMAIL에는 이메일 주소, AUTO_ACTIONS에는 ghp 토큰
