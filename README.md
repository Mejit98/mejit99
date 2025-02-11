#include <iostream>
#include <string>
#include <cmath>
using namespace std;
int f(const string &n, int b) {
    int d = 0;
    int l = n.length();
    for (int i = 0; i < l; ++i) {
        char c = n[l - 1 - i];
        int v;
        if (c >= '0' && c <= '9') {
            v = c - '0';
        } else if (c >= 'A' && c <= 'F') {
            v = c - 'A' + 10;
        } else if (c >= 'a' && c <= 'f') {
            v = c - 'a' + 10;
        } else {
            cerr << "Неправильный символ в числе: " << c << endl;
            return -1; 
        }
        if (v >= b) {
            cerr << "Цифра " << c << " недопустима для системы счисления с основанием " << b << endl;
            return -1; 
        }
        d += v * pow(b, i);
    }
    return d;
}
int main() {
    string n;
    int b;
    cout << "Введите число: ";
    cin >> n;
    cout << "Введите основание системы счисления (от 2 до 16): ";
    cin >> b;
    if (b < 2 || b > 16) {
        cerr << "Ошибка: основание должно быть от 2 до 16." << endl;
        return 1; 
    }
    int d = f(n, b);
    if (d != -1) {
        cout << "Десятичное значение: " << d << endl;
    }
    return 0;
}

