---
title: 指標 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, pointers
- declarations, pointers
- pointers [C++]
- pointers, declarations
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dad1f9a223d8eb97c8e59e955bd5358b27dafd08
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942863"
---
# <a name="pointers-c"></a>指標 （c + +）
指標是使用下列序列宣告。  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator ;  
```  
  
 其中可能會使用 `declarator` 的任何有效的指標宣告子。  簡單指標宣告子的語法如下：  
  
```  
* [cv-qualifiers] identifier [= expression]  
```  
  
 1. 宣告指定名稱：  
  
    - 選擇性的儲存類別規範。 如需詳細資訊，請參閱 <<c0> [ 規範](../cpp/specifiers.md)。  
  
    - 選擇性**const**或是**volatile**關鍵字套用至將指向的物件型別。  
  
    - 類型指定名稱：表示將指向之物件類型的類型名稱。  
  
 2. 宣告子：  
  
    - 選擇性的 Microsoft 專有修飾詞。 如需詳細資訊，請參閱 < [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)。  
  
    - `*` 運算子。  
  
    - 選擇性**const**或是**volatile**關鍵字套用至指標本身。  
  
    - 識別碼。  
  
    - 選擇性的初始設定式。  
  
     函式指標的宣告子如下所示：  
  
```  
(* [cv-qualifiers] identifier )( argument-list ) [cv-qualifers]  
[exception specification] [= expression];  
```  
  
-   對於指標陣列，其語法如下所示：  
  
```  
* identifier [ [ constant-expression ] ]  
```  
  
-   多個宣告子及其初始設定式可以一起出現在逗號分隔清單的單一宣告中，其後為宣告指定名稱。  
  
 指標宣告的簡單範例如下：  
  
```cpp 
char *pch;  
```  
  
 上述宣告會指定`pch`指向的物件型別的**char**。  
  
 較複雜的範例為：  
  
```cpp 
static unsigned int * const ptr;  
```  
  
 上述宣告會指定`ptr`是常數指標類型的物件**不帶正負號** **int**具有靜態儲存期。  
  
 下列範例顯示如何宣告及初始化多個指標：  
  
```cpp 
static int *p = &i, *q = &j;  
```  
  
 在上述範例中，指標 p 和 q 皆指向類型的物件**int**並分別初始化為 i 和 j 的位址。  儲存類別規範**靜態**適用於這兩個指標。  
  
## <a name="example"></a>範例  
  
```cpp 
// pointer.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   int i = 1, j = 2; // local variables on the stack  
   int *p;  
  
   // a pointer may be assigned to "point to" the value of  
   // another variable using the & (address of) operator  
   p = & j;   
  
   // since j was on the stack, this address will be somewhere  
   // on the stack.  Pointers are printed in hex format using  
   // %p and conventionally marked with 0x.    
   printf_s("0x%p\n",  p);  
  
   // The * (indirection operator) can be read as "the value  
   // pointed to by".  
   // Since p is pointing to j, this should print "2"  
   printf_s("0x%p %d\n",  p, *p);  
  
   // changing j will change the result of the indirection  
   // operator on p.  
   j = 7;  
   printf_s("0x%p %d\n",  p, *p );  
  
   // The value of j can also be changed through the pointer  
   // by making an assignment to the dereferenced pointer  
   *p = 10;  
   printf_s("j is %d\n", j); // j is now 10  
  
   // allocate memory on the heap for an integer,  
   // initialize to 5  
   p = new int(5);  
  
   // print the pointer and the object pointed to  
   // the address will be somewhere on the heap  
   printf_s("0x%p %d\n",  p, *p);  
  
   // free the memory pointed to by p  
   delete p;  
  
   // At this point, dereferencing p with *p would trigger  
   // a runtime access violation.  
  
   // Pointer arithmetic may be done with an array declared  
   // on the stack or allocated on the heap with new.  
   // The increment operator takes into account the size   
   // of the objects pointed to.  
   p = new int[5];  
   for (i = 0; i < 5; i++, p++) {  
      *p = i * 10;  
      printf_s("0x%p %d\n", p, *p);  
   }  
  
   // A common expression seen is dereferencing in combination  
   // with increment or decrement operators, as shown here.  
   // The indirection operator * takes precedence over the   
   // increment operator ++.   
   // These are particularly useful in manipulating char arrays.  
   char s1[4] = "cat";  
   char s2[4] = "dog";  
   char* p1 = s1;  
   char* p2 = s2;  
  
   // the following is a string copy operation  
   while (*p1++ = *p2++);  
  
   // s2 was copied into s1, so now they are both equal to "dog"  
   printf_s("%s %s", s1, s2);  
}  
```  
  
```Output  
0x0012FEC8  
0x0012FEC8 2  
0x0012FEC8 7  
j is 10  
0x00320850 5  
0x00320850 0  
0x00320854 10  
0x00320858 20  
0x0032085C 30  
0x00320860 40  
dog dog  
```  
  
## <a name="example"></a>範例  
 另一個範例示範如何在資料結構中使用指標，此例中為連結清單。  
  
```cpp 
// pointer_linkedlist.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct NewNode {  
   NewNode() : node(0){}  
   int i;  
   NewNode * node;  
};  
  
void WalkList(NewNode * ptr) {  
   if (ptr != 0) {  
      int i = 1;  
      while (ptr->node != 0 ) {  
         cout << "node " << i++ << " = " << ptr->i << endl;  
         ptr = ptr->node;  
      }  
      cout << "node " << i++ << " = " << ptr->i << endl;  
   }  
}  
  
void AddNode(NewNode ** ptr) {  
   NewNode * walker = 0;  
   NewNode * MyNewNode = new NewNode;  
   cout << "enter a number: " << endl;  
   cin >> MyNewNode->i;  
  
   if (*ptr == 0)  
      *ptr = MyNewNode;  
   else  {  
      walker = *ptr;  
      while (walker->node != 0)  
         walker = walker->node;  
  
      walker->node = MyNewNode;  
   }  
}  
  
int main() {  
   char ans = ' ';  
   NewNode * ptr = 0;  
   do {  
      cout << "a (add node)  d (display list)  q (quit)" << endl;  
      cin >> ans;  
      switch (ans) {  
      case 'a':  
         AddNode(&ptr);  
         break;  
      case 'd':  
         WalkList(ptr);  
         break;  
      }  
   } while (ans != 'q');  
}  
```  
  
```Output  
  
      a  
45  
d  
a  
789  
d  
qa (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
a (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
node 2 = 789  
a (add node)  d (display list)  q (quit)  
```  
  
## <a name="see-also"></a>另請參閱  
 [間接取值運算子：*](../cpp/indirection-operator-star.md)   
 [傳址運算子：&](../cpp/address-of-operator-amp.md)