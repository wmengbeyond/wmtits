### two sum
desc:
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

```
Example:
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

C++ code
```
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> vects;
        int size = nums.size();
        for (int i = 0; i < size - 1; ++i) {
            int num1 = nums[i];
            for (int j = i + 1; j < size; ++j) {
                int num2 = target - num1;
                if (nums[j] == num2) {
                    vects.push_back(i);
                    vects.push_back(j);
                    return vects;
                }
            }
        }
    }
};
```
c code 
```
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {
    bool flag = false;
    int *p = (int) malloc(sizeof(int) * 2);
    for (int i = 0; i < numsSize - 1 && !flag; ++i) {
        for (int j = i + 1; j < numsSize; ++j) {
            if (target == (nums[i] + nums[j])) {
                p[0] = i;
                p[1] = j;
                flag = true;
                break;
            }
        }
    }
    
    return p;
}
```
