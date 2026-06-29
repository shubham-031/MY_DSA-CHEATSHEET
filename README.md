# MY_DSA-CHEATSHEET

सर्वात आधी
int answer = INT_MAX;

याचा अर्थ:

answer मध्ये सर्वात मोठी possible integer value ठेवा.

म्हणजे:

answer = 2147483647

(32-bit int साठी)Step 1 : Question कसा वाचायचा?

Question मध्ये keywords शोध.

Subarray

Minimum Length

Sum >= Target

आता स्वतःला विचार.

Subarray आहे?

YES

Fixed Length दिली आहे?

NO

Condition आहे?

Sum >= target

Return काय?

Minimum Length

Brain मध्ये लगेच trigger
Universal Pattern
int left = 0;

for(int right = 0; right < n; right++)
{
    // 1. Expand Window

    add(nums[right]);



    // 2. Shrink Window

    while(window becomes valid)
    {
        update answer

        remove(nums[left]);

        left++;
    }
}




Golden Rule

हे तीन rules कायम लक्षात ठेव:

Count Subarrays
→ answer += windowSize

Longest / Maximum
→ answer = max(answer, windowSize)

Shortest / Minimum
→ answer = min(answer, windowSize)
````markdown
# MY_DSA-CHEATSHEET

# Variable Sliding Window

## सर्वात आधी

```cpp
int answer = INT_MAX;
```

याचा अर्थ:

`answer` मध्ये सर्वात मोठी possible integer value ठेवा.

म्हणजे:

```cpp
answer = 2147483647
```

(32-bit `int` साठी)

---

## Step 1 : Question कसा वाचायचा?

Question मध्ये keywords शोध.

```
Subarray

Minimum Length

Sum >= Target
```

आता स्वतःला विचार.

```
Subarray आहे?

YES

Fixed Length दिली आहे?

NO

Condition आहे?

Sum >= target

Return काय?

Minimum Length
```

---

## Brain मध्ये लगेच trigger

### Universal Pattern

```cpp
int left = 0;

for(int right = 0; right < n; right++)
{
    // 1. Expand Window

    add(nums[right]);



    // 2. Shrink Window

    while(window becomes valid)
    {
        update answer;

        remove(nums[left]);

        left++;
    }
}
```

---

## Golden Rule

हे तीन rules कायम लक्षात ठेव:

### Count Subarrays

```cpp
answer += windowSize;
```

### Longest / Maximum

```cpp
answer = max(answer, windowSize);
```

### Shortest / Minimum

```cpp
answer = min(answer, windowSize);
```
````




Variable Sliding Window

