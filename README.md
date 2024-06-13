# JAVA-individual-task-BOOK-MANAGER

# Main.java
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        BookManager bookManager = new BookManager();
        Scanner scanner = new Scanner(System.in);
        boolean exit = false;

        while (!exit) {
            System.out.println();
            System.out.println("You have opened the Book Management System. Please enter your choice (1 - 4): ");
            System.out.println("1. Add a Book");
            System.out.println("2. Remove a Book");
            System.out.println("3. Display All Books");
            System.out.println("4. Exit");
            
            int choice = scanner.nextInt();
            scanner.nextLine(); 

            if (choice == 1) {
                bookManager.addBook(scanner);
            } else if (choice == 2) {
                bookManager.removeBook(scanner);
            } else if (choice == 3) {
                bookManager.displayBooks();
            } else if (choice == 4) {
                exit = true;
                System.out.println("You have exited the Book Management System.");
            } else {
                System.out.println("Invalid choice. Please enter a number between 1 and 4.");
            }
        }

        scanner.close();
    }
}
```

# Book.java
```
public class Book {
    private String name;
    private String author;
    private int year;
    private int totalPages;

    public Book(String name, String author, int year, int totalPages) {
        this.name = name;
        this.author = author;
        this.year = year;
        this.totalPages = totalPages;
    }

    public String getName() {
        return name;
    }

    public String getAuthor() {
        return author;
    }

    public int getYear() {
        return year;
    }

    public int getTotalPages() {
        return totalPages;
    }

   
    public String toString() {
        return "- Book: " +
                " title = " + name +
                ", author = " + author +
                ", year = " + year +
                ", totalPages = " + totalPages;
    }
}
```

# BookManager.java
```
import java.util.ArrayList;
import java.util.Scanner;

public class BookManager {
    private ArrayList<Book> bookList = new ArrayList<>();

    public void addBook(Scanner scanner) {
        System.out.print("Please enter the title of the book: ");
        String name = scanner.nextLine();
        System.out.print("Please enter the author of the book: ");
        String author = scanner.nextLine();
        System.out.print("Please enter the year of publication: ");
        int year = scanner.nextInt();
        System.out.print("PLease enter the total number of pages: ");
        int totalPages = scanner.nextInt();
        scanner.nextLine(); 

        bookList.add(new Book(name, author, year, totalPages));
        System.out.println();
        System.out.println("The Book with the title '" + name + "' by " + author + " has been added to the list.");
        
    }

    public void removeBook(Scanner scanner) {
        System.out.print("Please enter the title of the book to remove: ");
        String bookName = scanner.nextLine();
        Book bookToRemove = null;
        for (Book book : bookList) {
            if (book.getName().equals(bookName)) {
                bookToRemove = book;
                break;
            }
        }
        if (bookToRemove != null) {
            bookList.remove(bookToRemove);
            System.out.println("The Book with the title '" + bookName + "' has been removed from the list.");
        } else {
            System.out.println("The Book with the title '" + bookName + "' was not found in the list.");
        }
    }

    public void displayBooks() {
        System.out.println("The List of all Books:");
        if (bookList.isEmpty()) {
            System.out.println("There are no books in the list.");
        } else {
            for (Book book : bookList) {
                System.out.println(book);
            }
        }
    }
}
```
