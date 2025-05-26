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

    for (const auto& player : basketball) {
        names_in_basketball.insert(player.first_name + " " + player.last_name);
    }

    for (const auto& player : football) {
        string full_name = player.first_name + " " + player.last_name;
        if (names_in_basketball.count(full_name)) {
            result.push_back(full_name);
        }
    }

    return result;
}

```


## Task 2: 


```C++

#include <iostream>
#include <vector>

using namespace std;

int find_missing_number(const vector<int>& nums, int n) {
    int expected_sum = n * (n + 1) / 2;
    int actual_sum = 0;

    for (int num : nums) {
        actual_sum += num;
    }

    return expected_sum - actual_sum;
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

```


## Task 4:


```C++


#include <iostream>
#include <vector>
#include <algorithm>
#include <limits>

using namespace std;

int highest_product(const vector<int>& nums) {
    int max1 = INT_MIN, max2 = INT_MIN;
    int min1 = INT_MAX, min2 = INT_MAX;

    for (int n : nums) {
        if (n > max1) {
            max2 = max1;
            max1 = n;
        } else if (n > max2) {
            max2 = n;
        }

        if (n < min1) {
            min2 = min1;
            min1 = n;
        } else if (n < min2) {
            min2 = n;
        }
    }

    return max(max1 * max2, min1 * min2);
}

```


## Task 5:


```C++


#include <iostream>
#include <vector>

using namespace std;

vector<float> sort_temperatures(const vector<float>& readings) {
    int buckets[21] = {0}; // 97.0 to 99.0 by 0.1 -> 21 possible values

    for (float temp : readings) {
        int index = static_cast<int>((temp - 97.0) * 10);
        buckets[index]++;
    }

    vector<float> sorted;
    for (int i = 0; i < 21; ++i) {
        while (buckets[i]--) {
            sorted.push_back(97.0f + i * 0.1f);
        }
    }

    return sorted;
}

```


## Task 6:

```C++


#include <iostream>
#include <vector>
#include <unordered_set>

using namespace std;

int longest_consecutive_sequence(const vector<int>& nums) {
    unordered_set<int> num_set(nums.begin(), nums.end());
    int longest = 0;

    for (int num : num_set) {
        if (!num_set.count(num - 1)) {
            int current = num;
            int length = 1;

            while (num_set.count(current + 1)) {
                current++;
                length++;
            }

            longest = max(longest, length);
        }
    }

    return longest;
}
```
