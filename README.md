# 재료종합설계 Peer Evaluation GitHub Pages App

정적 HTML 파일 1개로 구성된 peer evaluation 페이지입니다. GitHub Pages에 올려 학생들에게 링크를 공유하면 됩니다. 응답 저장과 중복 제출 방지는 Firebase Firestore를 사용합니다.

## 1. 포함 파일

- `index.html`: 학생 입력 및 peer evaluation 화면
- `firestore.rules`: Firebase Firestore 보안 규칙 예시

## 2. Firebase 설정

1. Firebase Console에서 새 프로젝트를 만듭니다.
2. Project settings → General → Your apps → Web app을 추가합니다.
3. 생성된 `firebaseConfig` 값을 복사합니다.
4. `index.html`의 아래 부분을 실제 값으로 교체합니다.

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

5. Firestore Database를 생성합니다. 위치는 asia-northeast3 또는 기본값을 사용해도 됩니다.
6. Firestore Rules 탭에 `firestore.rules` 내용을 붙여넣고 Publish 합니다.

## 3. GitHub Pages 배포

1. GitHub에서 새 repository를 만듭니다. 예: `materials-peer-evaluation`
2. `index.html`을 업로드합니다.
3. Repository → Settings → Pages로 이동합니다.
4. Branch를 `main`, folder를 `/root`로 선택하고 Save 합니다.
5. 몇 분 후 아래 형태의 링크가 생성됩니다.

```text
https://YOUR_GITHUB_ID.github.io/materials-peer-evaluation/
```

## 4. 결과 확인

Firebase Console → Firestore Database → `peerEvaluations` 컬렉션에서 제출 결과를 확인할 수 있습니다.
CSV가 필요하면 Firestore Export 또는 Firebase Extensions를 사용할 수 있습니다.

## 5. 팀 명단 수정

`index.html`에서 `const teams = [...]` 부분만 수정하면 됩니다.

## 6. 테스트 계정

현재 테스트 계정으로 `조인선`이 추가되어 있습니다. 학번은 `00000000` 또는 임의의 값을 입력해도 됩니다. 이 계정은 실제 팀원 선택지에는 포함되지 않으며, 조인선 교수님 팀의 평가 화면을 확인하는 용도입니다.
