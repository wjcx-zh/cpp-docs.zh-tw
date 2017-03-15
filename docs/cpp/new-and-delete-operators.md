---
title: "new 和 delete 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "delete_cpp"
  - "new_cpp"
  - "new"
  - "delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delete 關鍵字 [C++], 語法"
  - "new 關鍵字 [C++], 物件的動態配置"
  - "nothrownew.obj"
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# new 和 delete 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 使用 [new](../cpp/new-operator-cpp.md) 和 [delete](../cpp/delete-operator-cpp.md) 運算子支援物件的動態配置與解除配置。  這些運算子會從稱為可用儲存區的集區配置物件的記憶體。  `new` 運算子會呼叫特殊函式 [operator new](../misc/operator-new-function.md)，而 `delete` 運算子則會呼叫特殊函式 [operator delete](../misc/operator-delete-function.md)。  
  
 在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] .NET 2002 中，Standard C\+\+ 程式庫中的 `new` 函式會支援 C\+\+ 標準指定的行為，也就是在記憶體配置失敗時擲回 std::bad\_alloc 例外狀況。  
  
 如果記憶體配置失敗，C 執行階段程式庫的 `new` 函式也會擲回 std::bad\_alloc 例外狀況。  
  
 如果您仍然希望 C 執行階段程式庫使用非擲回版本的 `new`，請將您的程式與 nothrownew.obj 連結。  不過，當您連結 nothrownew.obj 時，Standard C\+\+ 程式庫中的 `new` 將不再有作用。  
  
 如需包含 C 執行階段程式庫和 Standard C\+\+ 程式庫的程式庫檔案清單，請參閱 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。  
  
## new 運算子  
 在程式中遇到下面這類陳述式時，陳述式就會轉譯成 `operator new` 函式的呼叫：  
  
```  
char *pch = new char[BUFFER_SIZE];  
```  
  
 如果是要求零位元組的儲存區，則 **operator new** 會傳回不同物件的指標 \(也就是說，重複呼叫 **operator new** 會傳回不同的指標\)。  如果記憶體不足無法用於配置要求，則 **operator new** 會傳回 **NULL** 或擲回例外狀況 \(如需詳細資訊，請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)\)。  
  
 您可以撰寫常式，嘗試釋放記憶體並重試配置。如需詳細資訊，請參閱 [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)。  如需復原配置的詳細資訊，請參閱下列主題[處理記憶體不足的情況](../misc/handling-insufficient-memory-conditions.md)。  
  
 下表描述 `operator new` 函式的兩個範圍。  
  
### operator new 函式的範圍  
  
|運算子|範圍|  
|---------|--------|  
|**::operator new**|全域|  
|*class\-name* **::operator new**|類別|  
  
 **operator new** 的第一個引數必須屬於 **size\_t** 類型 \(在 STDDEF.H 中定義的類型\)，而且傳回類型一律為 **void \***。  
  
 全域 **operator new** 函式是在 **new** 運算子用於配置內建類型的物件、不包含使用者定義的 **operator new** 函式之類別類型的物件，以及任何類型的陣列時呼叫。  當 **new** 運算子用於配置其中已定義 **operator new** 的類別類型物件時，就會呼叫該類別的 **operator new**。  
  
 為類別定義的 **operator new** 函式為靜態成員函式 \(因此不可為虛擬\)，它會隱藏該類型類別之物件的全域 **operator new** 函式。  假設有 **new** 用來將記憶體配置和設定為特定值的案例：  
  
```  
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
  
 以括號提供給 **new** 的引數會傳遞至 `Blanks::operator new` 做為 `chInit` 引數。  不過，全域 **operator new** 函式已隱藏，因此造成下列程式碼產生錯誤：  
  
```  
Blanks *SomeBlanks = new Blanks;  
```  
  
 在 Visual C\+\+ 5.0 和先前版本中，使用 **new** 運算子配置的非類別類型和所有陣列 \(無論是否屬於 **class** 類型\) 一律使用全域 **operator new** 函式。  
  
 從 Visual C\+\+ 5.0 開始，編譯器在類別宣告中支援成員陣列 **new** 和 **delete** 運算子。  例如:  
  
```  
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
  
### 處理記憶體不足  
 您可以使用如下所示的程式碼測試失敗的記憶體配置：  
  
```  
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
  
 另外一種處理記憶體配置要求失敗的方式是：撰寫自訂的復原常式來處理這類的失敗，然後呼叫 [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md) 執行階段函式來註冊您的函式。  
  
## delete 運算子  
 使用 **new** 運算子動態配置的記憶體可以使用 **delete** 運算子加以釋放。  delete 運算子會呼叫 **operator delete** 函式，該函式會將記憶體釋放回可用的集區。  使用 **delete** 運算子也會呼叫類別解構函式 \(如果有的話\)。  
  
 **operator delete** 函式有全域範圍和類別範圍。  特定類別只能定義一個 **operator delete** 函式，如果已定義，則會隱藏全域 **operator delete** 函式。  任何類型的陣列一定會呼叫全域 **operator delete** 函式。  
  
 如果宣告全域 **operator delete** 函式，則會採用類型為 **void \*** 的單一引數，表示其中包含要解除配置的物件指標。  傳回類型為 `void` \(**operator delete** 無法傳回值\)。  類別成員 **operator delete** 函式存在兩種形式：  
  
```  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 特定類別只能存在前兩個變數的其中一個。  第一種形式的運作方式如針對全域 `operator delete` 所述。  第二種形式接受兩個引數，第一個是解除配置記憶體區塊的指標，第二個是要解除配置的位元組數目。  使用來自基底類別的 **operator delete** 函式刪除衍生類別的物件時，第二種形式特別有用。  
  
 **operator delete** 為靜態函式，因此不能為虛擬。  `operator delete` 函式會遵守存取控制項，如[成員存取控制](../cpp/member-access-control-cpp.md)中所述。  
  
 下列範例說明使用者定義的 **operator new** 和 **operator delete** 函式，這兩個函式是針對記錄記憶體的配置和解除配置所設計：  
  
```  
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
  
 上述程式碼可用來偵測「記憶體流失」，即是在可用存放區中配置但從未釋放的記憶體。  要執行此項偵測時會重新定義全域 **new** 和 **delete** 運算子以計算記憶體的配置和解除配置。  
  
 從 Visual C\+\+ 5.0 開始，編譯器在類別宣告中支援成員陣列 **new** 和 **delete** 運算子。  例如:  
  
```  
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
  
## 請參閱  
 [特殊成員函式](../misc/special-member-functions-cpp.md)