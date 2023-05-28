# greenfield-cmd-python

import requests

def get_bnb_price():
    response = requests.get('https://api.binance.com/api/v3/ticker/price?symbol=BNBUSDT')
    data = response.json()
    if 'price' in data:
        return float(data['price'])
    return None

def get_account_balance(api_key, api_secret):
    headers = {
        'X-MBX-APIKEY': api_key
    }
    response = requests.get('https://api.binance.com/api/v3/account', headers=headers, params={'timestamp': int(time.time() * 1000)})
    data = response.json()
    if 'balances' in data:
        balances = {balance['asset']: float(balance['free']) for balance in data['balances'] if float(balance['free']) > 0}
        return balances
    return None

def main():
    api_key = input("Введите ваш API-ключ Binance: ")
    api_secret = input("Введите ваш API-секрет Binance: ")
    
    while True:
        command = input("Введите команду ('price' для получения цены BNB, 'balance' для получения баланса аккаунта, 'exit' для выхода): ")
        if command == 'price':
            price = get_bnb_price()
            if price is not None:
                print(f"Цена BNB: ${price}")
            else:
                print("Не удалось получить цену BNB.")
        elif command == 'balance':
            balances = get_account_balance(api_key, api_secret)
            if balances is not None:
                print("Баланс аккаунта:")
                for asset, balance in balances.items():
                    print(f"{asset}: {balance}")
            else:
                print("Не удалось получить баланс аккаунта.")
        elif command == 'exit':
            break
        else:
            print("Неверная команда. Попробуйте еще раз.")

if __name__ == "__main__":
    main()

Ниже представлены возможные сценарии использования данного кода:

Получение цены BNB:

Пользователь запускает скрипт.
Скрипт запрашивает у пользователя ввод их API-ключа и API-секрета Binance.
Пользователь вводит API-ключ и API-секрет.
Скрипт отображает приглашение для ввода команды.
Пользователь вводит "price" в качестве команды.
Скрипт отправляет запрос к Binance API для получения цены BNB.
Скрипт выводит полученную цену BNB.
Получение баланса аккаунта:

Пользователь запускает скрипт.
Скрипт запрашивает у пользователя ввод их API-ключа и API-секрета Binance.
Пользователь вводит API-ключ и API-секрет.
Скрипт отображает приглашение для ввода команды.
Пользователь вводит "balance" в качестве команды.
Скрипт отправляет запрос к Binance API для получения баланса аккаунта.
Скрипт выводит полученный баланс для каждого актива.
Выход из скрипта:

Пользователь запускает скрипт.
Скрипт запрашивает у пользователя ввод их API-ключа и API-секрета Binance.
Пользователь вводит API-ключ и API-секрет.
Скрипт отображает приглашение для ввода команды.
Пользователь вводит "exit" в качестве команды.
Скрипт завершается, и выполнение программы заканчивается.
Обработка некорректных команд:

Пользователь запускает скрипт.
Скрипт запрашивает у пользователя ввод их API-ключа и API-секрета Binance.
Пользователь вводит API-ключ и API-секрет.
Скрипт отображает приглашение для ввода команды.
Пользователь вводит некорректную команду.
Скрипт выводит сообщение об ошибке и предлагает пользователю повторить попытку.
Невозможность получить цену BNB или баланс аккаунта:

Пользователь запускает скрипт.
Скрипт запрашивает у пользователя ввод их API-ключа и API-секрета Binance.
Пользователь вводит API-ключ и API-секрет.
Скрипт отображает приглашение для ввода команды.
Пользователь
