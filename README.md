# Codealpha_CGPA_calculator
#include <iostream>
#include<conio.h>
#include<string>
#include <vector>
#include <iomanip>

using namespace std;

struct Course {
    string courseName;
    double grade;
    int credits;
};

double calculateGPA(const vector<Course>& courses) {
    double totalGradePoints = 0;
    int totalCredits = 0;

    for (const auto& course : courses) {
        totalGradePoints += course.grade * course.credits;
        totalCredits += course.credits;
    }

    return (totalCredits != 0) ? (totalGradePoints / totalCredits) : 0;
}

int main() {
    int numberOfCourses;
    cout << "Enter the number of courses: ";
    cin >> numberOfCourses;

    vector<Course> courses(numberOfCourses);

    for (int i = 0; i < numberOfCourses; ++i) {
        cout << "Enter details for course " << i + 1 << ":\n";

        cout << "Course name: ";
        cin.ignore(); // To ignore the newline character left by previous input
        getline(cin, courses[i].courseName);

        cout << "Grade (on a scale of 4.0): ";
        cin >> courses[i].grade;

        cout << "Credits: ";
        cin >> courses[i].credits;
    }

    cout << "\nCourse details:\n";
    double totalGradePoints = 0;
    int totalCredits = 0;

    for (const auto& course : courses) {
        cout << "Course: " << course.courseName << ", Grade: " << course.grade << ", Credits: " << course.credits << "\n";
        totalGradePoints += course.grade * course.credits;
        totalCredits += course.credits;
    }

    double gpa = calculateGPA(courses);

    cout << "\nTotal Credits: " << totalCredits << "\n";
    cout << "Total Grade Points: " << totalGradePoints << "\n";
    cout << "GPA for the semester: " << fixed << setprecision(2) << gpa << "\n";

    // Assuming we have previous semesters' GPAs and credits to calculate CGPA
    int totalCreditsAllSemesters = totalCredits; // For example, this should be cumulative
    double totalGradePointsAllSemesters = totalGradePoints; // For example, this should be cumulative

    // For the sake of example, assume this semester is the only one, thus CGPA equals GPA
    double cgpa = (totalCreditsAllSemesters != 0) ? (totalGradePointsAllSemesters / totalCreditsAllSemesters) : 0;

    cout << "Cumulative GPA (CGPA): " << fixed << setprecision(2) << cgpa << "\n";

    return 0;
}
