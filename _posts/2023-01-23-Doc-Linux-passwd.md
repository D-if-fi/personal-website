---
title: "：如何使用 passwd 命令锁定、解锁和检查 Linux 中给定用户帐户的状态"
published: true
categories: [Doc]
tags: [Linux]
---


<hr>

**passwd**：用于更新用户的身份验证令牌。这个任务是通过调用 Linux PAM 和 libuser API 来实现。

**usermod**：用于修改/更新给定用户的帐户信息。它用于将用户添加到特定的组中等等功能。*
## passwd 用法 ： 
### 如何使用 passwd 命令锁定、解锁和检查 Linux 中给定用户帐户的状态？
使用 -l 开关运行 passwd 命令，锁定给定的用户帐户。

```
# passwd -l yyds
Locking password for user yyds.
passwd: Success
```
你可以通过 passwd 命令或从 /etc/shadow 文件中获取给定用户名来检查锁定的帐户状态。

使用 passwd 命令检查用户帐户锁定状态。

```
# passwd -S yyds

或

# passwd --status yyds
yyds  PS 2022-07-27 -1 -1 -1 -1 (Password set, SHA512 crypt.)

```

***LK**：密码被锁定
**NP**：没有设置密码
**PS**：密码已设置*

使用 /etc/shadow 文件检查锁定的用户帐户状态。如果帐户已被锁定，密码前面将添加两个感叹号。

```
# grep daygeek /etc/shadow
yyds:!!$6$tGvVUhEY$PIkpI43HPaEoRrNJSRpM3H0YWOsqTqXCxtER6rak5PMaAoyQohrXNB0YoFCmAuh406n8XOvBBldvMy9trmIV00:18047:7:90:7:::
```
使用 -u 开关运行 passwd 命令，可以解锁给定的用户帐户。

```
# passwd -u yyds
Unlocking password for user yyds.
passwd: Success
```
