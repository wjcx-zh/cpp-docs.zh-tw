---
title: new 和 delete 運算子
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: 2fd665ce2570bbe7750684057cdf7f517f6f64f3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445453"
---
# <a name="new-and-delete-operators"></a>new 和 delete 運算子

C++支援使用[new](new-operator-cpp.md)和[delete](delete-operator-cpp.md)運算子進行物件的動態配置和解除配置。 這些運算子會從稱為可用儲存區的集區配置物件的記憶體。 **New**運算子會呼叫特殊函數[operator new](new-operator-cpp.md)，而**delete**運算子會呼叫特殊函數[運算子 delete](delete-operator-cpp.md)。

標準程式庫中的**新**函式支援C++標準中指定的行為，如果記憶體配置失敗，則會擲回 std：： bad_alloc 例外狀況。 C++ 如果您仍然想要使用非擲回版本的**new**，請將您的程式與 nothrownew.obj 連結。不過，當您使用 nothrownew.obj 連結時， C++標準程式庫中的預設**operator new**將不再有作用。

如需組成 C 執行時間程式庫和C++標準程式庫的程式庫檔案清單，請參閱 CRT 連結[庫功能](../c-runtime-library/crt-library-features.md)。

##  <a id="new_operator"> </a> New 運算子

當程式中遇到下列這類語句時，它會轉譯為**函式 operator new**的呼叫：

```cpp
char *pch = new char[BUFFER_SIZE];
```

如果要求是針對零位元組的儲存體， **operator new**會傳回不同物件的指標（也就是重複呼叫**operator new**會傳回不同的指標）。 如果配置要求的記憶體不足， **operator new**會擲回 `std::bad_alloc` 例外狀況，或如果您已在非擲回**運算子的新**支援中連結，則會傳回**nullptr** 。

您可以撰寫嘗試釋放記憶體的常式，並重試配置;如需詳細資訊，請參閱[_set_new_handler](../c-runtime-library/reference/set-new-handler.md) 。 如需有關復原配置的詳細資訊，請參閱本主題中的處理記憶體不足一節。

下表說明**operator new 函**式的兩個範圍。

### <a name="scope-for-operator-new-functions"></a>Operator new 函式的範圍

|運算子|影響範圍|
|--------------|-----------|
|**：： operator new**|全域|
|*類別名稱* **：： operator new**|類別|

**Operator new**的第一個引數必須是 `size_t` 類型（在 \<> stddef.h 中定義的類型），而且傳回類型一律為**void** <strong>\*</strong>。

當**new**運算子用於配置內建類型的物件、不包含使用者定義的**運算子新函**式之類別類型的物件，以及任何類型的陣列時，會呼叫全域**operator new 函**式。 當使用**new**運算子來配置定義了**operator new**的類別類型物件時，就會呼叫該類別的**operator new** 。

針對類別定義的**operator new 函**式是靜態成員函式（因此不可為虛擬），它會針對該類別類型的物件隱藏全域**operator new 函**式。 請考慮使用**new**來配置記憶體，並將其設定為指定值的情況：

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

在括弧中提供給**new**的引數會傳遞給 `Blanks::operator new` 做為 `chInit` 引數。 不過，全域**operator new 函**式是隱藏的，導致下列程式碼產生錯誤：

```cpp
Blanks *SomeBlanks = new Blanks;
```

編譯器支援類別宣告中的成員陣列**new**和**delete**運算子。 例如：

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

還有另一種方式可以處理失敗的記憶體配置要求。 撰寫自訂的修復常式來處理這類失敗，然後藉由呼叫[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)執行時間函式來註冊您的函數。

##  <a id="delete_operator"> </a> Delete 運算子

使用**new**運算子動態配置的記憶體可以使用**delete**運算子釋放。 Delete 運算子會呼叫**operator delete 函**式，將記憶體釋放回可用的集區。 使用**delete**運算子也會導致呼叫類別的析構函式（如果有的話）。

有全域和類別範圍的**運算子 delete 函**式。 只能為指定的類別定義一個**operator delete 函**式;如果已定義，則會隱藏全域**operator delete 函**式。 針對任何類型的陣列，一律會呼叫全域**operator delete 函**式。

全域**operator delete 函**式。 全域**operator delete**和類別成員**運算子 delete 函**式有兩種形式：

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

針對指定的類別，只有上述兩種形式的其中一種可以存在。 第一個表單接受 `void *`類型的單一引數，其中包含要解除配置的物件指標。 第二種形式（調整大小的解除配置）採用兩個引數，第一個是要解除配置的記憶體區塊指標，而第二個是要解除配置的位元組數目。 這兩種形式的傳回型別都是**void** （**operator delete**無法傳回值）。

第二種形式的目的是要加速搜尋要刪除之物件的正確大小類別目錄，這通常不會儲存在配置本身附近，而且可能會進行快取。 當來自基類的**operator delete 函**式用來刪除衍生類別的物件時，第二種形式會很有用。

**Operator delete 函**式是靜態的;因此，它不能是虛擬的。 **運算子 delete 函**式會遵守存取控制，如[成員存取控制](member-access-control-cpp.md)中所述。

下列範例會示範使用者定義的**operator new**和**運算子 delete 函**式，這些函數是設計來記錄記憶體的配置和取消配置：

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

上述程式碼可用來偵測「記憶體流失」，即是在可用存放區中配置但從未釋放的記憶體。 若要執行這項偵測，會重新定義全域**new**和**delete**運算子，以計算記憶體的配置和解除配置。

編譯器支援類別宣告中的成員陣列**new**和**delete**運算子。 例如：

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
