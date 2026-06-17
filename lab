#include <iostream>
#include <fstream>
#include <string>
#include <cstdlib>

using namespace std;

class User
{
public:
    virtual void displayRole()
    {
        cout << "\nLibrary User\n";
    }
    virtual ~User() {}
};

class Student : public User
{
public:
    void displayRole()
    {
        cout << "\nStudent User\n";
    }
};

class Book
{
public:
    int id;
    string title, author, status;

    Book()
    {
        id = 0;
        status = "Available";
    }
};

class Library
{
public:
    void addBook()
    {
        Book b;

        cout << "Enter Book ID: ";
        cin >> b.id;
        cin.ignore();

        cout << "Enter Title: ";
        getline(cin, b.title);

        cout << "Enter Author: ";
        getline(cin, b.author);

        ofstream file("books.txt", ios::app);
        file << b.id << "|" << b.title << "|" << b.author << "|Available\n";
        file.close();

        cout << "Book Added Successfully!\n";
    }

    void viewBooks()
    {
        ifstream file("books.txt");
        string line;

        cout << "\n===== BOOKS =====\n";
        while (getline(file, line))
            cout << line << endl;

        file.close();
    }

    void deleteBook()
    {
        int deleteID;
        string line;

        cout << "Enter Book ID To Delete: ";
        cin >> deleteID;

        ifstream file("books.txt");
        ofstream temp("temp.txt");

        while (getline(file, line))
        {
            string idStr = line.substr(0, line.find("|"));

            if (atoi(idStr.c_str()) != deleteID)
                temp << line << endl;
        }

        file.close();
        temp.close();

        remove("books.txt");
        rename("temp.txt", "books.txt");

        cout << "Book Deleted Successfully!\n";
    }
};

int main()
{
    Library lib;
    User *u = new Student();

    int choice;

    do
    {
        cout << "\n===== LIBRARY MANAGEMENT SYSTEM =====\n";
        cout << "1. Add Book\n";
        cout << "2. View Books\n";
        cout << "3. Delete Book\n";
        cout << "4. Show User\n";
        cout << "5. Exit\n";
        cout << "Enter Choice: ";
        cin >> choice;

        switch(choice)
        {
            case 1: lib.addBook(); break;
            case 2: lib.viewBooks(); break;
            case 3: lib.deleteBook(); break;
            case 4: u->displayRole(); break;
            case 5: cout << "Good Bye!\n"; break;
            default: cout << "Invalid Choice!\n";
        }

    } while(choice != 5);

    delete u;
    return 0;
}
