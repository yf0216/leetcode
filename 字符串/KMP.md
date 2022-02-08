---
title: KMP
updated: 2021-08-01T16:59:15.0000000+08:00
created: 2021-08-01T16:39:41.0000000+08:00
---

int KMP(string text,string pattern){

    if(!pattern.size())

        return 0;

    vector\<int> next(pattern.size());

    //next数组，表示模式串相同前后缀 eg. a b c d a b c a , 

    //  next数组为                     {0,0,0,0,1,2,3,1}；

    for (int i = 1, j = 0; i \< pattern.size();i++){//j为公共前缀的末尾字符位置        

while(j > 0 && pattern\[i\] != pattern\[j\])

            j = next\[j - 1\];//如果不匹配应该将j退回到哪个位置继续比较

        if(pattern\[i\] == pattern\[j\])

            j++;

        next\[i\] = j;

    }

    for (int i = 0, j = 0; i \< text.size();i++){

        while(j > 0 && text\[i\] != pattern\[j\])

            j = next\[j - 1\];

        if(text\[i\] == pattern\[j\])

            j++;

        if(j == pattern.size())

            return i - j + 1;

    }

    return -1;

}
