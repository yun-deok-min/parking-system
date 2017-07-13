# Entering Log

## GET `entering_logs?car_numbering=:car_numbering`

`:car_numbering`과 관련된 모든 입/출입 로그를 반환

### Response

```json
{
    "entering_logs": [
        {
            "id": 1,
            "start_at": 1234567890, // 타임스탬프
            "end_at": 1234567890    // 타임스탬프
        }
    ]
}
```
