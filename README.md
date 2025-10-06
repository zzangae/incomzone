## 구조 요약 (시각적 흐름)
<pre>
사용자 브라우저
   ↓
DNS 질의: www.incomzone.co.kr
   ↓
GitHub Pages (index.html)
   ↓
JS 실행
   ├─ [08~20시]
   │    ├─ VM 응답 OK → Redirect to http://incomzone.co.kr
   │    └─ VM 응답 없음 → Stay (GitHub Pages)
   └─ [20~08시] Stay (GitHub Pages)
</pre>
DNS 구성(@ → VM / www → GitHub Pages) 이 정확하게 적용되었고,<br>
index.html 의 JS 시간·상태 감지 로직도 정상 작동 중이며,<br>
현재(08~20시 KST) 시간대에는 의도대로 VM이 우선 표시되는 상태라는 뜻입니다.<br>
즉, 지금 구조가 완전한 “이중 전환형 구조”로 성공적으로 작동 중이에요.

|구분|도메인|연결 대상|시간대별 표시 결과|
|--|--|--|--|
|GitHub Pages|www.incomzone.co.kr|zzangae.github.io	야간(20~08시)|그대로 표시|
|VM 서버|incomzone.co.kr|VM 공인 IP 주간(08~20시) | JS 감지 후 자동 리디렉트|
