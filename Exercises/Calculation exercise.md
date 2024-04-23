---
tags:
  - exercise
  - begginer
---
```cs
string studentName = "Sophia Johnson";

string course1Name = "English 101";

string course2Name = "Algebra 101";

string course3Name = "Biology 101";

string course4Name = "Computer Science I";

string course5Name = "Psychology 101";

  

int gradeA = 4;

int gradeB = 3;

  

int course1Grade = gradeA;

int course2Grade = gradeB;

int course3Grade = gradeB;

int course4Grade = gradeB;

int course5Grade = gradeA;

  

int course1Credit = 3;

int course2Credit = 3;

int course3Credit = 4;

int course4Credit = 4;

int course5Credit = 3;

  

int totalCreditHours = 0;

totalCreditHours = course1Credit + course2Credit + course3Credit + course4Credit + course5Credit;

  

int totalGradePoints = 0;

totalGradePoints += course1Credit * course1Grade;

totalGradePoints += course2Credit * course2Grade;

totalGradePoints += course3Credit * course3Grade;

totalGradePoints += course4Credit * course4Grade;

totalGradePoints += course5Credit * course5Grade;

  

decimal gpaCalc = (decimal)totalGradePoints / totalCreditHours;

  

int leadingDigit = (int)gpaCalc;

int firstDigit = (int)(gpaCalc * 10) % 10;

int secondDigit = (int)(gpaCalc * 100) % 10;

  
  

Console.WriteLine("Student: " + studentName);

  

Console.WriteLine("Course\t\t\t Grade\t\t Credit Hours");

Console.WriteLine($"{course1Name}\t\t {course1Grade}\t\t {course1Credit}");

Console.WriteLine($"{course2Name}\t\t {course2Grade}\t\t {course2Credit}");

Console.WriteLine($"{course3Name}\t\t {course3Grade}\t\t {course3Credit}");

Console.WriteLine($"{course4Name}\t {course4Grade}\t\t {course4Credit}");

Console.WriteLine($"{course5Name}\t\t {course5Grade}\t\t {course5Credit}");

Console.WriteLine($"\n Final GPA:\t {leadingDigit}.{firstDigit}{secondDigit}");
```

[[Exercise]]