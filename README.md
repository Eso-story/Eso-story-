# Eso-story-
تضم المدونة أقسامًا رئيسية وفرعية مثل قصص الأطفال، القصص المصورة، قصص الخيال العلمي، قصص الرعب، والقصص الرومانسية، مما يسهل على القراء استكشاف القصص المفضلة لديهم. تتيح المدونة للمستخدمين تسجيل حساباتهم، إضافة تعليقات على القصص، والتفاعل مع المحتوى من خلال التقييمات والتعليقات.بة.
CREATE DATABASE blog_db;

USE blog_db;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE
);

CREATE TABLE categories (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL
);

CREATE TABLE stories (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    category_id INT,
    user_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES categories(id),
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE comments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    story_id INT,
    user_id INT,
    content TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (story_id) REFERENCES stories(id),
    FOREIGN KEY (user_id) REFERENCES users(id)
);

INSERT INTO categories (name) VALUES ('قصص أطفال'), ('قصص مصورة'), ('قصص خيال علمي'), ('قصص رعب'), ('قصص رومانسية');
/blog
    /css
        style.css
    /includes
        db.php
        header.php
        footer.php
    /stories
        index.php
        view.php
    /users
        register.php
        login.php
        logout.php
    /search
        search.php
    index.php
    add_story.php
    <?php
session_start();

$servername = "localhost";
$username = "root";
$password = "";
$dbname = "blog_db";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
