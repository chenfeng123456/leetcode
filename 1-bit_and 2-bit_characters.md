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
***********
本题中1不能单独出现，必须和后面的1或0一起，所以如果遇到0，则继续看下一个，如果1，则直接跳到往后数第二个。如此重复，最后一次判断一定出现在倒数第二个或最后一个上。如果可以扫描到最后一个，便可以直接判断是否符合要求；若是倒数第二个，若为1，则最后一个不论是多少，一律与前一个配在一起，若为0，则最后一个一定单独出现。
