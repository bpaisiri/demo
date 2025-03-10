import java.util.ArrayList;
import java.util.List;

public class Library {
    private List<Book> books;
    private List<User> users;

    public Library() {
        books = new ArrayList<>();
        users = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
    }

    public void addUser(User user) {
        users.add(user);
    }

    public void displayBooks() {
        if (books.isEmpty()) {
            System.out.println("No books in the library.");
        } else {
            for (Book book : books) {
                System.out.println(book);
            }
        }
    }

    public void searchBookByTitle(String title) {
        boolean found = false;
        for (Book book : books) {
            if (book.getTitle().equalsIgnoreCase(title)) {
                System.out.println("Found: " + book);
                found = true;
                break;
            }
        }
        if (!found) {
            System.out.println("Book not found.");
        }
    }

    public void borrowBook(int userId, String bookTitle) {
        boolean bookFound = false;
        boolean bookBorrowed = false;
        for (Book book : books) {
            if (book.getTitle().equalsIgnoreCase(bookTitle)) {
                bookFound = true;
                // Assuming the book is borrowed if it exists
                System.out.println("User " + userId + " has borrowed the book: " + book);
                bookBorrowed = true;
                break;
            }
        }
        if (!bookFound) {
            System.out.println("Book not found.");
        } else if (!bookBorrowed) {
            System.out.println("This book is already borrowed.");
        }
    }
}
