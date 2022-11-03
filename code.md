```sql
CREATE TABLE `Courses` (
	`Title` VARCHAR(20),
	`Name` VARCHAR(127),
	`CRN` INT(10),
	`Type` VARCHAR(127),
	`Section` INT(20),
	`Time` VARCHAR(40),
	`Day` VARCHAR(10),
	`Location` VARCHAR(40),
	`Instructor` VARCHAR(20),
	PRIMARY KEY (`CRN`),
  FOREIGN KEY (`Instructor`) REFERENCES Instructors(`NetId`)
);

CREATE TABLE `Students` (
	`first_name` VARCHAR(20),
	`last_name` VARCHAR(20),
	`NetId` VARCHAR(20),
	`email` VARCHAR(127),
	`dept` VARCHAR(10) ,
	PRIMARY KEY (`NetId`),
  FOREIGN KEY (`dept`) REFERENCES Department(`dept`)
);

CREATE TABLE `Instructors` (
	`first_name` VARCHAR(20),
	`last_name` VARCHAR(20),
	`NetId` VARCHAR(20),
	`email` VARCHAR(127),
	`dept` VARCHAR(10),
	PRIMARY KEY (`NetId`),
  FOREIGN KEY (`dept`) REFERENCES Department(`dept`)
);

CREATE TABLE `Department` (
	`dept` VARCHAR(10),
	`Full_Name` VARCHAR(40),
	PRIMARY KEY (`dept`)
);

CREATE TABLE `Enrollment` (
	`enrollment_id` INT(10),
	`GPA` FLOAT(5),
	`student_id` VARCHAR(20),
	`instructor_id` VARCHAR(20),
	`course_id` INT(10),
	PRIMARY KEY (`enrollment_id`),
  FOREIGN KEY (`student_id`) REFERENCES Students(`NetId`),
  FOREIGN KEY (`instructor_id`) REFERENCES Instructors(`NetId`),
  FOREIGN KEY (`course_id`) REFERENCES Courses(`CRN`)
);
```

