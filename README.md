package ThisState;
import java.util.Scanner; 
	import java.util.ArrayList;


	public class LibrarySystem {
	    
	    public static class Book {
	        private String title;
	        private String author;
	        private String code;

	        public Book(String title, String author, String code) {
	            this.title = title;
	            this.author = author;
	            this.code = code;
	        }

	        public String title() {
	            return title;
	        }

	        public String author() {
	            return author;
	        }

	        public String code() {
	            return code;
	        }

	        public String toString() {
	            return "Title:" + title +" "+", Author:" + author+" "+", Code:" + code;
	        }
	    }

	    public static class Library {
	        private ArrayList<Book> books;

	        public Library() {
	            books = new ArrayList<>();
	        }

	        public void addBook(Book book) {
	            books.add(book);
	        }

	        public void displayAllBooks() {
	            if (books.isEmpty()) {
	                System.out.println("No books in the library.");
	            } else {
	                for (Book book : books) {
	                    System.out.println(book);
	                }
	            }
	        }

	        public Book searchBycode(String code) {
	            for (Book book : books) {
	                if (book.code().equals(code)) {
	                    return book;
	                }
	            }
	            return null;
	        }
	    }

	    public static void main(String[] args) {
	        Library library = new Library();
	        Scanner scanner = new Scanner(System.in);
	        int choice;

	        do {
	            System.out.println("\nLibrary Menu:");
	            System.out.println("1. Add a book");
	            System.out.println("2. Display all books");
	            System.out.println("3. Search for a book by its Code");
	            System.out.println("4. Exit");
	            System.out.print("Enter your choice: ");
	            choice = scanner.nextInt();
	            scanner.nextLine();  

	            switch (choice) {
	                case 1:
	                    System.out.print("Enter title: ");
	                    String title = scanner.nextLine();
	                    System.out.print("Enter author: ");
	                    String author = scanner.nextLine();
	                    System.out.print("Enter code: ");
	                    String code = scanner.nextLine();
	                    Book book = new Book(title, author, code);
	                    library.addBook(book);
	                    System.out.println("Book added successfully!");
	                    break;
	                case 2:
	                    library.displayAllBooks();
	                    break;
	                case 3:
	                    System.out.print("Enter code to search: ");
	                    String searchCode = scanner.nextLine();
	                    Book foundBook = library.searchBycode(searchCode);
	                    if (foundBook != null) {
	                        System.out.println("Book found: " + foundBook);
	                    } else {
	                        System.out.println("Book not found.");
	                    }
	                    break;
	                case 4:
	                    System.out.println("Exiting the program.");
	                    break;
	                default:
	                    System.out.println("Invalid choice. Please try again.");
	            }
	        } while (choice != 4);

	        scanner.close();
	    }
	}
