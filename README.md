# PostgreSQL সম্পর্কিত গুরুত্বপূর্ণ প্রশ্ন এবং উত্তর

এই ডকুমেন্টে PostgreSQL ডেটাবেস ম্যানেজমেন্ট সিস্টেমের কিছু গুরুত্বপূর্ণ প্রশ্নের বিস্তারিত উত্তর দেওয়া হয়েছে।

---

### ১. PostgreSQL কী?

PostgreSQL হলো একটি ওপেন-সোর্স এবং শক্তিশালী **রিলেশনাল ডেটাবেস ম্যানেজমেন্ট সিস্টেম (RDBMS)** যা SQL ব্যবহার করে। এটি ACID নীতিমালা অনুসরণ করে ডেটার নিরাপত্তা ও নির্ভরযোগ্যতা নিশ্চিত করে। PostgreSQL JSON, XML, ও অন্যান্য ডেটা টাইপ সাপোর্ট করে যা আধুনিক অ্যাপ্লিকেশনের জন্য খুব উপযোগী।

উদাহরণ:
```sql
SELECT * FROM users;
```
### ২. PostgreSQL-এ ডেটাবেস স্কিমার (schema)-এর উদ্দেশ্য কী?

Schema হলো ডেটাবেসের একটি সংগঠিত কাঠামো যা টেবিল, ভিউ, ফাংশন, ইনডেক্স ইত্যাদি গ্রুপ করে রাখে। এটি এক ডেটাবেসের মধ্যে বিভিন্ন টেবিল বা অবজেক্টকে আলাদা রাখে এবং কনফ্লিক্ট থেকে রক্ষা করে।

উদাহরণ:
```sql
CREATE SCHEMA sales;
CREATE TABLE sales.customers (
    id SERIAL PRIMARY KEY,
    name TEXT
);

```
### ৩. PostgreSQL-এ Primary Key এবং Foreign Key কী?
* Primary Key: একটি কলাম বা কলামসমষ্টি যা প্রতিটি রেকর্ডকে ইউনিক করে এবং নাল হতে দেয় না।
* Foreign Key: অন্য একটি টেবিলের Primary Key কে রেফারেন্স করে, টেবিলগুলোর মধ্যে সম্পর্ক তৈরি করে।

উদাহরণ:
```sql
CREATE TABLE departments (
    id SERIAL PRIMARY KEY,
    name TEXT
);

CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name TEXT,
    department_id INTEGER,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);

```
### ৪. SELECT স্টেটমেন্টে WHERE ক্লজের ব্যবহার কী?

WHERE ক্লজ ব্যবহার করা হয় নির্দিষ্ট শর্ত পূরণ করে এমন রেকর্ড নির্বাচন করার জন্য, অর্থাৎ ডেটা ফিল্টার করার জন্য।

উদাহরণ:
```sql
SELECT * FROM employees WHERE department_id = 3;
```
### ৫. LIMIT এবং OFFSET ক্লজ কেন ব্যবহার করা হয়?

LIMIT এবং OFFSET ক্লজ কোয়েরির ফলাফলকে নির্দিষ্ট সংখ্যক রেকর্ডে সীমাবদ্ধ রাখতে ব্যবহৃত হয়, যা Pagination এর কাজে লাগে।

উদাহরণ:
```sql
SELECT * FROM employees LIMIT 5 OFFSET 10;
```
