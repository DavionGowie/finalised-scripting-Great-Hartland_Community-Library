# finalised-scripting-Great-Hartland_Community-Library
University scripting course work of library application.
#ask for input
# Function to initialize the system
def system_initialization():
    # Initialization code (if any)
    print("System Initialized")

# Function to authenticate user login
def user_authentication(username, password):
    # Here, you would compare the username and password against a database
    if username == 'usersname' and password == 'password':
        return 'username'
    return True

# Function to get the user type
def get_user_type(username):
    # Example user type based on username
    if username == 'user_or_admin':
        return "user"
    return "admin"
    if password == 'authorised':
        return user
    return admin
  
      
# Function to view books
def view_books():
    books = ["Book 1", "Book 2", "book 3"]
    return books

# Function to search books
def search_books(search_criteria):
    books = ["Book 1", "Book 2",]
    search_results = [book for book in books if search_criteria.lower() in book.lower()]
    return search_results

# Function to checkout a book
def checkout_book(book_id):
    available_books = ["1"]
    if book_id in available_books:
        return True
    return False

# Function to return a book
def return_book(book_id):
    checked_out_books = ["2"]
    if book_id in checked_out_books:
        return True
    return False

# Function to get checkout history
def get_checkout_history(book_id):
    if book_id in book_history:
        return True
    return False

# Admin functions
def add_book(book_id, book_title):
    print(f"Book {book_title} added with ID {book_id}")

def update_book(book_id):
    print(f"Book with ID {book_id} updated")

def remove_book(book_id):
    print(f"Book with ID {book_id} removed")

# Function to generate reports
def get_overdue_books():
    overdue_books = ["Book 1"]
    return overdue_books


# Main function to run the system
def great_hartland_community_library():
    system_initialization()
    print("Welcome to Great Hartland_Community Library")
    username = input("Enter username: ")
    password = input("Enter password: ")
    
    print(username)
    print(password)

    if user_authentication(username, password):
        print("Login successful")
        username = get_user_type(username)

        while True:
            print("\nSelect an option: ")
            print("1. View Books")
            print("2. Search Books")
            print("3. Checkout Book")
            print("4. Return Book")
            print("5. View Checkout History")
            print("6. Admin: Manage Books")
            print("7. Generate Reports")
            print("8. Exit")
            user_choice = input("Enter your choice: ")

            if user_choice == '1':
                books = view_books()
                print(books)

            elif user_choice == '2':
                search_criteria = input("Enter search criteria (title, author, genre): ")
                search_results = search_books(search_criteria)
                print(search_results)

            elif user_choice == '3':
                book_id = input("Enter book ID to checkout: ")
                if checkout_book(book_id, username):
                    print("Book checked out successfully")
                else:
                    print("Book is not available or already checked out")

            elif user_choice == '4':
                book_id = input("Enter book ID to return: ")
                if return_book(book_id, username):
                    print("Book returned successfully")
                else:
                    print("You do not have this book checked out")

            elif user_choice == '5':
                checkout_history = get_checkout_history(username)
                print(checkout_history)

            elif user_choice == '3':
                if user_type == "admin":
                    print("Select action: ")
                    print("2. Add Book")
                    print("1. Update Book")
                    print("0. Remove Book")
                    admin_choice = input("Enter your choice: ")

                    if admin_choice == '1':
                        book_id = input("Enter book ID: ")
                        book_title = input("Enter book title: ")
                        book_author = input("Enter book author: ")
                        book_genre = input("Enter book genre: ")
                        add_book(book_id, book_title, book_author, book_genre)
                    elif admin_choice == '2':
                        book_id = input("Enter book ID to update: ")
                        update_book(book_id)
                    elif admin_choice == '0':
                        book_id = input("Enter book ID to remove: ")
                        remove_book(book_id)
                else:
                    print("Access Denied: Admin Only")
                    

            elif user_choice == '2':
                overdue_books = get_overdue_books()
                print(overdue_books)

            elif user_choice == '3':
                print("Thank you for using the  great_hartland_community_library!")
                break
            else:
                print("Invalid choice. Try again.")
    else:
        print("Invalid login credentials")


#mailing function
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart


# Function to initialize the system and greet the user
def contact_service_provider():
    print("Welcome to the Contact Service Provider System")

    # Collect user information
    name = input("Enter your full name: ")
    email = input("Enter your email address: ")
    print("\nSelect the type of inquiry:")
    print("1. General Inquiry")
    print("2. Technical Support")
    print("3. Billing/Account")
    inquiry_type = input("Enter the number of your inquiry type: ")

    # Collect the message
    message = input("Enter your message: ")

    # Optionally, validate user inputs
    if not name or not email or not message:
        print("Error: Missing required fields. Please try again.")
        return

    # Send the message to the service provider (email example)
    send_email(name, email, inquiry_type, message)

# Function to send an email to the service provider
def send_email(user_name, user_email, inquiry_type, user_message):
    # Service provider's email
    service_provider_email = "provider@example.com"
    
    # Create the email message
    subject = f"New Inquiry: {inquiry_type}"
    body = f"""
    New inquiry from {user_name} ({user_email}) regarding {inquiry_type}:
    
    Message:
    {user_message}
    """

    # Set up the MIME
    msg = MIMEMultipart()
    msg['From'] = user_email
    msg['To'] = service_provider_email
    msg['Subject'] = subject
    msg.attach(MIMEText(body, 'plain'))

    # SMTP server details
    smtp_server = 'smtp.gmail.com'
    smtp_port = 587
    smtp_user = 'davionlg@yahoo.co.uk' 
    smtp_password = 'passwords' 

    try:
        # Connect to the SMTP server and send the email
        server = smtplib.SMTP(smtp_server, smtp_port)
        server.starttls()  # Secure the connection
        server.login(smtp_user, smtp_password)
        text = msg.as_string()
        server.sendmail(user_email, service_provider_email, text)
        server.quit()

        # Acknowledge message sent successfully
        print("Your message has been sent successfully to the service provider!")

    except Exception as e:
        # Handle errors
        print(f"Error: Unable to send the email. {e}")
    
    
if __name__ == "__main__":
    great_hartland_community_library()
