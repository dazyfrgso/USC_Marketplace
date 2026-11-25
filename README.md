# 🛒 USC Marketplace

A campus marketplace where USC students can buy and sell items, message sellers, and save listings to a wishlist. Only verified **@usc.edu** accounts can post or chat, which keeps it a trusted, students-only space.

> Built by a 7-person team for USC CSCI 201 (Principles of Software Development), Spring 2026. This is my fork; the original repo is [AnWilliam/USC_Marketplace](https://github.com/AnWilliam/USC_Marketplace).

## 🎥 Demo

https://github.com/user-attachments/assets/abf50863-510a-4d03-a3a0-7c982574c9a9

## ✨ Features

- **USC-only accounts:** Registration accepts only @usc.edu emails, and passwords are hashed before they're stored.
- **Guest vs. logged-in views:** Guests can browse listings. Logged-in users can post items, message sellers, and use a wishlist, and the navigation changes to match.
- **Listings:** Sellers create listings with a title, description, category, condition, price, and photo, then mark them sold or remove them.
- **Search and filters:** Search by keyword and filter by category and price.
- **Buyer–seller messaging:** One conversation per buyer, seller, and item, with sender names, timestamps, unread counts, and read receipts.
- **Wishlist:** Save listings with one tap and see them as cards on a wishlist page.
- **Profiles:** View and edit your profile and track your active listings.

## 👩‍💻 My Contributions

- **Messaging backend:** Built the conversation-start logic in the service layer, and made messages show sender names instead of user IDs by joining the Users table through the DAO, model, and JSON layers.
- **Message timestamps:** Added formatted timestamps with safe fallbacks, and fixed a timezone bug that showed send times in UTC instead of Pacific time.
- **Wishlist, end to end:** Built `WishlistDAO` and `WishlistServlet` (add, remove, check, and list), the add/remove toggle on item pages, and the wishlist card grid.
- **Design and documentation:** Worked on the team's conceptual design and project documentation, from the proposal and requirements to the testing plan.

## 📱 How It Works

```
 Browser (HTML/CSS/JS)
        │  fetch() → JSON
        ▼
 Servlets ──► Services ──► DAOs ──► MySQL (JDBC)
 (HTTP)       (rules)      (SQL)    users, items, categories,
                                    conversations, messages, wishlist
```

Each request goes through three layers: servlets handle HTTP, services enforce the rules (like USC-only emails and one conversation per item), and DAOs run parameterized SQL queries. Tomcat runs each request on its own thread, so many students can browse and message at the same time.

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | Java, Jakarta Servlets |
| Server | Apache Tomcat 10.1 |
| Database | MySQL, JDBC |
| Testing | JUnit (DAO, service, and servlet tests) |
| Collaboration | Git, GitHub |

## 🚀 Running Locally

1. Import `Marketplace` into Eclipse as a Dynamic Web Project.
2. Set Apache Tomcat 10.1 as the target runtime.
3. Run `Marketplace/database/schema.sql`, then `seed.sql`, in MySQL.
4. Put your MySQL username and password in `Marketplace/src/main/resources/db.properties`.
5. Run on Tomcat and open `http://localhost:8080/Marketplace/`.

## 👥 Team

William An · Songyun Gu · Chelsea Zhang · Yang Chen · Beverlyn Tsai · Daisy Fregoso · Cooper Flowers

## 👤 Author of this fork

**Daisy Fregoso** · [GitHub](https://github.com/dazyfrgso) · [LinkedIn](https://www.linkedin.com/in/daisy-fregoso/)
