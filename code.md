```cpp
#include <iostream>
#include <iomanip>
#include <string>

using namespace std;

int main() {
    int choice;

    while(true) {
        cout << "\n========================================" << endl;
        cout << "      CGPA & SGPA CALCULATOR" << endl;
        cout << "========================================" << endl;
        cout << "  [1] Calculate SGPA (Single Semester)" << endl;
        cout << "  [2] Calculate CGPA (Multiple Semesters)" << endl;
        cout << "  [3] View Grade Scale" << endl;
        cout << "  [4] Exit" << endl;
        cout << "========================================" << endl;
        cout << "Enter choice (1-4): ";
        cin >> choice;

        if(cin.fail()) {
            cin.clear();
            cin.ignore(1000, '\n');
            cout << "\nInvalid! Type 1, 2, 3, or 4.\n";
            continue;
        }

        // ========== SGPA CALCULATOR ==========
        if(choice == 1) {
            int numSubjects;
            double semPoints = 0.0;
            int semCredits = 0;

            cout << "\n========================================" << endl;
            cout << "         SGPA CALCULATION" << endl;
            cout << "========================================" << endl;
            cout << "\nHow many subjects in this semester? ";
            cin >> numSubjects;

            if(cin.fail() || numSubjects <= 0) {
                cin.clear();
                cin.ignore(1000, '\n');
                cout << "\nInvalid! Must be a positive number.\n";
                continue;
            }

            for(int i = 1; i <= numSubjects; i++) {
                string name;
                char grade;
                int credits;
                double points;

                cout << "\n--- Subject " << i << " of " << numSubjects << " ---" << endl;

                cout << "Subject name (one word): ";
                cin >> name;

                cout << "Grade (A/B/C/D/F): ";
                cin >> grade;
                grade = (char)toupper((unsigned char)grade);
                while(grade != 'A' && grade != 'B' && grade != 'C' && grade != 'D' && grade != 'F') {
                    cout << "Invalid! Type A/B/C/D/F: ";
                    cin >> grade;
                    grade = (char)toupper((unsigned char)grade);
                }

                if(grade == 'A') points = 4.0;
                else if(grade == 'B') points = 3.0;
                else if(grade == 'C') points = 2.0;
                else if(grade == 'D') points = 1.0;
                else points = 0.0;

                cout << "Credit hours: ";
                cin >> credits;
                while(cin.fail() || credits <= 0) {
                    cin.clear();
                    cin.ignore(1000, '\n');
                    cout << "Invalid! Must be positive: ";
                    cin >> credits;
                }

                semPoints += points * credits;
                semCredits += credits;

                cout << "  -> " << name << " | Grade: " << grade << " | Credits: " << credits << " | Points: " << points * credits << endl;
            }

            double sgpa = (semCredits == 0) ? 0.0 : semPoints / semCredits;

            cout << "\n========================================" << endl;
            cout << "         SGPA RESULT" << endl;
            cout << "========================================" << endl;
            cout << "Total Credits: " << semCredits << endl;
            cout << "SGPA:          " << fixed << setprecision(2) << sgpa << endl;

            cout << "\nAcademic Standing: ";
            if(sgpa >= 3.7) cout << "Outstanding (First Class with Distinction)";
            else if(sgpa >= 3.5) cout << "Excellent (First Class)";
            else if(sgpa >= 3.3) cout << "Very Good (Second Class Upper)";
            else if(sgpa >= 3.0) cout << "Good (Second Class Lower)";
            else if(sgpa >= 2.5) cout << "Above Average (Third Class)";
            else if(sgpa >= 2.0) cout << "Average (Pass)";
            else if(sgpa >= 1.0) cout << "Below Average (Conditional Pass)";
            else cout << "Poor (Fail)";
            cout << endl;
            cout << "========================================" << endl;
        }

        // ========== CGPA CALCULATOR ==========
        else if(choice == 2) {
            int numSemesters;

            cout << "\n========================================" << endl;
            cout << "         CGPA CALCULATION" << endl;
            cout << "========================================" << endl;
            cout << "\nHow many semesters? ";
            cin >> numSemesters;

            if(cin.fail() || numSemesters <= 0) {
                cin.clear();
                cin.ignore(1000, '\n');
                cout << "\nInvalid! Must be a positive number.\n";
                continue;
            }

            double totalWeightedGPA = 0.0;
            int totalCreditsAll = 0;

            for(int sem = 1; sem <= numSemesters; sem++) {
                int numSubjects;
                cout << "\n--- Semester " << sem << " of " << numSemesters << " ---" << endl;
                cout << "How many subjects? ";
                cin >> numSubjects;

                if(cin.fail() || numSubjects <= 0) {
                    cin.clear();
                    cin.ignore(1000, '\n');
                    cout << "\nInvalid! Skipping semester.\n";
                    continue;
                }

                double semPoints = 0.0;
                int semCredits = 0;

                for(int i = 1; i <= numSubjects; i++) {
                    string name;
                    char grade;
                    int credits;
                    double points;

                    cout << "\nSubject " << i << " of " << numSubjects << endl;

                    cout << "Name (one word): ";
                    cin >> name;

                    cout << "Grade (A/B/C/D/F): ";
                    cin >> grade;
                    grade = (char)toupper((unsigned char)grade);
                    while(grade != 'A' && grade != 'B' && grade != 'C' && grade != 'D' && grade != 'F') {
                        cout << "Invalid! Type A/B/C/D/F: ";
                        cin >> grade;
                        grade = (char)toupper((unsigned char)grade);
                    }

                    if(grade == 'A') points = 4.0;
                    else if(grade == 'B') points = 3.0;
                    else if(grade == 'C') points = 2.0;
                    else if(grade == 'D') points = 1.0;
                    else points = 0.0;

                    cout << "Credit hours: ";
                    cin >> credits;
                    while(cin.fail() || credits <= 0) {
                        cin.clear();
                        cin.ignore(1000, '\n');
                        cout << "Invalid! Must be positive: ";
                        cin >> credits;
                    }

                    semPoints += points * credits;
                    semCredits += credits;
                }

                double semGPA = (semCredits == 0) ? 0.0 : semPoints / semCredits;

                cout << "\nSemester " << sem << " GPA: " << fixed << setprecision(2) << semGPA << endl;
                cout << "Credits: " << semCredits << endl;

                totalWeightedGPA += semGPA * semCredits;
                totalCreditsAll += semCredits;
            }

            double cgpa = (totalCreditsAll == 0) ? 0.0 : totalWeightedGPA / totalCreditsAll;

            cout << "\n========================================" << endl;
            cout << "         FINAL CGPA RESULT" << endl;
            cout << "========================================" << endl;
            cout << "Total Credits: " << totalCreditsAll << endl;
            cout << "Overall CGPA:  " << fixed << setprecision(2) << cgpa << endl;

            cout << "\nAcademic Standing: ";
            if(cgpa >= 3.7) cout << "Outstanding (First Class with Distinction)";
            else if(cgpa >= 3.5) cout << "Excellent (First Class)";
            else if(cgpa >= 3.3) cout << "Very Good (Second Class Upper)";
            else if(cgpa >= 3.0) cout << "Good (Second Class Lower)";
            else if(cgpa >= 2.5) cout << "Above Average (Third Class)";
            else if(cgpa >= 2.0) cout << "Average (Pass)";
            else if(cgpa >= 1.0) cout << "Below Average (Conditional Pass)";
            else cout << "Poor (Fail)";
            cout << endl;
            cout << "========================================" << endl;
        }

        else if(choice == 3) {
            cout << "\n========================================" << endl;
            cout << "         GRADE SCALE" << endl;
            cout << "========================================" << endl;
            cout << "  A = 4.0 points (Outstanding)" << endl;
            cout << "  B = 3.0 points (Good)" << endl;
            cout << "  C = 2.0 points (Average)" << endl;
            cout << "  D = 1.0 point  (Below Average)" << endl;
            cout << "  F = 0.0 points (Fail)" << endl;
            cout << "========================================" << endl;
        }
        else if(choice == 4) {
            cout << "\nGoodbye!" << endl;
            break;
        }
        else {
            cout << "\nInvalid! Type 1, 2, 3, or 4.\n";
        }
    }

    return 0;
}
```
