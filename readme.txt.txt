1. 리스트의 종류와 설명

자료구조에는 리스트, 스택, 트리, 그래프 등이 포함되어 있습니다. 

단일 연결 리스트(링크 드 리스트) : 한 방향으로만 갈 수 있습니다.
이중 연결 리스트(더블 링크 드 리스트): 양 쪽에서 지시할 수 있습니다.
원형 연결 리스트가 있습니다 : 마지막 노드와 첫 번째 노드가 연결되어 있습니다. 

#include <stdio.h>
#include <stdlib.h>
typedef struct list {
 int d;
 struct list* p; //4바이트의 위치
} LIST;
LIST* root = NULL; // NULL은 주소가 지정되지 않았다는 뜻
LIST* last = NULL;
int main(void){
 LIST* r = (LIST*)malloc(sizeof(LIST)); // 동적 메모리 생성
 r->d = 35;   // 값 넣기
 r->p = NULL; // NULL 넣기
 root = r; // 포인터를 root에 저장 
 last = r; // 동적 메모리 p 포인터를 last에 보관
 
 r = (LIST*)malloc(sizeof(LIST)); //동적 메모리 생성
 last->p = r; // 이전 포인터 위치에 동적 메모리 포인터 넣기
 r->d = 40; // 값 넣기
 r->p = NULL; // NULL 넣기
 last = r;// 동적 메모리 P포인터를 last에 보관 
 
 r = (LIST*)malloc(sizeof(LIST));
 last->p = r;
 r->d = 45;
 r->p = NULL;
 last = r;
 
 while(root){
  printf("%d\n", root->d);
  root = root->p;
 }
}

함수로 만들기 

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

트리는 부모, 자식(차일드)관계를 가지고, 노드가 하나 이상의 차일드 노드를 가지는 것을 리라고 합니다.

이진 트리(바이너리 트리): 차일드 노드가 최대 2개까지 붙는 트리입니다. 
이진 검색 트리(바이너리 서치 트리): 왼쪽 노드와 그 이하 차일드 노드들은 현재 노드보다 작아야 하고, 
                                 오른 쪽 노드와 그 이하의 차일드 노드들은 현재 노드보다 큰 트리입니다.              
완전 이진 트리 : 마지막 레벨을 제외한 모든 서브 트리의 레벨이 같고, 모든 노드들이 왼쪽부터 채워져 있는 트리입니다.
풀 바이너리 트리 : 노드들의 차일드가 없거나, 두개 인 경우로 구성된 트리입니다.
포화 이진 트리 (퍼펙트 바이너리 트리) : 양쪽으로 빈공간 없이 모든 노드가 2개의 자식을 가지고 있는 트리입니다. 

.... 5  ....
..3.. ...7
.............8

#include <stdio.h>
#include <stdlib.h>            
typedef struct Tree {
    struct Tree *l, *r;
    int d; // 데이터 5,3,7,8
} T;
void print(T* p){
   printf("%d\n", p->d);
   if(p->l) print(p->l); // 왼쪽으로 끝까지 
   if(p->r) print(p->r); // 오른쪽으로 끝까지 
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

그래프를 표현하는 방법에는 Adjacency Matrix(2차원 배열에 표현)와 Adjacency List(링크 리스트로 표현)가 있습니다  

방향 그래프 : 방향이 있는 그래프 
무방향 그래프 : 방향이 없는 그래프 
사이클릭 그래프 : 하나 이상의 서클이 있는 그래프 
에이사이클릭 그래프 : 서클이 없는 그래프

4. 소감
이번 수업을 들으면서 자료구조에 대해 더 깊이 이해할 수 있었고, c언어에 더 흥미를 느끼게 되었습니다.
리스트와 트리를 복습하면서 이해가 되지 않았던 부분들을 이해할 수 있었습니다.
다음 수업시간에 배우게 될 그래프가 기대되고 c언어 꾸준히 공부하도록 하겠습니다.
c언어 사랑합니다 ~ 
