---
tags:
  - exercise
  - begginer
---
## My solution to the task

```cs
string permission = "Manager";

int level = 15;

  
if (level > 55 && permission.Contains("Admin"))
{
    Console.WriteLine("Welcome, super admin user");
}

else if (level >= 55 && permission.Contains("Admin"))
{
    Console.WriteLine("Welcome, Admin user.");
}

else if (level >= 20 && permission.Contains("Manager"))
{
    Console.WriteLine("Contact an Admin for access.");
}

else if (level < 20 && permission.Contains("Manager"))
{
    Console.WriteLine("You dont have sufficient privileges.");
}

else if (!permission.Contains("Admin") || !permission.Contains("Manager"))
{
    Console.WriteLine("You dont have sufficient privileges.");
}
```

## Better solution

```cs
string permission = "Admin|Manager";
int level = 53;

if (permission.Contains("Admin"))
{
    if (level > 55)
    {
        Console.WriteLine("Welcome, Super Admin user.");
    }
    else
    {
        Console.WriteLine("Welcome, Admin user.");
    }
}
else if (permission.Contains("Manager"))
{
    if (level >= 20)
    {
        Console.WriteLine("Contact an Admin for access.");
    }
    else
    {
        Console.WriteLine("You do not have sufficient privileges.");
    }
}
else
{
    Console.WriteLine("You do not have sufficient privileges.");
}
```

[[Exercise]]