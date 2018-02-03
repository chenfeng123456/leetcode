1-bit and 2-bit Characters
========

Description:
--------
We have two special characters. The first character can be represented by one bit 0. The second character can be represented by two bits. <font color=b>(10 or 11)</font><br>

Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.

Example 1:
--------
Input: <br>
bits = [1, 0, 0]<br>
Output: True<br>
Explanation: <br>
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.<br>

Example 2:
---------
Input: <br>
bits = [1, 1, 1, 0]<br>
Output: False<br>
Explanation: <br>
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.<br>
```cpp
bool isOneBitCharacter(int* bits, int bitsSize) {
    bool answer;
    int subscript=0;
    while(1)
    {
        if(subscript==bitsSize-1)
        {
            if(bits[subscript]==0)
            {
                answer=1;
                break;
            }
            else 
            {
                answer=0;
                break;
            }
        }
        else if(subscript==bitsSize-2)
        {
            if(bits[subscript]==1)
            {
                answer=0;
                break;
            }
            else
            {
                answer=1;
                break;
            }
        }
        if(bits[subscript]==0)
            subscript++;
        else if(bits[subscript]==1)
            subscript+=2;
    }
    return answer;
}
```
