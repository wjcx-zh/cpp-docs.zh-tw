---
title: "編譯器警告 （層級 1） C4291 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4291
dev_langs: C++
helpviewer_keywords: C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a1c03e12805c35ce04322a7ffb4d48499a9a9f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4291"></a>編譯器警告 (層級 1) C4291
'declaration': 沒有相符的 delete 運算子找到。如果初始設定擲回例外狀況，將不會釋放記憶體  
  
 在放置[新](../../cpp/new-operator-cpp.md)用有是沒有放置[刪除](../../cpp/delete-operator-cpp.md)。  
  
 運算子具有的物件配置記憶體時當**新**，呼叫物件的建構函式。 如果建構函式擲回例外狀況，應該取消配置物件所配置的記憶體。 這無法進行除非運算子**刪除**函式存在，並符合運算子**新**。  
  
 如果您使用運算子**新**而不需要任何額外的引數和編譯與[/GX](../../build/reference/gx-enable-exception-handling.md)， [/EHs](../../build/reference/eh-exception-handling-model.md)，或 /EHa 選項啟用例外狀況處理，編譯器會產生程式碼呼叫運算子**刪除**如果建構函式擲回例外狀況。  
  
 如果您使用的位置形式**新**運算子 （引數的形式除了大小的配置） 和物件的建構函式會擲回例外狀況，編譯器仍會產生程式碼以呼叫運算子**刪除**; 但它只會這麼如果運算子位置形式**刪除**存在比對運算子的位置形式**新**所配置的記憶體。 例如:   
  
```  
// C4291.cpp  
// compile with: /EHsc /W1  
#include <malloc.h>  
  
class CList  
{  
public:  
   CList(int)  
   {  
      throw "Fail!";  
   }  
};  
  
void* operator new(size_t size, char* pszFilename, int nLine)  
{  
   return malloc(size);  
}  
  
int main(void)  
{  
   try  
   {  
      // This will call ::operator new(unsigned int) to allocate heap  
      // memory. Heap memory pointed to by pList1 will automatically be  
      // deallocated by a call to ::operator delete(void*) when  
      // CList::CList(int) throws an exception.  
      CList* pList1 = new CList(10);  
   }  
   catch (...)  
   {  
   }  
  
   try  
   {  
      // This will call the overloaded ::operator new(size_t, char*, int)  
      // to allocate heap memory. When CList::CList(int) throws an  
      // exception, ::operator delete(void*, char*, int) should be called  
      // to deallocate the memory pointed to by pList2. Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291  
   }  
   catch (...)  
   {  
   }  
}  
```  
  
 上述範例會產生警告 C4291 因為運算子的任何位置形式**刪除**已經定義了符合運算子的位置形式**新**。 若要解決此問題，下列程式碼插入至上述**主要**。 請注意，所有多載運算子**刪除**函式的參數符合多載運算子**新**，除了第一個參數。  
  
```  
void operator delete(void* pMem, char* pszFilename, int nLine)  
{  
   free(pMem);  
}  
```