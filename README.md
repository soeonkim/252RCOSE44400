# Serverless Review Processing Pipeline

AWS 서버리스 서비스를 활용한 리뷰 감성 분석 파이프라인

## 구조

```
├── lambda_function/
│   ├── lambda_function.py    # Lambda 핸들러
│   ├── Dockerfile            # 컨테이너 빌드 파일
│   └── requirements.txt      # Lambda 의존성
├── request_generator.py      # 테스트 요청 생성기
├── requirements.txt          # 로컬 의존성
└── .env                      # 환경 변수
```

## Lambda 함수 (lambda_function.py)

리뷰 텍스트를 받아 감성 분석 후 DynamoDB에 저장하고, 긍정 리뷰 시 SES로 이메일 전송

- TextBlob을 사용한 감성 분석
- polarity > 0.1: Positive / < -0.1: Negative / 그 외: Neutral

## 요청 생성기 (request_generator.py)

API Gateway로 테스트 리뷰 30개를 비동기로 전송

```bash
pip install -r requirements.txt
# .env에 API_URL 설정 후
python request_generator.py
```
