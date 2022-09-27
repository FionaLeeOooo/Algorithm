# **Selection Sort**

### **Step**
> 1.在未排序序列中找到最小（大）元素，存放到排序序列的起始位置  
> 2.从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾  
> 3.重复第二步，直到所有元素均排序完毕

### **Time Complexity**: O(n²) 
***

### **python**
```python
def findSmallest(array):
    smallest = array[0]
    smallest_index = 0
    for i in range(1, len(array)):
        if array[i] < smallest:
            smallest = array[i]
            smallest_index = i
    return smallest_index

def selectionSort(arr):
    newArr = []
    for i in range(len(arr)):
        smallest = findSmallest(arr)
        newArr.append(arr.pop(smallest))
    return newArr

print(selectionSort([5, 3, 6, 2, 1, 9, 110]))
```

### **java**
```java
public class SelectionSort {
    // 选择排序：每一轮选择最小元素交换到未排定部分的开头

    public int[] sortArray(int[] nums) {
        int len = nums.length;
        // 循环不变量：([)0, i) 有序，且该区间里所有元素就是最终排定的样子
        for (int i = 0; i < len - 1; i++) {
            // 选择区间 [i, len - 1] 里最小的元素的索引，交换到下标 i
            int minIndex = i;
            for (int j = i + 1; j < len; j++) {
                if (nums[j] < nums[minIndex]) {
                    minIndex = j;
                }
            }
            swap(nums, i, minIndex);
        }
        return nums;
    }

    private void swap(int[] nums, int index1, int index2) {
        int temp = nums[index1];
        nums[index1] = nums[index2];
        nums[index2] = temp;
    }

    public static void main(String[] args) {
        int[] nums = {5, 2, 3, 1};
        SelectionSort selectionSort = new SelectionSort();
        int[] res = selectionSort.sortArray(nums);
        System.out.println(Arrays.toString(res));
    }

}
```