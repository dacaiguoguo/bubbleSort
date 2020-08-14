# bubbleSort
bubbleSort
```
//
//  main.c
//  BubbleSort
//
//  Created by dacaiguoguo on 2020/8/14.
//  Copyright © 2020 dacaiguoguo. All rights reserved.
//

#include <stdio.h>
#include <stdbool.h>
void bubbleSort(int* array, int length, _Bool betterFlag);
void logArray(int* toSortArray, int length);
int main(int argc, const char * argv[]) {
    //    int toSortArray[10] = {3, 6, 8, 2, 1, 0, 9, 4, 7, 5};
    int toSortArray[10] = {13, 6, 38, 22, 81, 170, 29, 34, 167, 135};
    // int toSortArray[10] = {9, 8, 7, 6, 5, 4, 3, 2, 1, 0 };
    int lengthOfArray = sizeof(toSortArray)/sizeof(int);
    logArray(toSortArray, lengthOfArray);
    bubbleSort(toSortArray, lengthOfArray, true);
    return 0;
}


void logArray(int* toSortArray, int length) {
    for (int i=0; i<length; i++) {
        printf("%d ", toSortArray[i]);
        if (i == length-1) {
            printf("\n");
        }
    }
}

void bubbleSort(int* array, int length, _Bool betterFlag) {
    int exchangeCount = 0;
    int totalExchangeCount = 0;
    for (int maxLoopCount = length-1; maxLoopCount > 1; maxLoopCount--) {
        exchangeCount = 0;
        int initIndex = length - 1 - maxLoopCount;
        int maxIndex = initIndex;
        if (!betterFlag) {
            initIndex = 0;
        }
        for (int i=initIndex, j = initIndex+1; i < maxLoopCount; i++, j++) {
            int initNumber = array[i];
            int nextNumber = array[j];
            if (nextNumber > initNumber) {
                exchangeCount++;
                array[j] = initNumber;
                array[i] = nextNumber;
                logArray(array, length);
                if (array[i] > array[maxIndex]) {
                    maxIndex = i;
                }
            }
        }
        if (betterFlag && initIndex != maxIndex) {
            // 如果找到的最大值的位置不是起点位置就把最大值换到起点，这样一次循环就完成了冒泡和最大下沉的动作
            exchangeCount++;
            int temp = array[initIndex];
            array[initIndex] = array[maxIndex];
            array[maxIndex] =temp;
        }
        totalExchangeCount += exchangeCount;
        if (exchangeCount == 0) {
            // 如果没有发生位置交换说明已经完成排序 终止程序
            break;
        }
        logArray(array, length);
    }
    printf("totalexchangeCount:%d\n", totalExchangeCount);
}

```
