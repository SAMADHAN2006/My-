# My-
# ===== Library Management System =====
# Using two dictionaries:
# member_record = { "MemberName": books_borrowed }
# book_record = { "BookName": times_borrowed }

member_record = {}
book_record = {}

# -------- Function Definitions -------- #

def add_member_record():
    name = input("Enter member name: ")
    borrowed = int(input(f"Enter number of books borrowed by {name}: "))
    member_record[name] = borrowed
    print("Member record added successfully.")


def add_book_record():
    title = input("Enter book title: ")
    count = int(input(f"Enter how many times '{title}' was borrowed: "))
    book_record[title] = count
    print("Book record added successfully.")


def display_records():
    print("\n--- Member Records ---")
    if not member_record:
        print("No member records found.")
    else:
        for name, count in member_record.items():
            print(f"{name} → {count} books borrowed")

    print("\n--- Book Records ---")
    if not book_record:
        print("No book records found.")
    else:
        for title, count in book_record.items():
            print(f"{title} → borrowed {count} times")


def average_borrow():
    if not member_record:
        print("No member data found.")
        return
    avg = sum(member_record.values()) / len(member_record)
    print(f"Average number of books borrowed per member: {avg:.2f}")


def min_max_book():
    if not book_record:
        print("No book data found.")
        return
    min_book = min(book_record, key=book_record.get)
    max_book = max(book_record, key=book_record.get)
    print(f"Least borrowed book: '{min_book}' → {book_record[min_book]} times")
    print(f"Most borrowed book: '{max_book}' → {book_record[max_book]} times")


def zero_borrow_members():
    zero_list = [name for name, count in member_record.items() if count == 0]
    if zero_list:
        print("Members who borrowed 0 books:", ", ".join(zero_list))
    else:
        print("No member with zero borrow found.")


# --------- MAIN MENU --------- #

def main():
    while True:
        print("\n===== LIBRARY MENU =====")
        print("1. Add Member Record")
        print("2. Add Book Record")
        print("3. Display All Records")
        print("4. Show Average Borrow per Member")
        print("5. Show Least & Most Borrowed Book")
        print("6. Show Members with Zero Borrows")
        print("7. Exit")

        choice = int(input("Enter your choice: "))

        if choice == 1:
            add_member_record()
        elif choice == 2:
            add_book_record()
        elif choice == 3:
            display_records()
        elif choice == 4:
            average_borrow()
        elif choice == 5:
            min_max_book()
        elif choice == 6:
            zero_borrow_members()
        elif choice == 7:
            print("Exiting Program... Thank You!")
            break
        else:
            print("Invalid choice! Please try again.")


# Run Program
if __name__ == "__main__":
    main()
