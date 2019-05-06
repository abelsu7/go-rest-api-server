# go-rest-api-server

> RESTful API server developed in Go

- 使用 [spf13/viperiper](https://github.com/spf13/viper) 读取**配置文件**`config.yaml`
- 使用 [lexkong/log](https://github.com/lexkong/log) 记录和管理 **API 日志**

## 建表语句

`db.sql`:

```mysql
CREATE DATABASE IF NOT EXISTS `db_apiserver` DEFAULT CHARACTER SET utf8;

USE `db_apiserver`;

--
-- Table structure for table `tb_users`
--

DROP TABLE IF EXISTS `tb_users`;

CREATE TABLE `tb_users`
(
    `id`        bigint(20) unsigned NOT NULL AUTO_INCREMENT,
    `username`  varchar(255)        NOT NULL,
    `password`  varchar(255)        NOT NULL,
    `createdAt` timestamp           NULL DEFAULT NULL,
    `updatedAt` timestamp           NULL DEFAULT NULL,
    `deletedAt` timestamp           NULL DEFAULT NULL,
    PRIMARY KEY (`id`),
    UNIQUE KEY `username` (`username`),
    KEY `idx_tb_users_deletedAt` (`deletedAt`)
) ENGINE = MyISAM
  AUTO_INCREMENT = 2
  DEFAULT CHARSET = utf8;

--
-- Dumping data for table `tb_users`
--

LOCK TABLES `tb_users` WRITE;
INSERT INTO `tb_users`
VALUES (0, 'admin', '$2a$10$veGcArz47VGj7l9xN7g2iuT9TF21jLI1YGXarGzvARNdnt4inC9PG', '2018-05-27 16:25:33',
        '2018-05-27 16:25:33', NULL);
UNLOCK TABLES;
```