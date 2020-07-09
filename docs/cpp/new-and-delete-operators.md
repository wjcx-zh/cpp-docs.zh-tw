---
title: new 和 delete 運算子
description: C + + 語言的 new 和 delete 運算子允許對配置進行控制。
ms.date: 07/07/2020
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.openlocfilehash: e609d1fdbd4f945ab8709c554d1396100027c4c1
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127856"
---
# <a name="new-and-delete-operators"></a>`new` 和 `delete` 運算子

C + + 支援使用和運算子來動態配置和解除配置物件 [`new`](new-operator-cpp.md) [`delete`](delete-operator-cpp.md) 。 這些運算子會從稱為可用儲存區的集區配置物件的記憶體。 **`new`** 運算子會呼叫特殊函式 [`operator new`](new-operator-cpp.md) ，而 **`delete`** 運算子會呼叫特殊函數 [`operator delete`](delete-operator-cpp.md) 。

**`new`** C + + 標準程式庫中的函式支援 c + + 標準中指定的行為， `std::bad_alloc` 如果記憶體配置失敗，則會擲回例外狀況。 如果您仍然想要的非擲回版本 **`new`** ，請將您的程式與連結 *`nothrownew.obj`* 。 不過，當您使用連結時 *`nothrownew.obj`* ， **`operator new`** c + + 標準程式庫中的預設值將不再有作用。

如需 C 執行時間程式庫和 c + + 標準程式庫中的程式庫檔案清單，請參閱[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。

## <a name="the-new-operator"></a><a id="new_operator"> </a> `new` 運算子

編譯器會將這類語句轉譯為函式呼叫 **`operator new`** ：

```cpp
char *pch = new char[BUFFER_SIZE];
```

如果要求是針對零位元組的儲存體，則會傳回 **`operator new`** 不同物件的指標。 也就是，重複呼叫以傳回 **`operator new`** 不同的指標。 如果配置要求的記憶體不足，則會擲回 **`operator new`** `std::bad_alloc` 例外狀況。 或者， **`nullptr`** 如果您已連結非擲回支援，它會傳回 **`operator new`** 。

您可以撰寫嘗試釋放記憶體的常式，並重試配置。 如需詳細資訊，請參閱 [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md)。 如需修復配置的詳細資訊，請參閱[處理記憶體不足](#handling-insufficient-memory)一節。

下表說明函式的兩個範圍 **`operator new`** 。

### <a name="scope-for-operator-new-functions"></a>函數的範圍 `operator new`

| 運算子 | 影響範圍 |
|--|--|
| **`::operator new`** | 全球 |
| *類別名稱***`::operator new`** | 類別 |

的第一個引數 **`operator new`** 必須是類型 `size_t` （定義于中 \<stddef.h> ），而且傳回類型一律為 **`void*`** 。

**`operator new`** 當 **`new`** 運算子用來配置內建類型的物件、不包含使用者定義函數之類別類型的物件， **`operator new`** 以及任何類型的陣列時，會呼叫全域函數。 當 **`new`** 運算子用來配置已定義之類別類型的物件時 **`operator new`** ，會呼叫該類別的 **`operator new`** 。

**`operator new`** 針對類別定義的函式是靜態成員函式（不能是虛擬的），它會隱藏 **`operator new`** 該類別類型之物件的全域函式。 請考慮 **`new`** 用來配置記憶體並將其設定為指定值的案例：

```cpp
#include <malloc.h>
#include <memory.h>

class Blanks
{
public:
    Blanks(){}
    void *operator new( size_t stAllocateBlock, char chInit );
};
void *Blanks::operator new( size_t stAllocateBlock, char chInit )
{
    void *pvTemp = malloc( stAllocateBlock );
    if( pvTemp != 0 )
        memset( pvTemp, chInit, stAllocateBlock );
    return pvTemp;
}
// For discrete objects of type Blanks, the global operator new function
// is hidden. Therefore, the following code allocates an object of type
// Blanks and initializes it to 0xa5
int main()
{
   Blanks *a5 = new(0xa5) Blanks;
   return a5 != 0;
}
```

括弧中提供的引數 **`new`** 會傳遞至 `Blanks::operator new` 做為 `chInit` 引數。 不過，全域函式 **`operator new`** 是隱藏的，導致下列程式碼產生錯誤：

```cpp
Blanks *SomeBlanks = new Blanks;
```

編譯器支援類別宣告中的成員陣列 **`new`** 和 **`delete`** 運算子。 例如：

```cpp
class MyClass
{
public:
   void * operator new[] (size_t)
   {
      return 0;
   }
   void   operator delete[] (void*)
   {
   }
};

int main()
{
   MyClass *pMyClass = new MyClass[5];
   delete [] pMyClass;
}
```

### <a name="handling-insufficient-memory"></a>處理記憶體不足

測試失敗的記憶體配置可以完成，如下所示：

```cpp
#include <iostream>
using namespace std;
#define BIG_NUMBER 100000000
int main() {
   int *pI = new int[BIG_NUMBER];
   if( pI == 0x0 ) {
      cout << "Insufficient memory" << endl;
      return -1;
   }
}
```

還有另一種方式可以處理失敗的記憶體配置要求。 撰寫自訂的修復常式來處理這類失敗，然後藉由呼叫執行時間函式來註冊您的函數 [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md) 。

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> `delete` 運算子

使用運算子動態配置的記憶體 **`new`** 可以使用 **`delete`** 運算子釋放。 Delete 運算子會呼叫 **`operator delete`** 函數，將記憶體釋放回可用的集區。 使用 **`delete`** 運算子也會呼叫類別析構函式（如果有的話）。

有全域和類別範圍的函式 **`operator delete`** 。 指定的類別只能定義一個函式 **`operator delete`** ，如果已定義，則會隱藏全域 **`operator delete`** 函數。 **`operator delete`** 針對任何類型的陣列，一律會呼叫全域函數。

全域 **`operator delete`** 函數。 全域 **`operator delete`** 和類別成員函式有兩種形式 **`operator delete`** ：

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

針對指定的類別，只有上述兩種形式的其中一種可以存在。 第一個表單採用類型的單一引數 **`void *`** ，其中包含要解除配置的物件指標。 第二個表單（調整大小的解除配置）採用兩個引數：第一個是要解除配置的記憶體區塊指標，而第二個是要解除配置的位元組數目。 這兩種形式的傳回類型為 **`void`** （ **`operator delete`** 無法傳回值）。

第二種形式的目的是要加速搜尋要刪除之物件的正確大小類別目錄。 這種資訊通常不會儲存在配置本身附近，而且可能會進行快取。 當來自基類的函式 **`operator delete`** 用來刪除衍生類別的物件時，第二種形式會很有用。

函式 **`operator delete`** 是靜態的，因此不能是虛擬的。 函 **`operator delete`** 式會遵守存取控制，如[成員存取控制](member-access-control-cpp.md)中所述。

下列範例會顯示 **`operator new`** **`operator delete`** 設計用來記錄配置和記憶體取消配置的使用者定義和函數：

```cpp
#include <iostream>
using namespace std;

int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?
int cBlocksAllocated = 0;  // Count of blocks allocated.

// User-defined operator new.
void *operator new( size_t stAllocateBlock ) {
   static int fInOpNew = 0;   // Guard flag.

   if ( fLogMemory && !fInOpNew ) {
      fInOpNew = 1;
      clog << "Memory block " << ++cBlocksAllocated
          << " allocated for " << stAllocateBlock
          << " bytes\n";
      fInOpNew = 0;
   }
   return malloc( stAllocateBlock );
}

// User-defined operator delete.
void operator delete( void *pvMem ) {
   static int fInOpDelete = 0;   // Guard flag.
   if ( fLogMemory && !fInOpDelete ) {
      fInOpDelete = 1;
      clog << "Memory block " << cBlocksAllocated--
          << " deallocated\n";
      fInOpDelete = 0;
   }

   free( pvMem );
}

int main( int argc, char *argv[] ) {
   fLogMemory = 1;   // Turn logging on
   if( argc > 1 )
      for( int i = 0; i < atoi( argv[1] ); ++i ) {
         char *pMem = new char[10];
         delete[] pMem;
      }
   fLogMemory = 0;  // Turn logging off.
   return cBlocksAllocated;
}
```

上述程式碼可用來偵測「記憶體流失」，也就是在免費存放區上配置但從未釋放的記憶體。 若要偵測流失，全域 **`new`** 和 **`delete`** 運算子會重新定義，以計算記憶體的配置和解除配置。

編譯器支援類別宣告中的成員陣列 **`new`** 和 **`delete`** 運算子。 例如：

```cpp
// spec1_the_operator_delete_function2.cpp
// compile with: /c
class X  {
public:
   void * operator new[] (size_t) {
      return 0;
   }
   void operator delete[] (void*) {}
};

void f() {
   X *pX = new X[5];
   delete [] pX;
}
```
