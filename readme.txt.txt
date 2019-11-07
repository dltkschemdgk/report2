1. 리스트의 종류와 설명

단일 연결 리스트, 이중 연결 리스트, 원형 연결 리스트가 있습니다. 

#include <stdio.h>
#include <stdlib.h>
typedef struct list {
 int d;
 struct list* p;
} LIST;
LIST* root = NULL;
LIST* last = NULL;
void AddList(int a){
 LIST* r = (LIST*)malloc(sizeof(LIST));
 r->d = a;
 r->p = NULL;
 if(root==NULL) root = r;
 else           last->p = r;
 last = r;
}
int main(void){
 AddList(35);
 AddList(40);
 AddList(45);
 while(root){
  printf("%d\n", root->d);
  root = root->p;
 }
}

2. 트리의 종류와 설명

완전 이진 트리, 포화 이진 트리, 정 이진 트리, 편향 이진 트리가 있습니다. 

.... 5  ....
..3.. ...7
.............8

#include <stdio.h>
#include <stdlib.h>            
typedef struct Tree {
    struct Tree *l, *r;
    int d;
} T;
void print(T* p){
   printf("%d\n", p->d);
   if(p->l) print(p->l);
   if(p->r) print(p->r);    
}
T* mem(){
 T* p=(T*)malloc(sizeof(T));
 p->l=p->r=NULL;
 return(p);
}
int main(void){
    T *r, *r1, *r2, *l1;
    l1= (T*)mem(); l1->d=3; 
    r2= (T*)mem(); r2->d=8; 
    r1= (T*)mem(); r1->d=7; r1->r=r2;
    r= (T*)mem(); r->d=5; r->l=l1;  r->r=r1;
    print(r);
}

3. 그래프에 대한 설명

무방향 그래프와 방향 그래프가 있습니다.

