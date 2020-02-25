将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

示例：

输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */


struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2){
    if(l1==NULL){
        return l2;
    }
    if(l2==NULL){
        return l1;
    }
    struct ListNode* aim,*b;
    if(l1->val>l2->val){
        aim=l2;
        b=aim;
        l2=l2->next;
    }
    else{
        aim=l1;
        b=aim;
        l1=l1->next;
    }
    while(aim->next!=NULL){
        if(l1->val>l2->val){
            aim->next=l2;
            aim=aim->next;
            l2=l2->next;
        }
        else{
            aim->next=l1;
            aim=aim->next;
            l1=l1->next;
        }
    }
    if(l1==NULL){
        aim->next=l2;
        aim=aim->next;
    }
    else{
        aim->next=l1;
        aim=aim->next;
    }
    return b;
}
