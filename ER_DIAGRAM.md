erDiagram
  USER ||--|o PATIENT : "can be"
  USER ||--|o DOCTOR : "can be"
  DOCTOR ||--o{ AVAILABILITY : "offers"
  PATIENT ||--o{ APPOINTMENT : "books"
  AVAILABILITY ||--|o APPOINTMENT : "reserved by"

  USER {
    int id PK
    varchar name
    varchar email UK
    varchar password_hash
    varchar role
    timestamp created_at
  }
  PATIENT {
    int id PK
    int user_id FK, UK
    date date_of_birth
    varchar phone
  }
  DOCTOR {
    int id PK
    int user_id FK, UK
    varchar specialty
    decimal consultation_fee
  }
  AVAILABILITY {
    int id PK
    int doctor_id FK
    date date
    time start_time
    time end_time
    boolean is_booked
  }
  APPOINTMENT {
    int id PK
    int patient_id FK
    int availability_id FK, UK
    varchar status
    varchar reason
  }