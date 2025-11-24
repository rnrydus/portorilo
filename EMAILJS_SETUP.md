# EmailJS 설정 가이드

Contact 폼에서 이메일이 자동으로 전송되도록 하려면 EmailJS를 설정해야 합니다.

## 1. EmailJS 계정 생성
1. https://www.emailjs.com/ 에 접속
2. 무료 계정 생성 (Free 플랜으로 시작 가능)

## 2. 이메일 서비스 추가
1. EmailJS 대시보드에서 "Email Services" 클릭
2. "Add New Service" 클릭
3. Gmail 선택 (또는 원하는 이메일 서비스)
4. Gmail 계정 연결 및 인증

## 3. 이메일 템플릿 생성
1. "Email Templates" 메뉴로 이동
2. "Create New Template" 클릭
3. 다음 정보 입력:
   - **To Email**: `rnrydus2507@gmail.com`
   - **From Name**: `{{from_name}}`
   - **From Email**: `{{from_email}}`
   - **Reply To**: `{{reply_to}}`
   - **Subject**: `포트폴리오 문의: {{from_name}}`
   - **Content**:
     ```
     이름: {{from_name}}
     이메일: {{from_email}}
     
     메시지:
     {{message}}
     ```
4. "Save" 클릭

## 4. Public Key 확인
1. "Account" > "General" 메뉴로 이동
2. "Public Key" 복사

## 5. script.js 파일 수정
1. `script.js` 파일을 엽니다
2. 다음 부분을 찾아 수정:
   ```javascript
   // EmailJS 초기화
   emailjs.init("YOUR_PUBLIC_KEY"); // 여기에 복사한 Public Key를 붙여넣기
   ```
3. 이메일 전송 코드의 주석을 해제하고 Service ID와 Template ID를 입력:
   ```javascript
   await emailjs.send(
       'YOUR_SERVICE_ID',      // Email Services에서 확인한 Service ID
       'YOUR_TEMPLATE_ID',     // Email Templates에서 확인한 Template ID
       {
           to_email: 'rnrydus2507@gmail.com',
           from_name: name,
           from_email: email,
           message: message,
           reply_to: email
       }
   );
   ```
4. mailto 관련 코드는 주석 처리하거나 삭제

## 완료!
이제 Contact 폼에서 "보내기" 버튼을 클릭하면 자동으로 rnrydus2507@gmail.com으로 이메일이 전송됩니다.

