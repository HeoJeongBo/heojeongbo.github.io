# 허정보 개인 홈페이지 프로젝트

## 프로젝트 개요
- **프로젝트명**: heojeongbo-homepage
- **목적**: 허정보 개인 홈페이지 제작
- **기술 스택**: React, TypeScript, TanStack Router, Vite, TailwindCSS, Biome
- **패키지 매니저**: Bun
- **배포**: GitHub Pages

## 파일 및 디렉토리 명명 규칙

### 파일명 규칙
- **컴포넌트 파일**: `custom.header.tsx`, `ui.button.tsx`, `layout.sidebar.tsx` 
- **유틸리티 파일**: `utils.date.ts`, `helpers.api.ts`
- **훅 파일**: `hooks.auth.ts`, `hooks.data.ts`
- **타입 파일**: `types.user.ts`, `types.api.ts`
- **상수 파일**: `constants.api.ts`, `constants.routes.ts`

**형식**: `카테고리.이름.확장자`
- 카테고리: 파일의 역할/유형 (custom, ui, layout, utils, hooks, types, constants 등)
- 이름: 구체적인 파일명 (header, button, sidebar 등)
- 모든 단어는 소문자

### 디렉토리명 규칙
- **단일 단어만 사용**: `components`, `hooks`, `utils`, `types`, `constants`
- **복수형 사용**: `components` (component 아님)
- **소문자만 사용**: `components` (Components 아님)

### 현재 구조와 변경 필요사항
```
src/
├── components/           ✅ 올바른 디렉토리명
│   └── Header.tsx       ❌ custom.header.tsx로 변경 필요
├── routes/              ✅ 올바른 디렉토리명  
│   ├── __root.tsx       ✅ 라우트 파일은 예외
│   └── index.tsx        ✅ 라우트 파일은 예외
├── main.tsx             ✅ 진입점 파일은 예외
├── logo.svg             ✅ 에셋 파일은 예외
├── styles.css           ✅ 스타일 파일은 예외
└── reportWebVitals.ts   ❌ utils.web-vitals.ts로 변경 필요
```

## 개발 환경 설정

### 패키지 매니저
- **사용**: Bun
- **설치**: `bun install`
- **개발 서버**: `bun run dev`
- **빌드**: `bun run build`
- **린트**: `bun run lint`
- **포맷**: `bun run format`

### 코드 품질 도구
- **Biome**: 린팅 및 포맷팅
- **TypeScript**: 타입 검사
- **설정 파일**: `biome.json`, `tsconfig.json`

## GitHub Pages 배포 설정

### 1. 배포 스크립트 추가
`package.json`에 다음 스크립트 추가:
```json
{
  "scripts": {
    "deploy": "bun run build && gh-pages -d dist"
  }
}
```

### 2. GitHub Pages 설정
1. GitHub 저장소 Settings > Pages
2. Source: Deploy from a branch
3. Branch: gh-pages / (root)

### 3. Base URL 설정
`vite.config.ts`에 GitHub Pages용 base URL 추가:
```typescript
export default defineConfig({
  base: '/heojeongbo.github.io/',
  // ... 기타 설정
})
```

### Git 저장소 설정
```bash
git remote add origin https://github.com/HeoJeongBo/heojeongbo.github.io.git
```

### 4. 배포 명령어
```bash
# 의존성 설치 (gh-pages)
bun add -d gh-pages

# 배포 실행
bun run deploy
```

## 프로젝트 구조 목표

```
src/
├── components/
│   ├── custom.header.tsx
│   ├── custom.footer.tsx
│   ├── ui.button.tsx
│   ├── ui.card.tsx
│   └── layout.main.tsx
├── hooks/
│   ├── hooks.theme.ts
│   └── hooks.navigation.ts
├── utils/
│   ├── utils.web-vitals.ts
│   └── utils.format.ts
├── types/
│   ├── types.common.ts
│   └── types.components.ts
├── constants/
│   ├── constants.routes.ts
│   └── constants.theme.ts
├── routes/
│   ├── __root.tsx
│   ├── index.tsx
│   ├── about.tsx
│   └── contact.tsx
├── assets/
│   ├── images/
│   └── icons/
├── styles/
│   ├── globals.css
│   └── components.css
├── main.tsx
└── vite-env.d.ts
```

## 개발 가이드라인

### 컴포넌트 작성
- 함수형 컴포넌트 사용
- TypeScript 타입 정의 필수
- Props 인터페이스는 파일 상단에 정의

### 스타일링
- TailwindCSS 활용
- 커스텀 CSS는 최소화
- 반응형 디자인 고려

### 라우팅
- TanStack Router 사용
- 파일 기반 라우팅
- 타입 안전한 라우팅

## 빌드 및 배포

### 로컬 개발
```bash
bun run dev     # 개발 서버 시작 (포트 3000)
bun run build   # 프로덕션 빌드
bun run serve   # 빌드된 파일 미리보기
```

### 코드 품질 검사
```bash
bun run lint    # 린트 검사
bun run format  # 코드 포맷팅
bun run check   # 전체 검사 (린트 + 포맷)
```

### GitHub Pages 배포
```bash
bun run deploy  # GitHub Pages에 배포
```

## 참고사항
- 모든 파일은 UTF-8 인코딩
- 개행 문자는 LF 사용
- 들여쓰기는 탭(tab) 사용 (Biome 설정에 따름)
- 따옴표는 큰따옴표(") 사용