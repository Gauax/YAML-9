import unittest
from book_manager import Book, BookManager

class TestBookManager(unittest.TestCase):
    def setUp(self):
        self.manager = BookManager()
        self.book1 = Book('123', 'Test Book One', 'Author One')
        self.book2 = Book('456', 'Test Book Two', 'Author Two')
        self.book_duplicate_isbn = Book('123', 'Duplicate ISBN', 'Author One')

    def test_add_book(self):
        self.manager.add_book(self.book1)
        self.assertIn(self.book1, self.manager.list_books(), "Book should be added to the list")

    def test_prevent_duplicate_book_addition(self):
        self.manager.add_book(self.book1)
        self.manager.add_book(self.book_duplicate_isbn)  # This has the same ISBN as book1
        self.assertEqual(len(self.manager.list_books()), 1, "Duplicate ISBN should not be added")

    def test_remove_book(self):
        self.manager.add_book(self.book1)
        self.manager.add_book(self.book2)
        self.manager.remove_book('123')
        self.assertNotIn(self.book1, self.manager.list_books(), "Book should be removed from the list")
        self.assertIn(self.book2, self.manager.list_books(), "Other books should remain in the list")

    def test_list_books(self):
        self.manager.add_book(self.book1)
        self.manager.add_book(self.book2)
        self.assertEqual(self.manager.list_books(), [self.book1, self.book2], "List of books should match the added books")

if __name__ == '__main__':
    unittest.main()
