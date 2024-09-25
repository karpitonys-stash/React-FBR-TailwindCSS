# React + File-Based Routing + TailwindCSS

> [!WARNING]
> - 개인용 보일러플레이트
> - 항상 패키지 버전을 잘 확인하기

- React + Vite
- TypeScript + [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc)
- [@vite-plugin-next-react-router](https://github.com/zoubingwu/vite-plugin-next-react-router)를 사용한 파일 구조 라우터

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
