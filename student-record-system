#include <iostream>
#include <string>
#include <cstdlib>   // for atoi
using namespace std;

const int MAX = 30;
const int COLS = 3;

// Function Prototypes
void showMenu();
int readChoice();
void addStudent(string students[][COLS], int& count, int maxSize);
void printStudents(const string students[][COLS], int count);
void bubbleSortById(string students[][COLS], int count);
int binarySearchById(const string students[][COLS], int count, int targetId);

int main() {
    string students[MAX][COLS];
    int count = 0;
    bool isSorted = false;
    int choice;

    do {
        showMenu();
        choice = readChoice();

        switch (choice) {
            case 1:
                addStudent(students, count, MAX);
                isSorted = false;
                break;

            case 2:
                printStudents(students, count);
                break;

            case 3:
                bubbleSortById(students, count);
                isSorted = true;
                cout << "Students sorted by ID.\n";
                break;

            case 4:
                if (!isSorted) {
                    cout << "Please sort by ID before using binary search.\n";
                } else {
                    int id;
                    cout << "Enter ID to search: ";
                    cin >> id;

                    int index = binarySearchById(students, count, id);
                    if (index == -1) {
                        cout << "Student not found.\n";
                    } else {
                        cout << "Student Found:\n";
                        cout << "ID: " << students[index][0] << endl;
                        cout << "Name: " << students[index][1] << endl;
                        cout << "GPA: " << students[index][2] << endl;
                    }
                }
                break;

            case 5:
                cout << "Exiting program...\n";
                break;

            default:
                cout << "Invalid choice.\n";
        }

    } while (choice != 5);

    return 0;
}

// ================= FUNCTIONS =================

void showMenu() {
    cout << "\n===== Student ID Search System =====\n";
    cout << "1. Add Student\n";
    cout << "2. Display All Students\n";
    cout << "3. Sort by ID (Bubble Sort)\n";
    cout << "4. Search by ID (Binary Search)\n";
    cout << "5. Exit\n";
}

int readChoice() {
    int choice;
    cout << "Enter your choice: ";
    cin >> choice;
    return choice;
}

void addStudent(string students[][COLS], int& count, int maxSize) {
    if (count >= maxSize) {
        cout << "Maximum number of students reached.\n";
        return;
    }

    string id, name, gpa;

    cout << "Enter Student ID: ";
    cin >> id;

    // Check duplicate ID
    for (int i = 0; i < count; i++) {
        if (students[i][0] == id) {
            cout << "Duplicate ID not allowed.\n";
            return;
        }
    }

    cin.ignore();
    cout << "Enter Student Name: ";
    getline(cin, name);

    cout << "Enter GPA: ";
    cin >> gpa;

    students[count][0] = id;
    students[count][1] = name;
    students[count][2] = gpa;

    count++;
    cout << "Student added successfully.\n";
}

void printStudents(const string students[][COLS], int count) {
    if (count == 0) {
        cout << "No students to display.\n";
        return;
    }

    cout << "\nID\tName\tGPA\n";
    for (int i = 0; i < count; i++) {
        cout << students[i][0] << "\t"
             << students[i][1] << "\t"
             << students[i][2] << endl;
    }
}

void bubbleSortById(string students[][COLS], int count) {
    for (int i = 0; i < count - 1; i++) {
        for (int j = 0; j < count - i - 1; j++) {
            int id1 = atoi(students[j][0].c_str());
            int id2 = atoi(students[j + 1][0].c_str());

            if (id1 > id2) {
                for (int k = 0; k < COLS; k++) {
                    swap(students[j][k], students[j + 1][k]);
                }
            }
        }
    }
}

int binarySearchById(const string students[][COLS], int count, int targetId) {
    int left = 0, right = count - 1;

    while (left <= right) {
        int mid = (left + right) / 2;
        int midId = atoi(students[mid][0].c_str());

        if (midId == targetId)
            return mid;
        else if (midId < targetId)
            left = mid + 1;
        else
            right = mid - 1;
    }

    return -1;
}
