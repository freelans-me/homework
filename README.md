я зробив "банківськойи системи", де є клас "Клієнт" та клас "Рахунок", які пов'язані між собою.
Клас "Клієнт" буде містити такі поля, як ім'я, прізвище, номер телефону та електронну пошту. Він також матиме метод для створення нового рахунку та метод для переведення коштів на інший рахунок.


class Client:
    def __init__(self, first_name, last_name, phone_number, email):
        self.first_name = first_name
        self.last_name = last_name
        self.phone_number = phone_number
        self.email = email
        self.accounts = []

    def create_account(self):
        account = Account(self)
        self.accounts.append(account)
        return account

    def transfer_funds(self, from_account, to_account, amount):
        if from_account.balance >= amount:
            from_account.withdraw(amount)
            to_account.deposit(amount)
            return True
        else:
            return False
class Account:
    def __init__(self, client):
        self.client = client
        self.number = generate_account_number()
        self.balance = 0

    def deposit(self, amount):
        self.balance += amount

    def withdraw(self, amount):
        self.balance -= amount

    def __str__(self):
        return f"Account number: {self.number}\nBalance: {self.balance}"
