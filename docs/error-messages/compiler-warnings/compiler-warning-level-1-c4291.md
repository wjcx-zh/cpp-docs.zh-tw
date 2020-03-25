---
title: 編譯器警告 (層級 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: cd161a37683703fd67b4c682558a51121c130816
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175710"
---
# <a name="compiler-warning-level-1-c4291"></a>編譯器警告 (層級 1) C4291

' 宣告 '：找不到相符的運算子 delete;如果初始化擲回例外狀況，則不會釋放記憶體

[放置[新](../../cpp/new-operator-cpp.md)的] 是用於沒有放置[刪除](../../cpp/delete-operator-cpp.md)的位置。

針對具有 operator **new**的物件配置記憶體時，會呼叫該物件的函式。 如果此函式擲回例外狀況，則配置給物件的任何記憶體都應該解除配置。 除非符合運算子**new**的運算子**delete**函式存在，否則無法進行此操作。

如果您使用不含任何額外引數的運算子**new** ，並使用[/gx](../../build/reference/gx-enable-exception-handling.md)、 [/ehs](../../build/reference/eh-exception-handling-model.md)或/eha 選項進行編譯以啟用例外狀況處理，則編譯器會產生程式碼，以便在此函式擲回例外狀況時呼叫 operator **delete** 。

如果您使用**new**運算子的放置形式（除了配置大小之外還有引數的表單），而且物件的函式會擲回例外狀況，則編譯器仍然會產生呼叫 operator **delete**的程式碼;但是，如果運算子**delete**的放置形式與配置記憶體的運算子**new**的放置形式相符，它就只會這麼做。 例如：

```cpp
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

上述範例會產生警告 C4291，因為未定義任何位置形式的運算子**delete** ，以符合 operator **new**的放置形式。 若要解決此問題，請將下列程式碼插入到**main**上面。 請注意，除了第一個參數以外，所有多載運算子**delete**函數參數都符合多載運算子**new**的。

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
