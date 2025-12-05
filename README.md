# GitHub Pages 배포 가이드 (정적 HTML + Tailwind 프로젝트)

### 1. TailwindCSS 빌드
- 개발 모드 실행
```
npm run dev
```

- 배포용 CSS 빌드
```
npm run build
```

- 빌드 결과물은 다음 경로에 생성됨
```
aurora/output.css
````

### 2. CSS 연결 확인

- index.html이 Tailwind 빌드 CSS를 정확한 경로로 로드하는지 확인
```
<link rel="stylesheet" href="./aurora/output.css" />
```

- 경로가 틀리면 GitHub Pages에서 스타일이 적용되지 않음

### 3. GitHub Pages 설정

```
GitHub → Repository → Settings → Pages
```

- 다음과 같이 설정
```
Source: Deploy from a branch

Branch: main

Folder: / (root)
```
- index.html이 루트에 있기 때문에 / 선택

### 4. 변경사항 푸시
```
git add .
git commit -m "deploy"
git push
```
- 푸시 후 GitHub Pages가 자동으로 사이트를 배포함

### 5. 배포 주소
```
https://USERNAME.github.io/REPO/
```

- USERNAME과 REPO는 본인 GitHub 정보로 변경

### 6. (선택) 커스텀 도메인 연결
- Settings → Pages → Custom domain 에서 구입한 도메인을 연결 가능

<hr/>

⚠️**주의사항** :  **빌드 후 파일 경로에 대한 중요 참고 사항TailwindCSS를 빌드할 때, 프로젝트 구조가 다음과 같다고 가정**
```
/ (루트)
├── index.html
├── aurora/
│   └── output.css  <-- 빌드 결과
└── package.json
```
- 빌드 과정: npm run build를 실행하면 aurora/output.css 파일이 생성됨
- 푸시 확인: git add . 명령을 했을 때, aurora/output.css 파일이 .gitignore에 의해 무시되지 않고 푸시 대상에 포함되는지 최종적으로 확인하기 (정적 파일 배포이므로 빌드 결과물을 푸시하는 것이 일반적)
