---
title: 新和 delete 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- delete_cpp
- new
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++], dynamic allocation of objects
- nothrownew.obj
- delete keyword [C++], syntax
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb8f04962593dff13559f49f7f7c23014968c266
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940756"
---
# <a name="new-and-delete-operators"></a>new 和 delete 運算子

C + + 支援動態配置和解除配置的物件使用[新](../cpp/new-operator-cpp.md)並[刪除](../cpp/delete-operator-cpp.md)運算子。 這些運算子會從稱為可用儲存區的集區配置物件的記憶體。 **新**運算子會呼叫特殊函式[new 運算子](../cpp/new-operator-cpp.md)，而**刪除**運算子會呼叫特殊函式[運算子 delete](../cpp/delete-operator-cpp.md).  
  
 **新**c + + 標準程式庫中的函式支援 c + + 標準，也就是如果記憶體配置失敗，會擲回 std:: bad_alloc 例外狀況中所指定的行為。 如果您仍然希望非擲回版本**新**，連結您的程式與 nothrownew.obj 連結。不過，當您連結 nothrownew.obj 時，預設值**new 運算子**c + + 標準程式庫中無法再運作。  
  
 如需包含 C 執行階段程式庫和 c + + 標準程式庫的程式庫檔案的清單，請參閱 < [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。  
  
##  <a id="new_operator"> </a> New 運算子  
 在程式中發生如下的陳述式時，就會轉譯成呼叫的函式**new 運算子**:  
  
```cpp  
char *pch = new char[BUFFER_SIZE];  
```  
  
如果要求零位元組的儲存體**new 運算子**相異的物件傳回的指標 (也就是說，重複呼叫**new 運算子**傳回不同的指標)。 如果沒有足夠的記憶體配置要求，如**new 運算子**擲回 std:: bad_alloc 例外狀況或傳回**nullptr**如果您已連結在非擲回**new 運算子**支援。  
  
您可以撰寫常式，它會嘗試釋放記憶體，然後重試配置，;請參閱[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)如需詳細資訊。 如需復原配置的詳細資訊，請參閱本主題的處理記憶體不足，無法一節。  

  
兩個範圍**new 運算子**函式下表中所述。  
  
### <a name="scope-for-operator-new-functions"></a>operator new 函式的範圍  
  
|運算子|範圍|  
|--------------|-----------|  
|**:: new 運算子**|Global|  
|*類別名稱* **:: new 運算子**|類別|  
  
 第一個引數**new 運算子**必須是型別`size_t`(中定義的類型\<stddef.h >)，而且傳回型別一律**void \*** 。  
  
 全域**new 運算子**函式時，會呼叫**新**運算子用於配置內建類型的物件、 類別類型的物件不包含使用者定義**new 運算子**函式，以及任何類型的陣列。 當**新**運算子用來配置的類別類型物件其中**new 運算子**定義，該類別的**運算子 new**稱為。  
  
 **New 運算子**函式中定義的類別是靜態成員函式 （因此不可為虛擬），會隱藏全域**new 運算子**函式，該類別類型的物件。 假設其中**新**用來配置，並將記憶體設定為指定的值：  
  
```cpp  
// spec1_the_operator_new_function1.cpp  
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
  
 括號，以提供的引數**新**傳遞至`Blanks::operator new`做為`chInit`引數。 不過，全域**new 運算子**函式已隱藏，因此造成程式碼，如下所示，會產生錯誤：  
  
```cpp  
Blanks *SomeBlanks = new Blanks;  
```  
  
 在 Visual c + + 5.0 和以前版本中，非類別類型和所有陣列 (無論是否**類別**類型) 使用配置**新**運算子一律使用全域**new 運算子**函式。  
  
 從 Visual c + + 5.0 開始，編譯器支援成員陣列**新**並**刪除**類別宣告中的運算子。 例如:   
  
```cpp  
// spec1_the_operator_new_function2.cpp  
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
 您可以使用如下所示的程式碼測試失敗的記憶體配置：  
  
```cpp  
// insufficient_memory_conditions.cpp  
// compile with: /EHsc  
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
  
 還有另一個方式來處理記憶體配置要求失敗： 撰寫自訂的復原常式來處理此類錯誤，然後藉由呼叫註冊您的函式[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)執行階段函式。  
  
##  <a id="delete_operator"> </a> Delete 運算子  
 會使用動態配置的記憶體**新**操作員可以使用釋放**刪除**運算子。 Delete 運算子會呼叫**運算子 delete**函式，這樣會釋放回可用的集區的記憶體。 使用**刪除**運算子也會使類別解構函式 （如果有的話） 來呼叫。  
  
 有全域和類別範圍**運算子 delete**函式。 只有一個**delete 運算子**函式可以針對特定的類別定義，如果有定義，則會隱藏全域**運算子 delete**函式。 全域**運算子 delete**函式一定會呼叫任何類型的陣列。  
  
 全域**運算子 delete**函式。 兩種形式存在的全域**delete 運算子**和類別成員**運算子 delete**函式：  
  
```cpp  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 只有其中一個前述的兩種形式可以表示特定類別。 第一種形式接受單一引數的型別**void \***，其中包含要解除配置物件的指標。 第二種形式，調整大小解除配置，會採用兩個引數，其中的第一個是解除配置之記憶體區塊指標，且其中的第二個是要解除配置的位元組數目。 這兩種形式的傳回型別是**void** (**運算子 delete**無法傳回值)。  
  
 第二種形式的目的是加速搜尋要刪除之物件的正確大小類別通常不儲存在本身的配置附近且可能取消快取;第二種形式時特別有用**運算子 delete**從基底類別的函數用來刪除衍生類別的物件。  
  
 **運算子 delete**函式為靜態，因此無法為虛擬。 `operator delete`函式中所述，請遵守存取控制[成員存取控制](../cpp/member-access-control-cpp.md)。  
  
 下列範例示範使用者定義**new 運算子**並**運算子 delete**旨在記錄配置和取消配置的記憶體的函式：  
  
```cpp  
// spec1_the_operator_delete_function1.cpp  
// compile with: /EHsc  
// arguments: 3  
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
  
 上述程式碼可用來偵測「記憶體流失」，即是在可用存放區中配置但從未釋放的記憶體。 若要執行此偵測中，全域**新**並**刪除**計數配置和解除配置的記憶體來重新定義運算子。  
  
 從 Visual c + + 5.0 開始，編譯器支援成員陣列**新**並**刪除**類別宣告中的運算子。 例如:   
  
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

