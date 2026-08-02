

![Pasted image 20260127124525](Pasted%20image%2020260127124525.png)


#include <bits/stdc++.h>
using namespace std;

// https://visualgo.net/en/sorting?slide=7-1
void bubbleSort(int a[], int N) { // the standard version
  for (; N > 0; --N) // N iterations
    for (int i = 0; i < N-1; ++i) // except the last, O(N)
      if (a[i] > a[i+1]) // not in non-decreasing order
        swap(a[i], a[i+1]); // swap in O(1)
}


// https://visualgo.net/en/sorting?slide=11-2
void merge(int a[], int low, int mid, int high) {
  // subarray1 = a[low..mid], subarray2 = a[mid+1..high], both sorted
  int N = high-low+1;
  int b[N]; // discuss: why do we need a temporary array b?
  int left = low, right = mid+1, bIdx = 0;
  while (left <= mid && right <= high) // the merging
    b[bIdx++] = (a[left] <= a[right]) ? a[left++] : a[right++];
  while (left <= mid) b[bIdx++] = a[left++]; // leftover, if any
  while (right <= high) b[bIdx++] = a[right++]; // leftover, if any
  for (int k = 0; k < N; ++k) a[low+k] = b[k]; // copy back
}

// https://visualgo.net/en/sorting?slide=11-5
void mergeSort(int a[], int low, int high) {
  // the array to be sorted is a[low..high]
  if (low < high) { // base case: low >= high (0 or 1 item)
    int mid = (low+high) / 2; 
    mergeSort(a, low  , mid ); // divide into two halves
    mergeSort(a, mid+1, high); // then recursively sort them
    merge(a, low, mid, high); // conquer: the merge routine
  }
}


// https://visualgo.net/en/sorting?slide=12-7, with two lines addition for https://visualgo.net/en/sorting?slide=13
int partition(int a[], int i, int j) {
  // ================== the only addition for Randomized Quick Sort
  int r = i + rand()%(j-i+1); // a random index between [i..j]
  swap(a[i], a[r]); // tada
  // ==================
  int p = a[i]; // p is the pivot
  int m = i; // S1 and S2 are initially empty
  for (int k = i+1; k <= j; ++k) { // explore the unknown region
    if ((a[k] < p) || ((a[k] == p) && (rand()%2 == 0))) { // case 2 (PATCHED solution to avoid TLE O(N^2) on input array with identical values)
      ++m;
      swap(a[k], a[m]); // C++ STL algorithm std::swap
    } // notice that we do nothing in case 1: a[k] > p
  }
  swap(a[i], a[m]); // final step, swap pivot with a[m]
  return m; // return the index of pivot, to be used by Quick Sort
}

// https://visualgo.net/en/sorting?slide=12-8
void quickSort(int a[], int low, int high) {
  if (low < high) {
    int pivotIdx = partition(a, low, high); // O(N)
    // a[low..high] ~> a[low..pivotIdx-1], pivot, a[pivotIdx+1..high]
    quickSort(a, low, pivotIdx-1); // recursively sort left subarray
    // a[pivotIdx] = pivot is already sorted after partition
    quickSort(a, pivotIdx+1, high); // then sort right subarray
  }
}


// to be used by various sorting algorithms
void printArray(int a[], int n) {
  for (int i = 0; i < n; ++i) {
    if (i > 0) cout << " ";
    cout << a[i];
  }
  cout << "\n";
}


const int MAX_N = 200000; // big enough for our demo to notice the difference, use smaller number if you intend to print the actual array before/after sorting
// if you encounter runtime error/stack overflow (quite likely), you need to adjust your compilation setting to: g++ -std=gnu++17 -Wl,--stack,16777216

int main() {
  int a[MAX_N];
  int n = MAX_N; // use smaller number if you intend to print the actual array before/after sorting or if you want to test any O(N^2) sorting algorithm
  for (int i = 0; i < n; ++i)
    a[i] = rand()%1000000; // [0..1000000-1]

  clock_t begin = clock();
  // printArray(a, n);
  // bubbleSort(a, n); // very slow, do not use large MAX_N >= 10000 (will be minutes/hours...)
  // printArray(a, n);
  cout << "Elapsed time for Bubble Sort (uncomment the line above first, be careful, this is slow): " << double(clock() - begin) / CLOCKS_PER_SEC << "s\n";

  begin = clock();
  // printArray(a, n);
  mergeSort(a, 0, n-1);
  // printArray(a, n);
  cout << "Elapsed time for Merge Sort: " << double(clock() - begin) / CLOCKS_PER_SEC << "s\n";

  n = MAX_N;
  for (int i = 0; i < n; ++i)
    // a[i] = i; // increasing input, one of the hardest test case for (non Randomized) Quick Sort
    // a[i] = 7; // constant input, also one of the hardest test case for (WRONGLY implemented or non Randomized) Quick Sort
    a[i] = rand()%1000000; // [0..1000000-1]

  begin = clock();
  // printArray(a, n);
  quickSort(a, 0, n-1); // experiment with line 31-32 above
  // sort(a, a+n); // there is a (quicker) Quick Sort inside (called 'introsort')
  // printArray(a, n);
  cout << "Elapsed time for Quick Sort: " << double(clock() - begin) / CLOCKS_PER_SEC << "s\n";

  return 0;
}