# Consumer–Provider Handshake

## Thông tin chung

- Lab: FIT4110 Lab 03
- Ngày: 2026-06-01
- Provider team: team-vision (AI Vision)
- Consumer team: team-core (Core Business)
- Provider service: AI Vision Service
- Consumer service: Core Business Service

## Contract

- Contract file: team-core.openapi.yaml
- Mock base URL: http://localhost:4010
- Auth method: Bearer Token
- Endpoint được test: POST /vision/face-match

## Smoke test

### Request

```http
POST /vision/face-match
Authorization: Bearer lab-token
Content-Type: application/json
```

```json
{
  "imageRef": "https://campus.local/images/card-scan-001.jpg",
  "requestId": "0196fb3d-4ad7-7d1e-9f49-5d5148d2babc",
  "cameraId": "CAM-002",
  "timestamp": "2026-05-10T08:01:00Z"
}
```

### Expected response

```json
{
  "detectionId": "123e4567-e89b-12d3-a456-426614174000",
  "detectionType": "FACE",
  "faceMatched": true,
  "isLive": true,
  "confidence": 0.92,
  "status": "success",
  "matchedPersonId": "PERSON-1234"
}
```

## Kết quả

- [x] Consumer gọi mock thành công.
- [x] Consumer parse được field cần dùng.
- [x] Consumer hiểu lỗi 4xx/5xx provider trả về.
- [x] Có Newman report hoặc screenshot.

## Ghi chú thay đổi hợp đồng

| Nội dung | Trước | Sau | Người đồng ý |
|---|---|---|---|
| | | | |

## Xác nhận

- Provider representative: team-vision lead
- Consumer representative: team-core lead
