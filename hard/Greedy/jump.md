# 45. ��Ծ��Ϸ II
### ԭ��
����һ���Ǹ��������飬�����λ������ĵ�һ��λ�á�
�����е�ÿ��Ԫ�ش������ڸ�λ�ÿ�����Ծ����󳤶ȡ�
���Ŀ����ʹ�����ٵ���Ծ����������������һ��λ�á�

ʾ��:
����: [2,3,1,1,4]
���: 2
����: �������һ��λ�õ���С��Ծ���� 2��
���±�Ϊ 0 �����±�Ϊ 1 ��λ�ã��� 1 ����Ȼ���� 3 ��������������һ��λ�á�

˵��:
���������ǿ��Ե�����������һ��λ�á�

��Դ�����ۣ�LeetCode��
[����](https://leetcode-cn.com/problems/jump-game-ii)��https://leetcode-cn.com/problems/jump-game-ii

### �ⷨ
```java
public class jump {
    public int jump(int[] nums) {
        int n = nums.length;
        int[] count = new int[n];
        int start = 0;
        for(int i = 0; i < n && start < n; i++){
            if(i + nums[i] < start)
                continue;
            for(int j = start; j < n && j <= i + nums[i]; j++)
                count[j] = count[i] + 1;
            start = i + nums[i] + 1;
        }
        return count[n - 1] - 1;
    }
}
```
˼·������
* һ��ʼ�����ö�̬�滮�ģ������ʱ�ˣ��������£�

    * ```java
        class Solution {
            public int jump(int[] nums) {
                int n = nums.length;
                int[] count = new int[n];
                Arrays.fill(count, Integer.MAX_VALUE);
                count[0] = 0;
                for(int i = 1; i < n; i++){
                    for(int j = 0; j < i; j++){
                        if(nums[j] >= i - j){
                            count[i] = Math.min(count[i], count[j] + 1);
                        }
                    }
                }
                return count[n - 1];
            }
        }
        ```

    * ���ò�����Ϊʲô�ᳬʱ��ԭ���кܶ�ĸ��²�����ͽ�͵ġ��ٸ����ӣ����絽���2��3��4Ԫ�ض���Ҫ1�����ӵ�2��3��4Ԫ�ض����Ե�������Ԫ�أ���ô��������Ԫ����Ҫ2�����ӵ�2��Ԫ����������ӵ�3��4Ԫ�ص�����û�������������ʱ�����ж�����и��¡�

* ������ο˷��ظ�����������ء�������������ӣ�����ӵڶ���Ԫ�ؿ���������5��Ԫ�أ���������Ԫ�صĲ�����ȷ��Ϊ2�ˣ������Ͳ��ó��Դ�3��4��Ԫ���������ˡ������˼���ǣ��������ʹ��`count[i]`��ʾ�����`i`��Ԫ����Ҫ�����ٲ�������ô����ֻ��`count[i]`��ֵһ�Ρ�����������ȷ�Կ�������˼����

    * �����0��Ԫ�ؿ���������`i`��Ԫ�أ��޷�������`i + 1`��Ԫ�ء�
    * ��ô`count[0]`��`count[i]`�϶�����ֵ�˵�һ�Σ���ֵΪ1��
    * ���ڵ�1��Ԫ����Ȼֻ�ܴӵ�0��Ԫ������ȥ��
    * ���ڵ�2��Ԫ�أ��ӵ�1��Ԫ������ȥ��Ҫ���Σ��ӵ�0��Ԫ������ȥֻ��Ҫ1�Ρ���ȻֻҪ�������ϣ��϶��ӵ�0��Ԫ������ȥ����ֵ����`count[2]`����Ҫ�ٸ�ֵ��
    * ͬ�����ڵ�3��Ԫ�أ��ӵ�1��2��Ԫ������ȥ��Ҫ2�Σ���Ȼ�ӵ�0��Ԫ��ֱ������ȥ����ֵ����`count[3]`����Ҫ�ٸ�ֵ��
    * ͬ��ֱ����`i`��Ԫ�ض�ֻһ�θ�ֵΪ1���ɡ�
    * ��ô��`i + 1`��Ԫ�أ���ʱ`count[i + 1]`��û�и�ֵ����Ϊ��0��Ԫ���޷������ǣ����ע�������Ԫ��Ҫ��`[1, i]`��Ԫ������ȥ����������ȥ�鿴����`[1, i]`�е���һ��Ԫ�ؿ�������ȥ�������ҵ���`j`��Ԫ�أ�Ȼ���`count[i + 1]`��ֵΪ2����һ�θ�ֵ֮�������ȥ���Ǵ�`[j + 1, i]`������ȥЧ��һ�£���û��Ҫȥ�鿴�ˣ����Ի���ֻ��ֵ��һ�Ρ�

* ���Խ������Ĺؼ����ǣ����κ�һ��`count[i]`ֻ��ֵһ�Ρ�������`int start`��ʾ��ǰ��һ��Ԫ�أ�����������������Ԫ��û�и�ֵ����ô`[0, start - 1]`�Ѿ�����ֵ��һ�Σ�`[start, n - 1]`����Ҫ����һ�θ�ֵ��

* ����������У�������ÿһ��Ԫ�ؾ����ܵ�ȥ��`count`��ֵ������Ԫ��`nums[i]`��������������Զ�ط�Ϊ`i + nums[i]`��

    * ���`i + nums[i] < start`˵��������Ծ��Χ�ڵ�����`count`Ԫ�ض�����ֵ���ˣ���������
    * ���򣬾ͽ�`count`���������`start`��ʼ��ֵ��`i + nums[i]`��`count[j] = count[i] + 1;`���������ЩԪ�ص�Ψһһ�θ�ֵ�󣬱�����`start`�����壬������������Ϊ`i + nums[i] + 1;`
    * ���Կ������ͼʾ��������һ�£���[2,3,1,1,4,2,1]Ϊ���ӣ�
    * ![jumpͼʾ.png](https://github.com/ustcyyw/yyw_algorithm/blob/master/hard/Greedy/jump%E5%9B%BE%E7%A4%BA.png?raw=true)

* PS����ʵ����ⷨͦ����BFS�ģ�

    * ���ٲ�������������·����
    * ������Ծ����Ԫ�ؾ���������ڽ�㡣
    * ֻ��`count`Ԫ�ظ�ֵһ�����������������ÿ��Ԫ��ֻ����һ�Ρ�

* ����ע�����㣺

    * ��ѭ������`start < n`����Ϊ���`start >= n`˵�����е�`count`����Ԫ�ض�����ֵ���ˣ�����Ͳ���Ҫ����ѭ���ˡ�
    * ����ֵ`count[n - 1] - 1;`�������1����Ϊ�������ϸ�����룬�ᷢ�ְ�����߼�д������0��Ԫ����Ҫ1�����͵��µ�����Ԫ�ص���С�������ȴ𰸶�1������ȻҲ������ѭ����ʼ֮ǰ��ɵ�0��Ԫ�ص���ɵ���Χ�ڵ�`count`Ԫ�صĳ�ʼ����

* ʱ�临�Ӷ�Ϊ$O(n)$�ģ���Ϊֻ������`count`��Ԫ�ظ�ֵ��1�Σ��ռ临�Ӷ�Ϊ$O(n)$�ġ�

���н����

 * ִ����ʱ :2 ms, ������ Java �ύ�л�����94.93%���û�
 * �ڴ����� :41.3 MB, ������ Java �ύ�л�����5.00%���û�

----
* ����LeetCode����뿴[���ֿ�](https://github.com/ustcyyw/yyw_algorithm)
* �������С�����Զ��������ο�[������Ŀ](https://github.com/ustcyyw/markdown_tool)
* [�ҵ�github](https://github.com/ustcyyw)���б��С��ĿҲ�ܺ��档��΢���~С����зз