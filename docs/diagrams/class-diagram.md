# Class диаграммасы

Hotel Booking System жүйесінің негізгі кластары.

```mermaid
classDiagram
    class User {
        +int id
        +string fullName
        +string email
        +string phone
        +string password
        +login()
        +logout()
    }

    class Guest {
        +searchRooms()
        +createBooking()
        +updateBooking()
        +cancelBooking()
    }

    class Admin {
        +addRoom()
        +updateRoom()
        +deleteRoom()
        +viewAllBookings()
    }

    class Room {
        +int id
        +string roomNumber
        +string type
        +int capacity
        +decimal pricePerNight
        +bool isAvailable
        +checkAvailability()
    }

    class Booking {
        +int id
        +date checkInDate
        +date checkOutDate
        +string status
        +decimal totalPrice
        +confirm()
        +cancel()
        +calculatePrice()
    }

    class Payment {
        +int id
        +decimal amount
        +string method
        +date paymentDate
        +string status
        +process()
    }

    User <|-- Guest
    User <|-- Admin
    Guest "1" --> "0..*" Booking : жасайды
    Room "1" --> "0..*" Booking : брондалады
    Booking "1" --> "0..1" Payment : төленеді
    Admin "1" --> "0..*" Room : басқарады
```

## Кластардың сипаттамасы

| Класс | Міндеті |
|---|---|
| User | Жүйе пайдаланушысының жалпы деректері |
| Guest | Бөлме іздейтін және брондайтын қонақ |
| Admin | Бөлмелер мен брондауларды басқаратын әкімші |
| Room | Қонақүй бөлмесі |
| Booking | Брондау ақпараты (күндер, күйі, құны) |
| Payment | Брондау төлемі |
