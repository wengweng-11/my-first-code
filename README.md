#include<stdio.h>
#include<malloc.h>
#define ERROR 0
#define OK 1
#define ElemType int

typedef int Status;
typedef struct LNode
{
 int data;
 struct LNode *next;
}LNode,*LinkList;


void merge(LinkList &l1,LinkList l2)
{
    LinkList p1,p2,q;
    q=l1;
    p1=l1->next;
    p2=l2->next;
    while(p1!=NULL&&p2!=NULL)
    {
        if(p1->data>p2->data)
        {
            q->next=p2;
            p2=p2->next;
            q=q->next;
        }
        else
        {
            q->next=p1;
            p1=p1->next;
            q=q->next;
        }
    }
    if(p1==NULL)q->next=p2;
    else if(p2==NULL)q->next=p1;
    delete l2;
}

 void create(LinkList &l,int n)
 {
     l=new LNode;
     l->next=NULL;
     LinkList r,p;
     int e,i;
     r=l;
     for(i=0;i<n;i++)
     {
         p=new LNode;
         scanf("%d",&e);
         p->data=e;
         r->next=p;
         p->next=NULL;
         r=p;
     }
 }

 void output(LinkList l)
 {
    LinkList p;
    p=l->next;
    while(p)
    {
        printf("%d ",p->data);
        p=p->next;
    }
    printf("\n");
 }

 int main()
 {
     int m,n;
     LinkList l1,l2;
     scanf("%d",&m);
     create(l1,m);
     scanf("%d",&n);
     create(l2,n);
     printf("List A:");
     output(l1);
     printf("List B:");
     output(l2);
      merge(l1,l2);
      printf("List C:");
      output(l1);
 }

