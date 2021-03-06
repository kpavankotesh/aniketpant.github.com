---
author: Aniket
title: Password Security and Hashing
layout: post
type: post
category: note
tags:
  - bcrypt
  - Codeigniter
  - Hashing
  - Password
  - PHPass
  - Problem
---

My old problem was not solved by now, and I was going through a question on Stack Overflow.

I got to know that MD5 should not be used in anyway. Then I read about SHA1 vs bcrypt. After quite some discussion and thanks to [Lawrence](http://about.me/dclawrence), I got a brilliant solution and really good lesson on password hashing.

Now, I would be using bcrypt to hash my passwords.

See this post for the [solution](http://stackoverflow.com/questions/7044785/what-is-the-safest-way-to-store-a-password-using-code-igniter/7045061).

To implement this password hashing technique, there is a library available.

1.  Download the files from [here](http://www.openwall.com/phpass/).
2.  Then, extract the files to application/library.

#### Load the library

```php
$this->load->library('PasswordHash',array(8, FALSE));
```

#### How to hash the password?

```php
$this->PasswordHash->HashPassword($password);
```

#### Check if a password is correct?

```php
$password = $_POST['password'];
$actualPassword = /*Get the hashed password from your db*/;

$check = $this->PasswordHash->CheckPassword($password, $actualPassword);
```

If you are not using CI, you can go through this [link](http://dev.myunv.com/articles/secure-passwords-with-phpass).