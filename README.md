#include <iostream>
#include <vector>
#include <string>

class Student {
public:
    Student(std::string name) : name(name) {}

    void addGrade(int grade) {
        grades.push_back(grade);
    }

    bool isExcellentStudent() const {
        return calculateAverageGrade() >= 4.5;
    }

    const std::string& getName() const {
        return name;
    }

private:
    double calculateAverageGrade() const {
        if (grades.empty()) {
            return 0.0;
        }

        double sum = 0.0;
        for (int grade : grades) {
            sum += grade;
        }

        return sum / grades.size();
    }

private:
    std::string name;
    std::vector<int> grades;
};


int main() {
    setlocale(LC_ALL, "Russian");

    Student student1("Иванов");
    Student student2("Петров");

    student1.addGrade(5);
    student2.addGrade(4);

    std::cout << student1.getName() << " отличник: " << (student1.isExcellentStudent() ? "Да" : "Нет") << std::endl;
    std::cout << student2.getName() << " отличник: " << (student2.isExcellentStudent() ? "Да" : "Нет") << std::endl;

    return 0;
}
