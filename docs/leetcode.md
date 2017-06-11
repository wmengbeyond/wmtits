### 1. two sum
* desc:
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

```
Example:
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

* C++ code
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
* C code 
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
### 2. Add Two Numbers

* desc:
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8

* C++ code
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* res = new ListNode(-1);
        ListNode* cur = res;
        int carry = 0;
        while ((l1 != NULL) || (l2 != NULL)) {
            int n1 = l1!=NULL? l1->val:0;
            int n2 = l2!=NULL? l2->val:0;
            
            int sum = n1 + n2 + carry;
            carry = sum / 10;
            
            cur->val = sum % 10;
            if((l1->next != NULL) || (l2->next != NULL)) {
                cur->next = new ListNode(-1);
                cur = cur->next;
            }
            else {
                if (carry) {
                    cur->next = new ListNode(1);
                    cur = cur->next;
                    cur->next = NULL;
                }
            }
            
            if(l1 != NULL) {
                l1 = l1->next;
            }
            
            if(l2 != NULL) {
                l2 = l2->next;
            }
        }
        
        return res;
    }
};
```

### 3. Longest Substring Without Repeating Characters

* desc

Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

* C++ code

```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int m[256] = {0};
        int len = 0;
        int left = 0;
        
        for (int i = 0; i < s.size(); ++i) {
            if (m[s[i]] == 0 || m[s[i]] < left) {
                len = max(len, i - left + 1);
            }
            else {
                left = m[s[i]];
            }
            
            m[s[i]] = i + 1;
        }
        
        return len;
    }
};
```
