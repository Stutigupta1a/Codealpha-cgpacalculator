#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

struct Course
{
    string grade;
    int creditHours;
    double gradePoint;
};

double getGradePoint(string grade)
{
    if (grade == "A+" || grade == "A")
        return 10.0;
    else if (grade == "B+")
        return 9.0;
    else if (grade == "B")
        return 8.0;
    else if (grade == "C+")
        return 7.0;
    else if (grade == "C")
        return 6.0;
    else if (grade == "D")
        return 5.0;
    else
        return 0.0; // F Grade
}

int main()
{
    int n;
    double totalCredits = 0, totalGradePoints = 0;

    cout << "===== CGPA CALCULATOR =====\n";
    cout << "Enter Number of Courses: ";
    cin >> n;

    vector<Course> courses(n);

    for (int i = 0; i < n; i++)
    {
        cout << "\nCourse " << i + 1 << endl;

        cout << "Enter Grade (A+, A, B+, B, C+, C, D, F): ";
        cin >> courses[i].grade;

        cout << "Enter Credit Hours: ";
        cin >> courses[i].creditHours;

        courses[i].gradePoint = getGradePoint(courses[i].grade);

        totalCredits += courses[i].creditHours;
        totalGradePoints += courses[i].gradePoint * courses[i].creditHours;
    }

    double cgpa = totalGradePoints / totalCredits;

    cout << "\n\n===== COURSE DETAILS =====\n";
    cout << left << setw(10) << "Grade"
         << setw(15) << "Credit Hours"
         << setw(15) << "Grade Point" << endl;

    for (int i = 0; i < n; i++)
    {
        cout << left << setw(10) << courses[i].grade
             << setw(15) << courses[i].creditHours
             << setw(15) << courses[i].gradePoint << endl;
    }

    cout << "\nTotal Credits      : " << totalCredits;
    cout << "\nTotal Grade Points : " << totalGradePoints;
    cout << "\nFinal CGPA         : " << fixed << setprecision(2) << cgpa;

    cout << endl;
    return 0;
}
