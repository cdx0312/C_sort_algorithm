#include <stdio.h>

void print(int* a, int a_size) {
    for (int i = 0; i < a_size; i++)
        printf("%d ", a[i]);
    printf("\n");
}

void InsertSort(int* a, int a_size) {
    for (int i = 1; i < a_size; i++) {
        if (a[i] < a[i-1]) {          //第i个元素如果大于第i-1个元素,直接插入
            int j = i - 1;
            int x = a[i];
            while (a[j] > x) {
                a[j+1] = a[j];
                j--;
            }
            a[j+1] = x;
        }
        print(a, a_size);
    }
}

void shellInsertSort(int* a, int a_size, int dk) {
    for (int i = dk; i < a_size; i++) {
        if (a[i] < a[i-dk]) {
            int j = i - dk;
            int x = a[i];
            a[i] = a[i-dk];
            while (x < a[j]) {
                a[j + dk] = a[j];
                j = j - dk;
            }
            a[j+dk] = x;
        }
        print(a,a_size);
    }
}

void shellSort (int* a, int a_size) {
    int dk = a_size / 2;
    while (dk >= 1){
        shellInsertSort(a, a_size, dk);
        dk /= 2;
    }
}

int selectMinKey(int* a, int a_size, int i) {
    int k = i;
    for (int j = i + 1; j < a_size; j++) {
        if (a[k] > a[j])
            k = j;
    }
    return k;
}

void selectSort(int* a, int a_size) {
    for (int i = 0; i < a_size; i++) {
        int index = selectMinKey(a, a_size,i);
        if (index != i){
            int temp = a[i];
            a[i] = a[index];
            a[index] = temp;
        }
        print(a,a_size);
    }
}

void selectSort2(int* a, int a_size) {
    for (int i = 1; i <= a_size/2; i++) {
        int min = i, max = i;
        for (int j = i - 1; j <= a_size-i; j++) {
            if (a[j] > a[max])
                max = j;
            if (a[j] < a[min])
                min = j;
        }
        int tmp = a[i-1];
        a[i-1] = a[min];
        a[min]=tmp;

        tmp = a[a_size-i];
        a[a_size-i] = a[max];
        a[max] = tmp;
        print(a, 8);
    }
}

/*
 * @param a是待调整的堆数组
 * @param s是待调整的数组元素的位置
 * @param a_size是数组长度
 */
void HeapAdjust (int* a, int a_size, int s) {
    int tmp = a[s];
    int child = 2 * s + 1;
    while (child < a_size) {
        if (child + 1 < a_size && a[child]<a[child+1])
            child++;
        if (a[s] < a[child]) {
            a[s] = a[child];
            s = child;
            child = 2 * s + 1;
        } else
            break;
        a[s] = tmp;
    }
    print(a, a_size);

}

void buildHeap (int* a, int a_size) {
    for (int i = (a_size - 1) / 2; i >= 0; i--)
        HeapAdjust(a,i,a_size);
}

void HeapSort (int* a, int a_size) {
    buildHeap(a, a_size);
    for (int i = a_size-1; i>0; i--){
        int tmp = a[i];
        a[i] = a[0];
        a[0] = tmp;
        HeapAdjust(a, i, 0);
    }
}

void bubbleSort(int* a, int a_size) {
    for (int i = 0; i < a_size; i++){
        for (int j = 0; j < a_size-i-1; j++) {
            if (a[j] > a[j+1]) {
                int tmp = a[j];
                a[j] = a[j+1];
                a[j+1] = tmp;
            }
        }
        print(a, 8);
    }
}

void bubbleSort1(int* a, int a_size) {
    int i = a_size - 1;
    while (i > 0) {
        int pos = 0;
        for (int j = 0; j < i; j++) {
            if (a[j] > a[j + 1]) {
                pos = j;
                int tmp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = tmp;
            }
        }
        i = pos;
        print(a, a_size);
    }
}

void bubblesort2(int* a, int a_size) {
    int low = 0;
    int high = a_size - 1;
    while (low < high) {
        for (int j = low; j < high; j++) {
            if (a[j] > a[j+1]){
                int tmp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = tmp;
            }
        }
        --high;
        for(int j = high; j > low; j--) {
            if (a[j] < a[j-1]) {
                int tmp = a[j-1];
                a[j-1] = a[j];
                a[j] = tmp;
            }
        }
        low++;
        print(a, a_size);
    }
}

void swap (int* a, int* b) {
    int tmp = *a;
    *a = *b;
    *b = tmp;
}

int partition(int* a, int low, int high) {
    int key = a[low];
    while(low<high) {
        while (low < high && a[high] >= key)
            high--;
        swap(a+low, a+high);
        while (low < high && a[low] <= key)
            low++;
        swap(a + low, a + high);
    }
    print(a, 8);
    return low;
}

void quicksort(int* a, int low, int high){
    if (low < high) {
        int key = partition(a, low, high);
        quicksort(a, low, key-1);
        quicksort(a, key+1, high);
    }
}
//a[i..m]和a[m+1,..n]归并到辅助数组b[i...n]
void mergesort(int* a, int* b, int i, int m, int n) {
    int j, k;
    for (j = m + 1, k = i; i <= m && j <= n; k++) {
        if (a[j] < a[i])
            b[k] = a[j++];
        else
            b[k] = a[i++];
    }
    while (j <= m)
        b[k++] = a[i++];
    while (j <= n)
        b[k++] = r[j++];
}             
    int main() {
        int a[8] = {3, 1, 5, 7, 2, 4, 9, 6};
//    InsertSort(a, 8);
//    shellSort(a, 8);
//    selectSort(a,8);
//    selectSort2(a, 8);
//    HeapSort(a, 8);
//    bubblesort2(a, 8);
        quicksort(a, 0, 7);
        print(a, 8);
        return 0;
    }
