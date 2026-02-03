# 모바일 ↔ 서버(DB) 연동 체크리스트

> 목표: DB는 서버에만 두고, 모바일은 모든 데이터를 서버 API에서 가져오는 구조로 정리.

## ✅ 코드 기준으로 이미 연결된 항목
- [x] **API 베이스 구성**: `EXPO_PUBLIC_API_BASE_URL` 사용 (모바일 `api.ts`).
- [x] **인증 토큰 저장/사용**: 로그인 응답의 `token`을 AsyncStorage에 저장 후 Bearer로 전송.
- [x] **로그인/회원가입**: `/api/login`, `/api/signup` 호출.
- [x] **내 정보 조회**: `/api/me` 호출.
- [x] **피드/글 목록**: `/api/posts` 호출.
- [x] **글 상세**: `/api/posts/:id` 호출.
- [x] **좋아요 토글**: `/api/posts/:id/toggle-like` 호출.
- [x] **작가 프로필/글 목록**: `/api/users/:id/profile`, `/api/users/:id/posts` 호출.

## 🔄 연결이 필요한 항목 (남은 할 일)
- [ ] **글 작성 API 연결**: `POST /api/posts` 연동 (현재 Write 화면에 TODO 주석만 있음).
- [ ] **글 수정/삭제**: `PUT /api/posts/:id`, `DELETE /api/posts/:id` 연동.
- [ ] **글 편집 초기 데이터**: `GET /api/posts/:id/edit` 연동.
- [ ] **북마크 폴더/아이템**: `/api/bookmarks/...` 전 구간 연동.
- [ ] **글 기준 북마크 상태 조회**: `GET /api/posts/:postId/bookmarks`.
- [ ] **팔로우 토글**: `POST /api/users/:id/follow`.
- [ ] **내가 쓴 글/좋아요 글 목록**: `/api/posts/my`, `/api/posts/liked`.
- [ ] **성장/업적/퀘스트**: `/api/growth/summary`, `/api/growth/achievements`, `/api/quests/active`.
- [ ] **로그아웃 처리**: `/api/logout` 호출 + 토큰 정리 동작 확인.

## ⚙️ 환경/운영 체크
- [ ] **모바일 개발 환경에서 서버 접근 가능**: CORS 허용 도메인/호스트에 Expo 디바이스 IP 포함.
- [ ] **서버 실행/마이그레이션**: 서버 DB 마이그레이션/시드 스크립트 실행 여부 확인.
- [ ] **에러 포맷 통일**: `{ ok: false, message }` 응답 규약을 모바일 에러 처리와 동기화.

---

필요하면 이 체크리스트를 기준으로 모바일 화면별 연동 작업을 순차적으로 진행하면 됩니다.
