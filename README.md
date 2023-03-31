'''
#include <iostream> 
#include <cmath> 
#include <iomanip> 
using namespace std; 
double fn(double x) { 
    return sin(x); 
} 
double taylorSeries(double x, double z) { 
    double rez = 0.0; 
    double term = x; 
    int n = 1; 
    while (abs(term) > z) { 
        rez += term; 
        term = (-1.0 * term * x * x) / ((2 * n) * (2 * n + 1)); 
        n++; 
    } 
    return rez; 
} 
int main() { 
    double xs, xf, dx, z; 
    cout << "Введите начальное значение x: "; 
    cin >> xs; 
    cout << "Введите конечное значение x: "; 
    cin >> xf; 
    cout << "Введите размер шага: "; 
    cin >> dx; 
    cout << "Введите нужную точность: "; 
    cin >> z; 
    cout << setw(10) << "x" << setw(15) << "f(x)" << setw(20) << "просуммированно" << endl; 
    cout << "----------------------------------------------------------" << endl; 
    double x = xs; 
    while (x <= xf) { 
        double rez = taylorSeries(x, z); 
        double ex = fn(x); 
        int qwrt = 1; 
        while (abs(rez - ex) > z) { 
            rez = taylorSeries(x, z / qwrt++); 
        } 
        cout << fixed << setprecision(6); 
        cout << setw(10) << x << setw(15) << rez << setw(20) << qwrt << endl; 
        x += dx; 
    } 
    return 0; 
} 
'''
