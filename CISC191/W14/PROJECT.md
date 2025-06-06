# Final Project 

## Task 1:  

```C++

#include <iostream>
#include <vector>
#include <unordered_set>
#include <string>

using namespace std;

struct Player {
    string first_name;
    string last_name;
    string team;
};

vector<string> get_common_players(const vector<Player>& basketball, const vector<Player>& football) {
    unordered_set<string> names_in_basketball;
    vector<string> result;

    // Add basketball player full names to set
    for (const auto& player : basketball) {
        names_in_basketball.insert(player.first_name + " " + player.last_name);
    }

    // Check football players against set
    for (const auto& player : football) {
        string full_name = player.first_name + " " + player.last_name;
        if (names_in_basketball.count(full_name)) {
            result.push_back(full_name);
        }
    }

    return result;
}

int main() {
    vector<Player> basketball_players = {
        {"Jill", "Huang", "Gators"},
        {"Janko", "Barton", "Sharks"},
        {"Wanda", "Vakulskas", "Sharks"},
        {"Jill", "Moloney", "Gators"},
        {"Luuk", "Watkins", "Gators"}
    };

    vector<Player> football_players = {
        {"Hanzla", "Radosti", "32ers"},
        {"Tina", "Watkins", "Barleycorns"},
        {"Alex", "Patel", "32ers"},
        {"Jill", "Huang", "Barleycorns"},
        {"Wanda", "Vakulskas", "Barleycorns"}
    };

    vector<string> common_players = get_common_players(basketball_players, football_players);

    cout << "Players in both sports:\n";
    for (const string& name : common_players) {
        cout << name << endl;
    }

    return 0;
}


```


## Task 2: 


```C++

#include <iostream>
#include <vector>

using namespace std;

// Function to find the missing number from 0 to n
int find_missing_number(const vector<int>& nums, int n) {
    int expected_sum = n * (n + 1) / 2;
    int actual_sum = 0;

    for (int num : nums) {
        actual_sum += num;
    }

    return expected_sum - actual_sum;
}

int main() {
    vector<int> test1 = {2, 3, 0, 6, 1, 5}; // Missing 4, n = 6
    vector<int> test2 = {8, 2, 3, 9, 4, 7, 5, 0, 6}; // Missing 1, n = 9

    cout << "Missing number in test1: " << find_missing_number(test1, 6) << endl;
    cout << "Missing number in test2: " << find_missing_number(test2, 9) << endl;

    return 0;
}
```

## Task 3:


```C++

#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int max_profit(const vector<int>& prices) {
    if (prices.empty()) return 0;

    int min_price = prices[0];
    int max_profit = 0;

    for (int price : prices) {
        min_price = min(min_price, price);                 
        max_profit = max(max_profit, price - min_price);    
    }

    return max_profit;
}

int main() {
    vector<int> prices = {10, 7, 5, 8, 11, 2, 6};

    cout << "Maximum profit: " << max_profit(prices) << endl;

    return 0;
}


```


## Task 4:


```C++


#include <iostream>
#include <vector>
#include <algorithm>
#include <limits>
#include <climits>

using namespace std;

int highest_product(const vector<int>& nums) {
    if (nums.size() < 2) {
        cerr << "Array must contain at least two numbers." << endl;
        return 0;  // or throw exception
    }

    int max1 = INT_MIN, max2 = INT_MIN;
    int min1 = INT_MAX, min2 = INT_MAX;

    for (int n : nums) {
        // Update two largest
        if (n >= max1) {
            max2 = max1;
            max1 = n;
        } else if (n > max2) {
            max2 = n;
        }

        // Update two smallest
        if (n <= min1) {
            min2 = min1;
            min1 = n;
        } else if (n < min2) {
            min2 = n;
        }
    }

    // Compare product of two largest with product of two smallest (in case both are negative)
    return max(max1 * max2, min1 * min2);
}

int main() {
    vector<int> nums = {5, -10, -6, 9, 10};

    cout << "Highest product of any two numbers: " << highest_product(nums) << endl;

    return 0;
}


```


## Task 5:


```C++
#include <iostream>
#include <vector>
#include <cmath> // For round()

using namespace std;

vector<float> sort_temperatures(const vector<float>& readings) {
    const int num_buckets = 21;  // For temps from 97.0 to 99.0 (inclusive) in 0.1 steps
    int buckets[num_buckets] = {0};

    for (float temp : readings) {
        // Multiply by 10 and round to avoid floating-point imprecision
        int index = static_cast<int>(round((temp - 97.0f) * 10.0f));

        // Safety check (can be removed if inputs are guaranteed valid)
        if (index >= 0 && index < num_buckets) {
            buckets[index]++;
        }
    }

    vector<float> sorted;
    for (int i = 0; i < num_buckets; ++i) {
        for (int count = 0; count < buckets[i]; ++count) {
            sorted.push_back(97.0f + i * 0.1f);
        }
    }

    return sorted;
}

int main() {
    vector<float> readings = {98.6, 98.0, 97.1, 99.0, 98.9, 97.8, 98.5, 98.2, 98.0, 97.1};
    vector<float> sorted = sort_temperatures(readings);

    cout << "Sorted temperatures: ";
    for (float temp : sorted) {
        cout << temp << " ";
    }
    cout << endl;

    return 0;
}


```


## Task 6:

```C++


#include <iostream>
#include <vector>
#include <unordered_set>
#include <algorithm> // for max()

using namespace std;

int longest_consecutive_sequence(const vector<int>& nums) {
    if (nums.empty()) return 0;

    unordered_set<int> num_set(nums.begin(), nums.end());
    int longest = 0;

    for (int num : nums) {
        // Only try to build sequence if this is the start of one
        if (num_set.find(num - 1) == num_set.end()) {
            int current = num;
            int length = 1;

            // Count length of current sequence
            while (num_set.find(current + 1) != num_set.end()) {
                current++;
                length++;
            }

            longest = max(longest, length);
        }
    }

    return longest;
}

int main() {
    vector<int> test1 = {10, 5, 12, 3, 55, 30, 4, 11, 2};
    vector<int> test2 = {19, 13, 15, 12, 18, 14, 17, 11};

    cout << "Longest consecutive sequence length (Test 1): " << longest_consecutive_sequence(test1) << endl;
    cout << "Longest consecutive sequence length (Test 2): " << longest_consecutive_sequence(test2) << endl;

    return 0;
}

```
