---
title: "new 運算子 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "new 關鍵字 [C++]"
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# new 運算子 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從可用存放區針對 *type\-name* 的物件或物件陣列配置記憶體，並傳回適用類型、非零物件指標。  
  
> [!NOTE]
>  Microsoft C\+\+ 元件擴充功能會提供對 `new` 關鍵字的支援以加入 vtable 位置項目。  如需詳細資訊，請參閱 [new \(new slot in vtable\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)。  
  
## 語法  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## 備註  
 如果不成功，**new** 會傳回零或擲回例外狀況；請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)以取得詳細資訊。  您可以變更這個預設行為，作法是撰寫自訂例外狀況處理常式，並將您的函式名稱當做引數來呼叫 [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md) 執行階段程式庫函式。  
  
 如需如何在 Managed 堆積上建立物件的詳細資訊，請參閱 [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)。  
  
 當使用 **new** 來配置 C\+\+ 類別物件的記憶體時，會在配置記憶體之後呼叫物件的建構函式。  
  
 使用 [delete](../cpp/delete-operator-cpp.md) 運算子解除配置以 **new** 運算子配置的記憶體。  
  
 下列範例會先配置然後再釋放大小為 `dim` 乘以 10 個字元的二維陣列。  配置多維陣列時，第一個維度以外的所有維度都必須是判斷值為正值的常數運算式；最左邊的陣列維度可以是任何判斷值為正值的運算式。  使用 **new** 運算子配置陣列時，第一個維度可以是零 \(**new** 運算子會傳回唯一指標\)。  
  
```  
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 *type\-name* 不能包含 **const**、`volatile`、類別宣告或列舉宣告。  因此，下列運算式是不合法的：  
  
```  
volatile char *vch = new volatile char[20];  
```  
  
 **new** 運算子無法配置參考類型，因為這些類型不是物件。  
  
 **new** 運算子無法用來配置函式，但是可以用來配置函式的指標。  下列範例會配置然後再釋放含七個傳回整數之函式指標的陣列。  
  
```  
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 如果您沒有搭配任何額外的引數使用運算子 **new**，並使用 [\/GX](../build/reference/gx-enable-exception-handling.md)、[\/EHa](../build/reference/eh-exception-handling-model.md) 或 [\/EHs](../build/reference/eh-exception-handling-model.md) 選項進行編譯，當建構函式擲回例外狀況時，編譯器將會產生程式碼以呼叫運算子 **delete**。  
  
 下列清單說明 **new** 的文法項目：  
  
 *placement*  
 如果您多載 **new**，可提供您一個傳遞其他引數的方式。  
  
 *type\-name*  
 指定要配置的類型；它可以是內建或使用者定義的類型。  如果類型規格是複雜的，請以括號括住類型規格以強制繫結的順序。  
  
 *initializer*  
 提供初始化物件的值。  初始設定式無法指定給陣列。  **new** 運算子只有在類別具有預設建構函式時，才會建立物件的陣列。  
  
## 範例  
 下列程式碼範例會配置一個字元陣列和一個 `CName` 類別物件，然後加以釋放。  
  
```  
// expre_new_Operator.cpp  
// compile with: /EHsc  
#include <string.h>  
  
class CName {  
public:  
   enum {  
      sizeOfBuffer = 256  
   };  
  
   char m_szFirst[sizeOfBuffer];  
   char m_szLast[sizeOfBuffer];  
  
public:  
   void SetName(char* pszFirst, char* pszLast) {  
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);  
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);  
   }  
  
};  
  
int main() {  
   // Allocate memory for the array  
   char* pCharArray = new char[CName::sizeOfBuffer];  
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");  
  
   // Deallocate memory for the array  
   delete [] pCharArray;             
   pCharArray = NULL;  
  
   // Allocate memory for the object  
   CName* pName = new CName;  
   pName->SetName("Firstname", "Lastname");  
  
   // Deallocate memory for the object  
   delete pName;  
   pName = NULL;  
}  
```  
  
## 範例  
 如果您使用 **new** 運算子的新位置形式 \(即除了配置大小之外，還有其他引數的形式\)，則編譯器不支援可在建構函式擲回例外狀況時使用的位置形式 **delete** 運算子。  例如:  
  
```  
// expre_new_Operator2.cpp  
// C2660 expected  
class A {  
public:  
   A(int) { throw "Fail!"; }  
};  
void F(void) {  
   try {  
      // heap memory pointed to by pa1 will be deallocated  
      // by calling ::operator delete(void*).  
      A* pa1 = new A(10);  
   } catch (...) {  
   }  
   try {  
      // This will call ::operator new(size_t, char*, int).  
      // When A::A(int) does a throw, we should call  
      // ::operator delete(void*, char*, int) to deallocate  
      // the memory pointed to by pa2.  Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
  
      A* pa2 = new(__FILE__, __LINE__) A(20);  
   } catch (...) {  
   }  
}  
  
int main() {  
   A a;  
}  
```  
  
## 初始化以 new 所配置的物件  
 選擇性的 *initializer* 欄位會包含在 **new** 運算子的文法中。  這樣就可讓您以使用者定義的建構函式初始化新物件。  如需如何執行初始化的詳細資訊，請參閱[初始設定式](../cpp/initializers.md)。  下列範例將示範如何使用具有 **new** 運算子的初始化運算式：  
  
```  
// expre_Initializing_Objects_Allocated_with_new.cpp  
class Acct  
{  
public:  
    // Define default constructor and a constructor that accepts  
    //  an initial balance.  
    Acct() { balance = 0.0; }  
    Acct( double init_balance ) { balance = init_balance; }  
private:  
    double balance;  
};  
  
int main()  
{  
    Acct *CheckingAcct = new Acct;  
    Acct *SavingsAcct = new Acct ( 34.98 );  
    double *HowMuch = new double ( 43.0 );  
    // ...  
}  
```  
  
 在這個範例中，`CheckingAcct` 是使用 **new** 運算子所配置，但是未指定預設初始化。  因此會呼叫 `Acct()` 類別的預設建構函式。  然後以相同方式配置 `SavingsAcct` 物件，不過它會明確初始化為 34.98。  由於 34.98 屬於 **double** 類型，因此會呼叫接受該類型引數的建構函式處理初始化。  最後，非類別類型 `HowMuch` 會初始化為 43.0。  
  
 如果物件為類別類型且該類別具有建構函式 \(如上述範例\)，則只有在符合下列其中一項條件時，物件才可以由 **new** 運算子初始化：  
  
-   在初始設定式中提供的引數與建構函式中的引數一致。  
  
-   類別有預設建構函式 \(可以在沒有引數的情況下呼叫的建構函式\)。  
  
 存取控制和語意模糊控制是根據`operator new`語意模糊和[使用特殊成員函式初始化](http://msdn.microsoft.com/zh-tw/0b399cab-40a7-4e79-9278-05f40139a0e1)中訂定的規則，在 [和建構函式上執行。](http://msdn.microsoft.com/zh-tw/82223d73-64cb-4923-b678-78f9568ff3ca)  
  
 使用 **new** 運算子配置陣列時，不可明確執行每個元素的初始化，而只會呼叫預設建構函式 \(如果有的話\)。  如需詳細資訊，請參閱[預設引數](../cpp/default-arguments.md)。  
  
 如果記憶體配置失敗 \(`operator new` 傳回值為 0\)，則不會執行初始化。  這樣可防止嘗試初始化不存在的資料。  
  
 就像函式呼叫一般，不會定義初始化運算式的評估順序。  此外，您不應依賴這些運算式會在執行記憶體配置之前完全評估。  如果記憶體配置失敗，而且 **new** 運算子傳回零，則初始設定式中的某些運算式可能不會完全評估。  
  
## 以 new 所配置物件的存留期  
 使用 **new** 運算子配置的物件不會在其所在的定義範圍結束時終結。  由於 **new** 運算子會傳回其所配置物件的指標，因此程式必須為指標定義適當的範圍，才能存取這些物件。  例如:  
  
```  
// expre_Lifetime_of_Objects_Allocated_with_new.cpp  
// C2541 expected  
int main()  
{  
    // Use new operator to allocate an array of 20 characters.  
    char *AnArray = new char[20];  
  
    for( int i = 0; i < 20; ++i )  
    {  
        // On the first iteration of the loop, allocate  
        //  another array of 20 characters.  
        if( i == 0 )  
        {  
            char *AnotherArray = new char[20];  
        }  
    }  
  
    delete [] AnotherArray; // Error: pointer out of scope.  
    delete [] AnArray;      // OK: pointer still in scope.  
}  
```  
  
 一旦指標 `AnotherArray` 超出範例中的範圍，就無法刪除物件。  
  
## new 運作方式  
 *allocation\-expression* \(包含 **new** 運算子的運算式\) 會執行下列三種功能：  
  
-   為要配置的物件找出並保留存放區。  這個階段完成時會配置正確數量的存放區，但還不是物件。  
  
-   將物件初始化。  初始化完成後，就會出現使配置存放區成為物件的足夠資訊。  
  
-   將指標傳回物件，此物件的指標類型衍生自 *new\-type\-name* 或 *type\-name*。  程式會使用此指標來存取新配置的物件。  
  
 **new** 運算子會叫用 `operator new` 函式。  針對任何類型的陣列，以及不屬於 **class**、`struct` 或 **union** 類型的物件，會呼叫全域函式 **::operator new** 來配置存放區。  類別類型的物件可以根據類別定義各自的 `operator new` 靜態成員函式。  
  
 當編譯器遇到 **new** 運算子以配置類型為 `type` 的物件時，就會呼叫 `type`**::operator new\( sizeof\(** `type` **\) \)**，如果未定義使用者定義的 `operator new`，則會呼叫 **::operator new\( sizeof\(** `type` **\) \)**。  因此，**new** 運算子可以配置物件所需正確數量的記憶體。  
  
> [!NOTE]
>  `operator new` 的引數類型為 **size\_t**。  此類型是在 DIRECT.H、MALLOC.H、MEMORY.H、SEARCH.H、STDDEF.H、STDIO.H、STDLIB.H、STRING.H 和 TIME.H 中定義。  
  
 文法中的選項允許指定 *placement* \(請參閱 [new 運算子](../cpp/new-operator-cpp.md)的文法\)。  *placement* 參數只能用於使用者定義的 `operator new` 實作；它可用於將額外的資訊傳遞至 `operator new`。  如果類別 T 的成員運算子是 new，*placement* 欄位的運算式 \(例如 `T *TObject = new ( 0x0040 ) T;`\) 會被轉譯為 `T *TObject = T::operator new( sizeof( T ), 0x0040 );`，否則會轉譯為 `T *TObject = ::operator new( sizeof( T ), 0x0040 );`。  
  
 *placement* 欄位的原始用途是允許在使用者指定的位址配置與硬體相關的物件。  
  
> [!NOTE]
>  雖然上述範例只示範 *placement* 欄位中的一個引數，但利用這種方式可額外傳遞到 `operator new` 的引數數量不受限制。  
  
 即使已定義類別類型的 `operator new`，也可以此範例的格式使用全域運算子：  
  
```  
T *TObject =::new TObject;  
```  
  
 範圍解析運算子 \(`::`\) 會強制使用全域 **new** 運算子。  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [operator new 函式](../misc/operator-new-function.md)