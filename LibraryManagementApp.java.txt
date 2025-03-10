import java.util.Scanner;

public class LibraryManagementApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Library library = new Library();

        // Add some books to the library
        library.addBook(new Book(1, "Java Basics", "John Doe"));
        library.addBook(new Book(2, "Advanced Java", "Jane Smith"));

        while (true) {
            System.out.println("\nLibrary Management System");
            System.out.println("1. Add Book");
            System.out.println("2. Display Books");
            System.out.println("3. Search Book by Title");
            System.out.println("4. Register User");
            System.out.println("5. Borrow Book");
            System.out.println("6. Exit");
            System.out.print("Choose an option: ");
            
            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline character

            switch (choice) {
                case 1:
                    // Add Book
                    System.out.print("Enter book ID: ");
                    int id = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter book title: ");
                    String title = scanner.nextLine();
                    System.out.print("Enter author name: ");
                    String author = scanner.nextLine();
                    library.addBook(new Book(id, title, author));
                    System.out.println("Book added successfully!");
                    break;

                case 2:
                    // Display Books
                    library.displayBooks();
                    break;

                case 3:
                    // Search Book by Title
                    System.out.print("Enter book title to search: ");
                    String searchTitle = scanner.nextLine();
                    library.searchBookByTitle(searchTitle);
                    break;

                case 4:
                    // Register User
                    System.out.print("Enter user ID: ");
                    int userId = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter user name: ");
                    String userName = scanner.nextLine();
                    library.addUser(new User(userId, userName));
                    System.out.println("User registered successfully!");
                    break;

                case 5:
                    // Borrow Book
                    System.out.print("Enter user ID: ");
                    int borrowUserId = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter book title to borrow: ");
                    String borrowBookTitle = scanner.nextLine();
                    library.borrowBook(borrowUserId, borrowBookTitle);
                    break;

                case 6:
                    // Exit
                    System.out.println("Exiting system...");
                    scanner.close();
                    System.exit(0);
                    break;

                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }
}
