# Employee-Leave-Management
Leave Management System Using SpringBoot for Backend and Angular for Frontend 
 Github Link:
- [x] Backend: https://github.com/JatinThakur2/Employee-Leave-Management
- [ ] Frontend: https://github.com/JatinThakur2/Leave-Management-System

### General Commands
To run sql files
```sql
CREATE DATABASE IF NOT EXISTS `leavemanagement`;
USE `leavemanagement`;
```
Structure for table leavemanagement.employee
```structure for table leavemanagement.employee
CREATE TABLE IF NOT EXISTS `employee` (
  `employee_id` bigint(20) NOT NULL AUTO_INCREMENT,
  `created_at` datetime NOT NULL,
  `email` varchar(255) DEFAULT NULL,
  `first_name` varchar(255) DEFAULT NULL,
  `last_name` varchar(255) NOT NULL,
  `middle_name` varchar(255) DEFAULT NULL,
  `password` varchar(255) NOT NULL,
  `phone_number` varchar(255) NOT NULL,
  `role` varchar(255) NOT NULL,
  `status` varchar(255) NOT NULL,
  `username` varchar(255) NOT NULL,
  `group_id` bigint(20) DEFAULT NULL,
  `supervisor` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`employee_id`),
  UNIQUE KEY `UK_im8flsuftl52etbhgnr62d6wh` (`username`),
  KEY `FKaqbqb3qdsfq2f9v3nj7ddgj57` (`group_id`),
  KEY `FK5amfhprgb3rrhxjx7rq3al980` (`supervisor`),
  CONSTRAINT `FK5amfhprgb3rrhxjx7rq3al980` FOREIGN KEY (`supervisor`) REFERENCES `employee` (`employee_id`),
  CONSTRAINT `FKaqbqb3qdsfq2f9v3nj7ddgj57` FOREIGN KEY (`group_id`) REFERENCES `employee_group` (`group_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=latin1;
```
Data for table leavemanagement.employee: 
```data for table leavemanagement.employee: 
REPLACE INTO `employee` (`employee_id`, `created_at`, `email`, `first_name`, `last_name`, `middle_name`, `password`, `phone_number`, `role`, `status`, `username`, `group_id`, `supervisor`) VALUES
	(1, '2022-05-12 20:01:33', 'admin@gmail.com', 'admin', 'admin', NULL, '$2a$10$9YBWBYJhjSYCeOpEzIG/H.WbPqlNa688Fs7klp7P07vOUX27ubwlu', '000000000', 'ROLE_ADMIN', 'ACTIVE', 'admin', NULL, NULL);
```
Structure for table leavemanagement.employee_group
```structure for table leavemanagement.employee_group
CREATE TABLE IF NOT EXISTS `employee_group` (
  `group_id` bigint(20) NOT NULL AUTO_INCREMENT,
  `group_name` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`group_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```
Structure for table leavemanagement.leave_request
```structure for table leavemanagement.leave_request
CREATE TABLE IF NOT EXISTS `leave_request` (
  `leave_id` bigint(20) NOT NULL AUTO_INCREMENT,
  `created_at` datetime NOT NULL,
  `denied_reason` text DEFAULT NULL,
  `from_date` date NOT NULL,
  `leave_reason` text NOT NULL,
  `status` varchar(255) NOT NULL,
  `to_date` date NOT NULL,
  `employee_id` bigint(20) NOT NULL,
  `leave_type` bigint(20) NOT NULL,
  `reviewed_by` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`leave_id`),
  KEY `FKtc4wao0ica39vusknbo96ln2w` (`employee_id`),
  KEY `FK7nc4hxm1gc3ud3kq7612sgleg` (`leave_type`),
  KEY `FKlm66o70qrqubdmyxha1r817k1` (`reviewed_by`),
  CONSTRAINT `FK7nc4hxm1gc3ud3kq7612sgleg` FOREIGN KEY (`leave_type`) REFERENCES `leave_type` (`leave_type_id`),
  CONSTRAINT `FKlm66o70qrqubdmyxha1r817k1` FOREIGN KEY (`reviewed_by`) REFERENCES `employee` (`employee_id`),
  CONSTRAINT `FKtc4wao0ica39vusknbo96ln2w` FOREIGN KEY (`employee_id`) REFERENCES `employee` (`employee_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```


Structure for table leavemanagement.leave_type
```structure for table leavemanagement.leave_type
CREATE TABLE IF NOT EXISTS `leave_type` (
  `leave_type_id` bigint(20) NOT NULL AUTO_INCREMENT,
  `status` varchar(255) NOT NULL,
  `type_name` varchar(255) NOT NULL,
  PRIMARY KEY (`leave_type_id`),
  UNIQUE KEY `UK_neurrpkaxg9cheirk5cr06kgk` (`type_name`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```
Structure for table leavemanagement.oauth_access_token

```structure for table leavemanagement.oauth_access_token
CREATE TABLE IF NOT EXISTS `oauth_access_token` (
  `token_id` varchar(255) DEFAULT NULL,
  `token` mediumblob DEFAULT NULL,
  `authentication_id` varchar(255) NOT NULL,
  `user_name` varchar(255) DEFAULT NULL,
  `client_id` varchar(255) DEFAULT NULL,
  `authentication` mediumblob DEFAULT NULL,
  `refresh_token` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`authentication_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```
Structure for table leavemanagement.oauth_refresh_token
``` structure for table leavemanagement.oauth_refresh_token
CREATE TABLE IF NOT EXISTS `oauth_refresh_token` (
  `token_id` varchar(255) DEFAULT NULL,
  `token` mediumblob DEFAULT NULL,
  `authentication` mediumblob DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```
