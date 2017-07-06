# Database 테이블 설계

현재까지 내용으로 설계한 데이터베이스 테이블입니다.

간략하게 표현했고 현재 가능한 정보로는 `주차공간`, `입출입한 모든 차량`, `주차시간`, `입출시간`, `요금계산`, `가상화폐` 입니다.

## ParkingLot

```text
주차공간에 대한 정보
주차장의 공간을 표현한다고 생각하시면됩니다.
현재 주차 중인지 아닌지에 대한 정보는 ParkingLog와의 Join을 통해 도출합니다.
이 테이블은 오직 주차 공간에 대한 정보만 담고 있습니다.


!TODO: 만약 속도면에서 필요하다면 현재 주차상태를 caching 합니다
```

- id            `Primary Key`
- alias_name    별칭
- floor         층수
- zone_name     구역명
- zone_index    구역내 번호

---

## Vehicle

```text
입출입했던 모든 차량에 대한 정보
현재까지 입출입한 모든 차량에 대한 정보만을 포함합니다.
그 차량이 언제 출입했는지에 대한 정보는 EnteringLog or ParkingLog에서 관리합니다.
```

- id
- number        차량번호

---

## ParkingLog

```text
어떤 차량이 어떤 공간에 주차중인지?
주차를 마쳤다면 언제 주차를 시작했는지, 언제 종료했는지 기록합니다.

이를 통해 해당 공간이 사용중인지 아닌지와
어떤 차량이 현재 주차중인지 파악할 수 있습니다.
```

- id
- vehicle_id            `Foreign Key`
- parking_lot_id        `Foreign Key`
- start_at              주차 시작 시각
- end_at                주차 종료 시각

---

## EnteringLog

```text
어떤 차량이 언제 출입했었는지 파악합니다.
이를 통해 차량 출입 빈도를 파악할 수 있습니다.
```

- id
- vehicle_id    `Foreign Key`
- start_at      입차 시각
- end_at        출차 시각

---

## Pricing `보류`

```text
주차요금 테이블입니다.
변경될 수 있기에 완성하지 않고 보류해둡니다.
```

- id
- amount
- 단위에 대한 정보

---

## VitualMoney

가상 화폐 테이블입니다. 우선 차량에 충전된 요금을 귀속시킵니다.

- id
- amount
- vehicle_id
