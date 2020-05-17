# 11. ʢ���ˮ������
### ԭ��
���� n ���Ǹ����� a1��a2��...��an��ÿ�������������е�һ���� (i, ai) ���������ڻ� n ����ֱ�ߣ���ֱ�� i �������˵�ֱ�Ϊ (i, ai) �� (i, 0)���ҳ����е������ߣ�ʹ�������� x �Ṳͬ���ɵ�����������������ˮ��

˵�����㲻����б�������� n ��ֵ����Ϊ 2��
ͼ�д�ֱ�ߴ����������� [1,8,6,2,5,4,8,3,7]���ڴ�����£������ܹ�����ˮ����ʾΪ��ɫ���֣������ֵΪ 49�� 

ʾ����
���룺[1,8,6,2,5,4,8,3,7]
�����49

��Դ�����ۣ�LeetCode��
���ӣ�https://leetcode-cn.com/problems/container-with-most-water

### �ⷨ
```java
public class maxArea {
    public int maxArea(int[] height) {
        int res = 0;
        for (int i = 0, j = height.length - 1; i < j; ) {
            if (height[i] > height[j])
                res = Math.max(res, (j - i) * height[j--]);
            else
                res = Math.max(res, (j - i) * height[i++]);
        }
        return res;
    }
}
```
˼·������
* Ҫȷ��ʢˮ���������Ҫ֪�����ߵĸ߶ȣ�Ȼ��ȡ���֮һΪ���ߡ�������Ҫ֪������֮��ľ��룬Ϊ�ס�
* ĳ��λ�õĸ߶�Ϊ`height[i]`���ٶ��������ߵ������ֱ�Ϊ`i, j`��������Ŀ����ʾ��ͼ����������֮���λ�þ���`j - i`����������ļ��㷽ʽ���ǣ�
    * ���`height[i] > height[j]`����ô�������`(j - i) * height[j]`
    * �������Ϊ`(j - i) * height[i]`
* Ҫö�ٳ����е�`(i, j)`��ϣ����������ȡ����������Ǳ������ˡ�
* ���һ��ʼ��`i = 0, j = height.length - 1`����ʱ��������ܸı�`i`����`j`���׶����̣�������������£���β��п��ܵõ�һ��������������Ȼ�׶�Ҫ��̣��Ǿ͸ı�֮ǰ�������ԵĶ̰�̣��������а���һ�߻��������Ƿ��ܵõ�һ�������ıߴӶ�ʵ�֡��ߡ��䳤��
    * ���`height[i] > height[j]`������һ�γ��������Ӧ�ý�`j--`�����ƣ���֮��һ�γ���Ӧ��`i++`��
* �������ĳһ��`(i, j)`���ڳ��Խ��̱߻�������ʱ��Ϊʲô����i���ƻ���j�����أ���Ϊ��������������������Ѿ������Թ��ˣ���������Ϊ`height[i - 1] < height[j]`��������`(i, j)`�ģ�����`i`���ǻص��Ѿ����ǹ�������ˡ�
* ���ϣ��ڲ��ϳ��ԵĹ����У�����Ҫ�������`res = Math.max(res, (j - i) * height[j--]);`����`res = Math.max(res, (j - i) * height[i++]);`��
* ʱ�临�Ӷ�Ϊ$O(n)$���ռ临�Ӷ�Ϊ$O(1)$��

���н����

* ִ����ʱ :3 ms, ������ Java �ύ�л�����91.66%���û�
* �ڴ����� :40.8 MB, ������ Java �ύ�л�����5.04%���û�

----
* ����LeetCode����뿴[���ֿ�](https://github.com/ustcyyw/yyw_algorithm)
* �������С�����Զ��������ο�[������Ŀ](https://github.com/ustcyyw/markdown_tool)
* [�ҵ�github](https://github.com/ustcyyw)���б��С��ĿҲ�ܺ��档��΢���~С����зз