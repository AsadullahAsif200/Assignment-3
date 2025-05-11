# Assignment-3
# Code 1
#include <iostream>
using namespace std;
// Function to find the minimum and maximum values in an array
void getExtremes(float& min, float& max, float a[], int n) {
    // Initialize min and max with the first element of the array
    min = a[0];
    max = a[0];

    // Loop through the array starting from the second element
    for (int i = 1; i < n; ++i) {
        if (a[i] < min)
            min = a[i];  // Update min if current element is smaller

        if (a[i] > max)
            max = a[i];  // Update max if current element is larger
    }
}
// Main function to test getExtremes
int main() {
    float data[] = {4.5, 2.3, 9.1, 1.0, 7.6};  // Sample array
    int size = 5;
    float minVal, maxVal;
    // Call the function
    getExtremes(minVal, maxVal, data, size);
    // Display results
    cout << "Minimum Value: " << minVal << endl;
    cout << "Maximum Value: " << maxVal << endl;

    return 0;
}
#code 2
#include <iostream>
#include <cmath>  // for sqrt()
using namespace std;

// Function to compute standard deviation
double stdev(double x[], int n) {
    double sum = 0.0, mean, sum_sq = 0.0;

    // Step 1: Calculate mean
    for (int i = 0; i < n; ++i) {
        sum += x[i];
    }
    mean = sum / n;

    // Step 2: Calculate squared differences
    for (int i = 0; i < n; ++i) {
        sum_sq += (x[i] - mean) * (x[i] - mean);
    }

    // Step 3: Calculate standard deviation
    return sqrt(sum_sq / n);
}
// Test function in main
int main() {
    double data[] = {3.5, 2.1, 5.6, 1.8, 4.2};
    int size = 5;
    double result = stdev(data, size);
    cout << "Standard Deviation: " << result << endl;

    return 0;
}

#code 3
#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3], C[3][3];

    // Input matrix A
    cout << "Enter elements of Matrix A (3x3):" << endl;
    for (int i = 0; i < 3; ++i)
        for (int j = 0; j < 3; ++j)
            cin >> A[i][j];

    // Input matrix B
    cout << "Enter elements of Matrix B (3x3):" << endl;
    for (int i = 0; i < 3; ++i)
        for (int j = 0; j < 3; ++j)
            cin >> B[i][j];

    // Initialize result matrix C to 0
    for (int i = 0; i < 3; ++i)
        for (int j = 0; j < 3; ++j)
            C[i][j] = 0;

    // Matrix multiplication
    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            for (int k = 0; k < 3; ++k) {
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }

    // Display the result
    cout << "Resultant Matrix C (A x B):" << endl;
    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            cout << C[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}

#code 4
#include <iostream>
#include <string>
using namespace std;
int main() {
    string line;
    int chars = 0, spaces = 0, tabs = 0, lines = 0;
    cout << "Enter text (type END to stop):\n";
    while (true) {
        getline(cin, line);
        if (line == "END") break;

        lines++;
        for (char ch : line) {
            chars++;
            if (ch == ' ') spaces++;
            else if (ch == '\t') tabs++;
        }  }
    cout << "\nTotal Characters: " << chars << endl;
    cout << "Total Spaces: " << spaces << endl;
    cout << "Total Tabs: " << tabs << endl;
    cout << "Total Lines: " << lines << endl;
    return 0;
}

#code 5
#include <iostream>
using namespace std;

void sortArray(int arr[], int n) {
    // Simple bubble sort
    for (int i = 0; i < n-1; i++)
        for (int j = 0; j < n-i-1; j++)
            if (arr[j] > arr[j+1])
                swap(arr[j], arr[j+1]);
}

int main() {
    int arr[100], n;
    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter " << n << " numbers:\n";
    for (int i = 0; i < n; i++)
        cin >> arr[i];

    // ---- Mean ----
    float sum = 0;
    for (int i = 0; i < n; i++)
        sum += arr[i];
    float mean = sum / n;

    // ---- Median ----
    sortArray(arr, n);
    float median;
    if (n % 2 == 0)
        median = (arr[n/2 - 1] + arr[n/2]) / 2.0;
    else
        median = arr[n/2];

    // ---- Mode ----
    int maxCount = 0, mode = arr[0];
    for (int i = 0; i < n; i++) {
        int count = 0;
        for (int j = 0; j < n; j++)
            if (arr[j] == arr[i])
                count++;
        if (count > maxCount) {
            maxCount = count;
            mode = arr[i];
        }
    }

    // ---- Output ----
    cout << "\nMean = " << mean << endl;
    cout << "Median = " << median << endl;
    cout << "Mode = " << mode << endl;

    return 0;
}
 
#code 6

#include <iostream>
using namespace std;

void convertToRoman(int year) {
    int values[] = {1000, 900, 500, 400, 100, 90, 50, 40, 
                    10, 9, 5, 4, 1};
    string symbols[] = {"m", "cm", "d", "cd", "c", "xc", "l", "xl", 
                        "x", "ix", "v", "iv", "i"};

    cout << "Roman equivalent: ";
    for (int i = 0; i < 13; i++) {
        while (year >= values[i]) {
            cout << symbols[i];
            year -= values[i];
        }
    }
    cout << endl;
}

int main() {
    int year;
    cout << "Enter a year (1-3999): ";
    cin >> year;

    if (year < 1 || year > 3999) {
        cout << "Invalid year. Enter a value between 1 and 3999.\n";
    } else {
        convertToRoman(year);
    }

    return 0;
}


