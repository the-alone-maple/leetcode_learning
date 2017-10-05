# leetcode_learning
an leetcode program experience

<h3>1.3sum-closest(哈希、排序)</h3>

    Code：
    public int threeSumClosest(int[] num, int target) {
        Arrays.sort(num);        
        int result = num[0]+num[1]+num[2];
        for (int i = 0; i < num.length - 2; i++) {
            int start = i + 1, end = num.length - 1;
            while (start < end) {
                int sum = num[i] + num[start] + num[end];
                if (sum > target){
                     end--;
                 } else {
                    start++;
                 }
                   
                 if (Math.abs(sum - target) < Math.abs(result - target)) {
                    result = sum;
                }
            }
        }
        return result;
    }
    
    Programming idea:
    这道题目是为了求最接近目标值的结果，本题的解题思路是
        （1）先获得给定数组的有序结果
        （2）建立循环，i代表当前执行到的位置，设置起始标记left = i+1，设置尾标记right = 数组长度-1
            （注意：这里的i只能执行到num.length-2位,因为存在left和right标记）
        （3）根据i循环求num[i]+num[left]+num[right]的结果sum，并将（sum-tartget）与（result-target）对比，绝对值越小的则为正确。
        （4）反复执行步骤（3），直到得出最接近的值。
    
    
