---
title: "編譯器警告 (層級 1) C4291 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4291"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4291"
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4291
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaration' : 找不到相符的 delete 運算子; 如果初始化過程中擲回例外狀況，將無法釋出記憶體  
  
 有使用 [new](../../cpp/new-operator-cpp.md) 位置但是沒有 [delete](../../cpp/delete-operator-cpp.md) 位置。  
  
 當使用 **new** 運算子為物件配置記憶體時，該物件的建構函式會被呼叫。  如果該建構函式擲回一個例外狀況，任何為該物件配置的記憶體都應該被解除配置。  這種狀況將不會發生，除非有和 **new** 運算子搭配的 **delete** 運算子函式。  
  
 如果您用運算子 **new** 而不加任何多餘的引數，並用 [\/GX](../../build/reference/gx-enable-exception-handling.md)、[\/EHs](../../build/reference/eh-exception-handling-model.md) 或 \/EHa 選項編譯以啟用例外處理，當建構函式擲回例外狀況時，編譯器會產生程式碼呼叫運算子 **delete**。  
  
 如果您使用位置形式的 **new** 運算子 \(除了配置大小的引數外還有其他引數的形式\)，而且物件的建構函式擲回例外狀況，編譯器還是會產生呼叫運算子 **delete** 的程式碼，但是它只會在有和配置記憶體的運算子 **new** 搭配的運算子 **delete** 存在時這麼做。  例如：  
  
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
  
 上述範例會產生警告 C4291，因為沒有定義和運算子 **new** 位置形式搭配的運算子 **delete** 的位置形式。  若要解決此問題，將下列程式碼插入到 **main** 的上面。  請注意，所有多載運算子 **delete** 函式的參數都和多載運算子 **new** 的參數相符，除了第一個參數之外。  
  
```  
void operator delete(void* pMem, char* pszFilename, int nLine)  
{  
   free(pMem);  
}  
```