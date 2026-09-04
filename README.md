# 황은유 자기소개 홈페이지

빌드 도구 없는 정적 멀티페이지 사이트입니다. Tailwind Play CDN을 쓰고, 디자인 토큰·네브바·푸터는 `assets/`에서 공유합니다.

## 라우트

| 경로 | 파일 | 설명 |
| --- | --- | --- |
| `/` | `index.html` | 홈 (히어로 · 경력 카드 · 갤러리 캐러셀 · 협업 CTA) |
| `/demo/` | `demo/index.html` | 라이브러리 게임 데모 — 책 주제 찾기(KDC) 5문제 |

홈 내부 앵커: `#about`, `#career`, `#gallery`, `#contact`

## 폴더 구조

```
.
├── index.html              # 홈
├── demo/index.html         # 게임 데모 라우트
├── assets/
│   ├── tailwind.config.js  # 디자인 토큰 (DESIGN.md와 1:1)
│   ├── base.css            # 리셋 · 앵커 스크롤 오프셋 · 모션 감소 대응
│   ├── site.js             # 네브바/푸터 렌더링, 메뉴 활성화, 모바일 메뉴, 갤러리 캐러셀
│   └── game.js             # 데모 게임 문제 + 채점 로직
├── DESIGN.md               # 디자인 시스템 명세 (Stitch 내보내기)
└── docs/                   # 참고 스크린샷
```

## 자주 고치는 곳

| 바꾸고 싶은 것 | 위치 |
| --- | --- |
| 이름 · 소개 문구 · 메일 · SNS 링크 | `assets/site.js` 상단 `PROFILE` |
| 메뉴 항목 | `assets/site.js` 상단 `NAV` (네브바·모바일 메뉴·푸터에 한 번에 반영) |
| 경력 카드 | `index.html` 의 `#career` 섹션 `<article>` |
| 갤러리 사진 · 키워드 | `index.html` 의 `#gallery` 섹션 `<figure>` (`figcaption`이 키워드) |
| 게임 문제 | `assets/game.js` 상단 `QUESTIONS` |
| 색상 · 타이포 토큰 | `assets/tailwind.config.js` |

푸터 저작권 연도는 `new Date().getFullYear()`로 매년 자동으로 바뀝니다.

## 로컬 실행

```bash
python -m http.server 8123
```

<http://localhost:8123/> (홈), <http://localhost:8123/demo/> (게임 데모)

## 배포 메모

- Netlify · Vercel · GitHub Pages에 폴더째 올리면 `/demo/`로 접근됩니다.
- 갤러리 사진은 Unsplash 원본 URL을 직접 참조합니다. 오프라인 배포가 필요하면 이미지를 내려받아 `assets/`에 두고 경로를 바꾸세요.
- 프로덕션에서는 Play CDN 대신 Tailwind CLI 빌드를 권장합니다. `assets/tailwind.config.js`의 `theme.extend`를 그대로 쓰면 됩니다.
# example
