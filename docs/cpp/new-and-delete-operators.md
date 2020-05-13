---
title: new 和 delete 運算子
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: fd170c1500e2d80879fdd89f7d825930189ae942
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367879"
---
# <a name="new-and-delete-operators"></a>new 和 delete 運算子

C++支援使用[新的](new-operator-cpp.md)運算子和[刪除](delete-operator-cpp.md)運算元動態分配和分配物件。 這些運算子會從稱為可用儲存區的集區配置物件的記憶體。 **新增**運算子呼叫特殊函數運算符[new](new-operator-cpp.md),**刪除**運算子呼叫特殊函數[運算子刪除](delete-operator-cpp.md)。

C++標準庫中**的新功能**支援C++標準中指定的行為,即如果記憶體分配失敗,則引發std::bad_alloc異常。 如果您仍想要**新版本的**非引發版本,請將程式連結到 nothrownew.obj。但是,當您連結到 nothrownew.obj 時,C++標準庫中**的默認運算符**不再正常工作。

有關構成 C 執行時庫和 C++標準函式庫的庫檔案的清單,請參考[CRT 函式庫功能](../c-runtime-library/crt-library-features.md)。

## <a name="the-new-operator"></a><a id="new_operator"> </a>新運算子

當程式中遇到如下語句時,它將轉換為對函數**運算符 new**的呼叫:

```cpp
char *pch = new char[BUFFER_SIZE];
```

如果請求為零位元組的儲存,**則運算符 new**傳回指向不同物件的指標(即,對**運算元的新**重複呼叫返回不同的指標)。 如果分配請求記憶體不足,**則運算符 new**會引發`std::bad_alloc`異常 ,或者如果已連結在非引發**運算符新**支援中,則返回**nullptr。**

您可以編寫一個例程,嘗試釋放記憶體並重試分配;有關詳細資訊[,請參閱_set_new_handler。](../c-runtime-library/reference/set-new-handler.md) 有關恢復方案的更多詳細資訊,請參閱本主題的"處理記憶體不足"部分。

**下表描述了運算符新功能**的兩個作用域。

### <a name="scope-for-operator-new-functions"></a>操作者新功能的範圍

|運算子|影響範圍|
|--------------|-----------|
|**:: 運算子新**|全域|
|*類別***名稱 ::運算子**|類別|

**運算子 new**的第一個參數必須`size_t`為 型態(在 stddef.h>中\<定義的類型),並且傳回類型始終**為空**<strong>\*</strong>。

使用**新**運算子分配內建型態的物件、不包含使用者定義的**運算元新**函式的類別物件以及任何類型的陣列時,將呼叫全域**運算子新功能**。 當**新**運算元用於分配定義**運算符 new**的類類型的物件時,將調用該類的**運算符 new。**

為類定義的**運算符新**函數是一個靜態成員函數(因此,它不能是虛擬的),它隱藏該類類型物件的全域**運算符新**函數。 考慮使用**new**將記憶體配置和設定為給定值的情況:

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

以括弧提供給**new**的`Blanks::operator new``chInit`參數作為 參數傳遞給。 但是,全域**運算子新**函數被隱藏,導致以下代碼產生錯誤:

```cpp
Blanks *SomeBlanks = new Blanks;
```

編譯器支援類聲明中**的新**成員陣列**和刪除**運算符。 例如：

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

可以測試失敗的記憶體分配,如下所示:

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

還有另一種方法來處理失敗的記憶體分配請求。 編寫自定義恢復例程來處理此類故障,然後通過調用[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)運行時函數來註冊函數。

## <a name="the-delete-operator"></a><a id="delete_operator"> </a>刪除運算子

可以使用**delete**運算符釋放使用**新**運算元動態分配的記憶體。 刪除運算符呼叫**運算符刪除**函數,該函數將記憶體釋放回可用池。 使用**delete**運算元還會導致調用類析構函數(如果有)。

有全域和類作用域**運算符刪除**函數。 只能為給定類定義一個**運算符刪除**函數;如果已定義,它將隱藏全域**運算符刪除**函數。 對於任何類型的陣列,始終調用全域**運算符刪除**函數。

全域**運算符刪除**函數。 全域**運算子移除**與類別成員**運算子刪除**函數存在兩種形式:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

給定類只能存在前兩個窗體中的一個。 第一個表單個表單`void *`型參數,其中包含指向要解調的對象的指標。 第二種形式(大小處理)採用兩個參數,第一個參數是指向要解分配的記憶體塊的指標,第二個參數是要解調的位元數。 兩種形式的傳回**型態無效(****運算符刪除**不能返回值)。

第二個表單的目的是加快搜索要刪除的物件的正確大小類別,該類別通常不儲存在分配本身附近,並且可能未緩存。 當運算符從基類**中刪除**函數用於刪除派生類的物件時,第二個窗體很有用。

**運算符刪除**函數是靜態的;因此,它不能是虛擬的。 **運算子刪除**函數遵循訪問控制,如[成員訪問控制](member-access-control-cpp.md)中所述。

下面的範例顯示使用者定義的**運算子新的**與**運算子刪除**旨在記錄記憶體分配和分配位置的功能:

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

上述程式碼可用來偵測「記憶體流失」，即是在可用存放區中配置但從未釋放的記憶體。 要執行此檢測,將重新定義**new**全域新**運算子和刪除**運算符,以計數記憶體的分配和分配。

編譯器支援類聲明中**的新**成員陣列**和刪除**運算符。 例如：

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
