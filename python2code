import yfinance as yf
#--------------------
portfolio = {}
def getstockcurrentPrice(symbol):
    try:
        ticker_symbol= yf.Ticker(symbol)
        history_ticker = ticker_symbol.history("max")
        return round(history_ticker.tail()["Close"].iloc[-1],4)
    except Exception:
        print(f"This symbol {symbol} is not founded!")
        return "NONE"
#---------------------------------------------------------------------
def Validation(symbol):
    try:
        ticker_symbol= yf.Ticker(symbol)
        history_ticker = ticker_symbol.history("max")
        if history_ticker.empty:
            return False
        return True
    except Exception:
        return False
#--------------------------------------------------------------------
def addstock(symbol,shares,price):
    try:
        if Validation(symbol) is True:
            if symbol in portfolio:
                print(f"This stock {symbol} is already founded")
            else:
                portfolio[symbol] = [shares,price] # I add the share and the price as a list to the dict
                print(f"{symbol} added successfully!")
        else:
            print(f"This symbol {symbol} is not founded!")
    except Exception:
        print("There is an Error!")
#--------------------------------------------------------------------
def removeStock(symbol):
    if Validation(symbol) is True and symbol in portfolio:
        del portfolio[symbol]
        print(f"{symbol} removed successfully!")
    else:
        print(f"This symbol {symbol} is not founded!")
#--------------------------------------------------------------------
def portfoliocalculations():
    totalValueOfStocks = 0
    totalPaidValue = 0
    for key,value in portfolio.items():
        currentPrice = getstockcurrentPrice(key)*int(value[0])
        paidValue = int(value[0]) * int(value[1])
        totalValueOfStocks+=currentPrice
        totalPaidValue+=paidValue
        print(f"Symbol: {key}, Real Price for {value[0]} = {round(currentPrice,2)}, Paid Price = {paidValue}")
    print(f"The total Value of Stocks = {totalValueOfStocks}\nThe total Paid Value = {totalPaidValue}\nGain/Loss = {round(totalValueOfStocks-totalPaidValue,2)}")
#Main function---------------------------------------------------------------------------------------------
print("Hello!\n(1) to Add Stock\n(2) to Remove Stock\n(3) to View Portfolio\n(4) to Exit")
choice = input("Choose a number from 1 to 4: ")
while choice !="4":
    if choice == "1":
        symbol = input("Enter a symbol to add: ").upper()
        shares = input("Enter the shares: ")
        price = input("Enter the price for each share: ")
        addstock(symbol,shares,price)
    elif choice == "2":
        symbol = input("Please enter a symbol to remove: ")
        removeStock(symbol)
    elif choice == "3":
        portfoliocalculations()
    print("(1) to Add Stock\n(2) to Remove Stock\n(3) to View Portfolio\n(4) to Exit")
    choice = input("Choose a number from 1 to 4: ")
if choice == '4':
    print("Exit!")
#THE END----------------------------------------------------------------------------------------------------
    
