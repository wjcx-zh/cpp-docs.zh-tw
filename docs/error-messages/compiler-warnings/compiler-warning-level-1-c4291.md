---
title: 編譯器警告 (層級 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c1972236e30be4e6ca738b606b00398f5c7860e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754862"
---
# <a name="compiler-warning-level-1-c4291"></a>編譯器警告 (層級 1) C4291

"聲明":未找到匹配的運算符刪除;如果初始化引發異常,則不會釋放記憶體

使用沒有放置[刪除](../../cpp/delete-operator-cpp.md)的[放置新](../../cpp/new-operator-cpp.md)放置。

當為具有運算符**new**的物件分配記憶體時,將調用物件的構造函數。 如果構造函數引發異常,則為物件分配的任何記憶體都應處理。 除非存在與運算符**new**匹配的運算符**刪除**函數,否則無法執行此操作。

如果使用運算符**new**而不提供任何額外的參數,並使用[/GX](../../build/reference/gx-enable-exception-handling.md) [、/EHs](../../build/reference/eh-exception-handling-model.md)或 /EHa 選項編譯以啟用異常處理,則編譯器將生成代碼,以便在建構函數引發異常時調用運算符**刪除**。

如果使用**新**運算子的放置形式(除了分配大小之外帶有參數的窗體),並且物件的建構函數引發異常,編譯器仍將生成代碼來呼叫運算符**刪除**;但只有在運算符**刪除**的放置窗體與分配記憶體的運算元**的新**放置形式匹配時,才會執行此操作。 例如：

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

上述示例生成警告 C4291,因為未定義與運算符**new**的放置形式匹配的運算符**刪除**放置形式。 要解決此問題,請在**主**上插入以下代碼。 請注意,除第一個參數外,所有重載運算符**刪除**函數參數都與重載運算符**new**的函數參數匹配。

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
