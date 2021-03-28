# [Tow Sum](https://github.com/Urchinzhou/Keep-ARTS/issues/2)

# 枚举
```C
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target, int* returnSize){
    int i,j;
    for(i = 0; i < numsSize; i++){
        for(j = i + 1; j < numsSize; j++){
            if(nums[i] + nums[j] == target){
                int *arr = malloc(2 * sizeof(int));
                arr[0] = i;
                arr[1] = j;
                *returnSize = 2;
                return arr;
            }
        }
    }
    *returnSize = 0;
    return NULL;
}
```
# 哈希表
思路：创建哈希表，遍历数组，根据数组元素 x，先在哈希表中查找是否存在 target-x，若不存在，则添加 x 至哈希表，若存在，则结束遍历，返回结果。
注：“先查找 target - x，再添加 x 至哈希表”的作用在于，避免 x 与自己匹配，比如入参为 arr[3,3]，target 为 6 时，倘若先添加 x 再匹配，则会出现 arr[0] 与 arr[0] 匹配出结果的情况。
```C
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */

 struct hashmap{
     int key;
     int value;
     UT_hash_handle hh;
 };
struct hashmap *hashtable;

 struct hashmap *find(int key){
     struct hashmap *tmp = NULL;
     HASH_FIND_INT(hashtable, &key, tmp);
     return tmp;
 }

 void insert(int key, int value){
     struct hashmap *hm = find(key);
     if(hm == NULL){
         struct hashmap *tmp = (struct hashmap*)malloc(sizeof(struct hashmap));
         tmp->key = key;
         tmp->value = value;
         HASH_ADD_INT(hashtable, key, tmp);
     }
     else
        hm->value = value;
 }

int* twoSum(int* nums, int numsSize, int target, int* returnSize){
    hashtable = NULL;
    for(int i = 0; i < numsSize; i++){
        struct hashmap *hm = find(target - nums[i]);
        if(hm != NULL){
            int *arr = malloc(sizeof(int) * 2);
            arr[0] = hm->value;
            arr[1] = i;
            *returnSize = 2;
            return arr;
        }
        insert(nums[i], i);
    }
    *returnSize = 0;
    return NULL;
}