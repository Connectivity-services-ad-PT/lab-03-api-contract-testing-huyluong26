# Consumer–Provider Handshake

## Thông tin chung

- Lab: FIT4110 Lab 03
- Ngày: 01/06/2026
- Provider team: B4 (AI Vision - team-vision)
- Consumer team: B6 (Core Business - team-core)
- Provider service: AI Vision Service
- Consumer service: Core Business Service

## Contract

- Contract file: `contracts/ai-vision.openapi.yaml`
- Mock base URL: `http://localhost:4010` (hoặc `4011` tuỳ config mock)
- Auth method: Bearer Token
- Endpoint được test: `POST /vision/face-match`

## Smoke test

### Request

```http
POST /vision/face-match
Authorization: Bearer <your-auth-token>
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
  "detectionId": "b65103cb-64bc-4fc5-bf0b-6a98f1f7d5c7",
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
| Bổ sung liveness check | Không có | Thêm trường `isLive: boolean` | Đại diện B4 & B6 |
| Thống nhất UUID format | Dùng ID thường | Chuẩn hoá `format: uuid` | Đại diện B4 & B6 |

## Xác nhận

- Provider representative: Đại diện nhóm B4 (AI Vision)
- Consumer representative: Hoàng Văn Thi (Đại diện B6 - Core Business)
