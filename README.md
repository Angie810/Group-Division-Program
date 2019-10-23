# Group-Division-Program
The small program can help you randomly divide students into certain groups.

using System;
using System.Collections.Generic;

namespace ConsoleApp8
{
    class Program
    {
        class Student
        {
            private string Name { get; set; }
            private int studentNum { get; set; }

            public Student(string name, int studentNum)
            {
                this.Name = name;
                this.studentNum = studentNum;
            }

            public override string ToString()
            {
                return "Name: "+Name+"Student No.: "+studentNum.ToString();
            }

        }
        static void Main(string[] args)
        {
            Console.Write("How many students are there in your class?");
            int studentCounts= int.Parse(Console.ReadLine());

            List<Student> listOfStudents = new List<Student>();

            for (int i = 0; i < studentCounts; i++)
            {
                Console.Write("Enter the name of the student: ");
                string name = Console.ReadLine();

                Console.Write("Enter the student number: ");
                int studentNum = int.Parse(Console.ReadLine());

                var student = new Student(name, studentNum);

                listOfStudents.Add(student);
            }

            Console.Write("How many people would you like to have in one group?");
            int groupSize = int.Parse(Console.ReadLine());

            int groupCount = studentCounts / groupSize;

            Random rnd = new Random();

            for (int i = 0; i < groupCount; i++)
            {
                List<Student> list1 = new List<Student>(groupSize);

                for (int j = 0; j < groupSize; j++)
                {
                    int randomNum = rnd.Next(0, studentCounts);
                    list1.Add(listOfStudents[randomNum]);
                    listOfStudents.Remove(listOfStudents[randomNum]);
                    studentCounts--;
                }
                Console.WriteLine();
                foreach (var item in list1)
                {
                    Console.WriteLine("The "+i+" Group: "+item.ToString());
                }
            }

        }
    }
}
