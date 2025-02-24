# -1-
# содержит решение ОАП
class RegistrationRem:
    def __init__(self):
        self.window = Toplevel()
        self.window.title("Регистрация на ремонт")
        self.window.geometry("400x400")
        self.create_widgets()

    def create_widgets(self):
        ttk.Label(self.window, text="Имя:").pack(pady=5)
        self.entry_name = Entry(self.window)
        self.entry_name.pack(pady=5)

        ttk.Label(self.window, text="Телефон:").pack(pady=5)
        self.entry_phone = Entry(self.window)
        self.entry_phone.pack(pady=5)

        ttk.Label(self.window, text="Комментарий:").pack(pady=5)
        self.entry_comment = Text(self.window, height=5, width=30)
        self.entry_comment.pack(pady=5)

        # Отображение цены
        self.base_price = 2000  # Базовая цена
        self.expenses_label = ttk.Label(self.window, text=f"Цена: {self.base_price} руб. + расходы на комплектующие")
        self.expenses_label.pack(pady=10)

        self.submit_button = ttk.Button(self.window, text="Подтвердить", command=self.submit)
        self.submit_button.pack(pady=20)

    def submit(self):
        name = self.entry_name.get()
        phone = self.entry_phone.get()
        comment = self.entry_comment.get("1.0", END).strip()


        additional_expenses = 0
        total_price = self.base_price + additional_expenses

        print(f"Имя: {name}, Телефон: {phone}, Комментарий: {comment}")
        CheckRegistration(name, phone, comment, total_price)  # Передаем общую цену
        self.open_check_window(name, phone, comment, total_price)
        self.window.destroy()

    def open_check_window(self, name, phone, comment, price):
        CheckWindow(name, phone, comment, price)
