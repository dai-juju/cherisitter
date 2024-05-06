1. 중고 유아용품 거래 중개 및 구독 서비스를 통해 유아용품을 합리적인 가격으로 구매할 수 있게 한다.
2. 유저들은 유아용품 들의 가격 비교가 가능하며 및 구성 성분을 알 수 있다.

   중고 거래 중개 플랫폼

판매자와 구매자를 연결하는 마켓플레이스
상품 등록, 검색, 구매, 결제, 리뷰 기능
안전 거래를 위한 에스크로 시스템
실시간 채팅 및 알림 기능


유아용품 구독 서비스

제품 카탈로그 및 정기 배송 설정
선호 브랜드 및 유형 등록
자동 재주문 및 결제 시스템


제품 정보 및 가격 비교

상세 제품 정보 및 성분 Data
유사 제품 간 가격 비교 기능
상품 리뷰 및 평점 시스템


기타 주요 기능

소셜 공유 및 친구 추천 시스템
관심상품 알림 및 세일 정보 제공


    User ||--o{ Order : places
    User ||--o{ Review : writes
    User ||--o{ Subscription : has
    User ||--|{ Wishlist : has
    
    Order }|--|| OrderItem : contains
    OrderItem }|--|{ Product : describes
    
    Review }|--|{ Product : reviews
    
    Subscription ||--|{ SubscriptionPlan : follows
    
    Product ||--o{ Category : belongs_to
    Product ||--|{ Seller : offered_by
    
    Wishlist ||--|{ Product : includes
    
    SubscriptionPlan ||--|{ Product : includes
    SubscriptionPlan ||--|{ DeliveryFrequency : has
    
    Seller ||--o{ Product : offers
    
    Category {
        int CategoryID
        string Name
        string Description
    }
    
    Product {
        int ProductID 
        string Name
        string Description
        double Price
        int Quantity
        string Ingredients
    }
    
    Review {
        int ReviewID
        int Rating 
        string Comments
    }
    
    Order {
        int OrderID
        date OrderDate
        double TotalAmount
        string Status
    }
    
    OrderItem {
        int OrderItemID
        int Quantity
        double Price
    }
    
    User {
        int UserID
        string Name 
        string Email
        string Password
    }
    
    Wishlist {
        int WishlistID
    }
    
    Subscription {
        int SubscriptionID  
        date StartDate
        date EndDate
    }

    SubscriptionPlan {
        int PlanID
        string Name
        double Price  
    }
    
    DeliveryFrequency {
        int FrequencyID
        string Interval 
    }
    
    Seller {
        int SellerID
        string Name
        string Email 
    }

    |app: products|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'products/'|GET|전체 제품 목록 조회||||
|'products/'|POST|새 제품 등록||✅|✅|
|'<int:pk>/'|GET|특정 제품 상세 조회||||
|'<int:pk>/'|PUT|특정 제품 정보 수정||✅|✅|
|'<int:pk>/'|PATCH|특정 제품 정보 부분 수정||✅|✅|
|'<int:pk>/'|DELETE|특정 제품 삭제|||✅|
|'categories/'|GET|전체 카테고리 목록 조회||||
|'categories/<int:pk>/'|GET|특정 카테고리 제품 조회||||
|'sellers/'|GET|전체 판매자 목록 조회||||
|'sellers/<int:pk>/'|GET|특정 판매자의 제품 조회||||

|app: orders|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'orders/'|GET|현재 사용자의 주문 내역 조회|✅|||
|'orders/'|POST|새 주문 생성|✅|||
|'<int:pk>/'|GET|특정 주문 상세 조회|✅|||
|'<int:pk>/'|PUT|특정 주문 정보 수정|✅||✅|
|'<int:pk>/'|DELETE|특정 주문 취소|✅||✅|

|app: reviews|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'reviews/'|GET|전체 리뷰 목록 조회||||
|'reviews/'|POST|새 리뷰 작성|✅|||
|'<int:pk>/'|GET|특정 리뷰 조회||||
|'<int:pk>/'|PUT|특정 리뷰 수정|✅|✅||
|'<int:pk>/'|DELETE|특정 리뷰 삭제|✅|✅|✅|

|app: subscriptions|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'subscriptions/'|GET|현재 사용자의 구독 내역 조회|✅|||
|'subscriptions/'|POST|새 구독 생성|✅|||
|'<int:pk>/'|GET|특정 구독 상세 조회|✅|||
|'<int:pk>/'|PUT|특정 구독 수정|✅|||
|'<int:pk>/'|DELETE|특정 구독 취소|✅|||
|'plans/'|GET|전체 구독 플랜 목록 조회||||
|'plans/<int:pk>/'|GET|특정 구독 플랜 상세 조회||||

|app: wishlists|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'wishlists/'|GET|현재 사용자의 위시리스트 조회|✅|||
|'wishlists/'|POST|새 상품 위시리스트에 추가|✅|||
|'<int:pk>/'|DELETE|위시리스트에서 상품 삭제|✅|||

