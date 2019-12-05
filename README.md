# -
node생성, link기법 사용


#include <stdio.h>

#include <stdlib.h>

typedef struct _node { //node 구조체 선언
	void* dataPtr;
	struct _node* link;
}NODE;

NODE* createNode(void* dataPtr); //node 생성 및 초기화 함수

void main() { 
	NODE* node1; 
	NODE* node2; 
	NODE* nodePtr; 
	int data1 = 7, data2 = 75; 
	int* dataPtr1 = &data1, dataPtr2 = &data2; 

	node1 = createNode(dataPtr1); 
	node2 = createNode(dataPtr2); 
	node1->link = node2; 

	nodePtr = node1; 
	while (nodePtr != NULL) { 
		printf("데이터: %d \n", *(int*)nodePtr->dataPtr); 		
		nodePtr = nodePtr->link;
 }
}
NODE* createNode(void* dataPtr) { 
	NODE* nodePtr;
	nodePtr = (NODE*)malloc(sizeof(NODE));
	nodePtr->dataPtr = dataPtr;
	nodePtr->link = NULL; 
	return nodePtr;
}


