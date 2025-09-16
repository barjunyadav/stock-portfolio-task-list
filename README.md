class StockPortfolio:
    def _init_(self):
        self.portfolio = {}

    def add_stock(self, ticker, quantity, price):
        if ticker in self.portfolio:
            self.portfolio[ticker]['quantity'] += quantity
            self.portfolio[ticker]['price'] = price
        else:
            self.portfolio[ticker] = {'quantity': quantity, 'price': price}

    def remove_stock(self, ticker, quantity):
        if ticker in self.portfolio:
            self.portfolio[ticker]['quantity'] -= quantity
            if self.portfolio[ticker]['quantity'] <= 0:
                del self.portfolio[ticker]

    def update_price(self, ticker, price):
        if ticker in self.portfolio:
            self.portfolio[ticker]['price'] = price

    def get_value(self):
        total_value = sum(info['quantity'] * info['price'] for info in self.portfolio.values())
        return total_value

    def print_portfolio(self):
        for ticker, info in self.portfolio.items():
            print(f"Ticker: {ticker}, Quantity: {info['quantity']}, Price: {info['price']}")

# Example task list
portfolio = StockPortfolio()
portfolio.add_stock('AAPL', 10, 150)
portfolio.add_stock('GOOGL', 5, 2800)
portfolio.update_price('AAPL', 155)
portfolio.remove_stock('AAPL', 3)
portfolio.print_portfolio()
print("Total portfolio value:", portfolio.get_value())
