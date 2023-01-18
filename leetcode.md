# leetcode
### 1/18

### 283 移动0 
https://leetcode.cn/problems/move-zeroes/
双指针,当r不为0时,swap;l,r均++,
如果右边为0时,右边++;
> void moveZeroes(vector<int>& nums) {
        int n = nums.size();
        int left=0,right=0;
        while(right<n){
            if(nums[right]){
                swap(nums[left],nums[right]);
                left++;
            }
            right++;
        }
    }

### 448. 找到所有数组中消失的数字
https://leetcode.cn/problems/find-all-numbers-disappeared-in-an-array/
原地hash,利用数组自带范围的性质,将存在的数值-1的下标的值+n(范围最大)
之后遍历数组找到在范围内的值,将其下标+1后放入数组中
>vector<int> findDisappearedNumbers(vector<int>& nums) {
        int n=nums.size();
        vector<int> v;
        for(int i=1;i<=n;i++){
            int x=(nums[i-1]-1)%n;
            nums[x]+=n;
        }
        for(int i=1;i<=n;i++){
            if(nums[i-1]<=n) v.emplace_back(i);
        }
        return v;
    }

### 543. 二叉树的直径
https://leetcode.cn/problems/diameter-of-binary-tree/
利用递归,最大直径相当于这个点的左右子树长度之和+自己(+1)
则递归求出各自长度,然后将其替换一个在函数外定义的ans值
之后返回左右子树中的max+1给上面的节点
>int depth(TreeNode* rt){
        if(rt== nullptr) return 0;
        int l= depth(rt->left);
        int r= depth(rt->right);
        ans=max(ans,l+r+1);
        return max(l,r)+1;
    }


  ### 461. 汉明距离
https://leetcode.cn/problems/hamming-distance/
对应数字二进制中不同位置的数目,异或两个数字后求1的数量
c++自带__bultin_popcoin
自己写用Brian Kernighan算法
>int popcount(int x){
        int count=0;
        while(x>0){
            x&=(x-1);
            count++;
        }
        return count;
    }


### 剑指 Offer 58 - II. 左旋转字符串
https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/
1.利用c++特性,先将s[n]-s[end]推入,再推前面
2.substring,先拿前面再拿后面再合体
3.翻转数组,先翻转前面的再翻转后面的,最后一起翻转
s[i]可以表示为s.begin()+i;

### 剑指 Offer 05. 替换空格
https://leetcode.cn/problems/ti-huan-kong-ge-lcof/
c++新特性,建立新string,遍历oristring,遇到空格在pushback'%20'
否则推入原本
> string replaceSpace(string s) {
        string sum;
        for(auto c:s){
            if(c==' '){
                sum.push_back('%');
                sum.push_back('2');
                sum.push_back('0');
            }else{
                sum.push_back(c);
            }
        }
        return sum;
    }