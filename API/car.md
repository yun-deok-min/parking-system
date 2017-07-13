# Car

## GET `cars/:numbering'

`:numbering`에 해당하는 차량의 현재 주차정보와 위치를 반환
주차중이라면 입차시간 까지

### Response

> 현재 주차중일 때

```json
{
    "car": {
        "numbering": "88허1234",
        "start_at": 1234567890 //타임스탬프
    },
    "place": {
        "zone_name": "A",
        "zone_index": 1,
        "floor": 2
    }
}
```

> 현재 주차중이 아닐 때

```json
{
    "car": {
        "numbering": "88허1234"
    },
    "place": null
}
```
