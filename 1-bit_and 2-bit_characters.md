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