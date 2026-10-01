# 독립 웹페이지 버전 (Firebase)

## 파일
- `index.html` : 앱 전체 (member_note.html을 `python3 build.py`로 변환한 결과. 직접 고치지 말고 원본을 고친 뒤 다시 빌드)
- `firebase-config.js` : Firebase 웹 앱 설정값 (프로젝트마다 다름)
- `firestore.rules` : Firestore 보안 규칙 (Firebase 콘솔 → Firestore → 규칙에 붙여넣기)

## 설정 순서
1. Firebase 프로젝트, 이메일/비밀번호 로그인, Firestore(서울, 프로덕션 모드) 만들기
2. `firestore.rules` 내용을 Firestore → 규칙 탭에 붙여넣고 게시
3. `firebase-config.js`의 값을 콘솔의 firebaseConfig로 교체
4. GitHub 저장소에 `index.html`, `firebase-config.js` 올리고 Settings → Pages에서 배포
5. 배포 주소로 접속해 관리자로 쓸 이메일로 가입 → 콘솔 Authentication에서 그 계정의 UID 복사
6. Firestore → 데이터 → 컬렉션 시작 → ID `admins`, 문서 ID에 그 UID, 필드는 `on` (boolean true) 하나 만들기
7. 페이지를 새로 고침하면 상단에 `관리자` 버튼이 보여요
8. Authentication → 설정 → 승인된 도메인에 `아이디.github.io` 추가 (로그인 오류가 나면)

## 알려진 제한
- 눈바디 사진 올리기는 이 버전에서 지원하지 않아요 (Firebase 저장소는 유료 요금제가 필요해서 뒤로 미뤘어요)
- 가입·동의 문구는 시범용 초안이에요. 정식 서비스 전에 전문가 검토가 필요해요
