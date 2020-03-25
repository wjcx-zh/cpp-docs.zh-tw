---
title: new 運算子 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: 21e67f8d44673a15e5d3a5994597caae4cc01a2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161122"
---
# <a name="new-operator-c"></a>new 運算子 (C++)

從可用存放區為*類型名稱*的物件或物件陣列配置記憶體，並將適當類型的非零指標傳回給物件。

> [!NOTE]
>  Microsoft C++元件擴充功能提供**新**關鍵字的支援，以加入 vtable 位置專案。 如需詳細資訊，請參閱[new （vtable 中的新位置）](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>語法

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>備註

如果失敗， **new**會傳回零或擲回例外狀況;如需詳細資訊，請參閱[new 和 Delete 運算子](../cpp/new-and-delete-operators.md)。 您可以藉由撰寫自訂的例外狀況處理常式，並使用您的函式名稱做為其引數呼叫[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)執行時間程式庫函式，來變更此預設行為。

如需如何在 managed 堆積上建立物件的詳細資訊，請參閱[gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)。

當使用**new**來配置C++類別物件的記憶體時，會在配置記憶體之後呼叫物件的函式。

使用[delete](../cpp/delete-operator-cpp.md)運算子來解除配置使用**new**運算子所配置的記憶體。

下列範例會先配置然後再釋放大小為 `dim` 乘以 10 個字元的二維陣列。 配置多維陣列時，第一個維度以外的所有維度都必須是判斷值為正值的常數運算式；最左邊的陣列維度可以是任何判斷值為正值的運算式。 使用**new**運算子配置陣列時，第一個維度可以是零，而**new**運算子會傳回唯一的指標。

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*型別名稱*不能包含**const**、 **volatile**、class 宣告或列舉宣告。 因此，下列運算式是不合法的：

```cpp
volatile char *vch = new volatile char[20];
```

**New**運算子不會配置參考型別，因為它們不是物件。

**New**運算子不能用來配置函式，但可以用來配置函數的指標。 下列範例會配置然後再釋放含七個傳回整數之函式指標的陣列。

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

如果您使用不含任何額外引數的**new**運算子，並使用[/gx](../build/reference/gx-enable-exception-handling.md)、 [/eha](../build/reference/eh-exception-handling-model.md)或[/ehs](../build/reference/eh-exception-handling-model.md)選項進行編譯，則編譯器會產生程式碼，以便在此函式擲回例外狀況時呼叫 operator **delete** 。

下列清單描述**new**的文法元素：

*粘貼*<br/>
如果您多載**new**，提供傳遞其他引數的方法。

*類型-名稱*<br/>
指定要配置的類型；它可以是內建或使用者定義的類型。 如果類型規格是複雜的，請以括號括住類型規格以強制繫結的順序。

*initializer*<br/>
提供初始化物件的值。 初始設定式無法指定給陣列。 只有在類別具有預設的函式時， **new**運算子才會建立物件的陣列。

## <a name="example"></a>範例

下列程式碼範例會配置一個字元陣列和一個 `CName` 類別物件，然後加以釋放。

```cpp
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

## <a name="example"></a>範例

如果您使用**new**運算子的 placement new 形式，則除了配置大小之外，還有含有引數的表單，如果此函式擲回例外狀況，編譯器就不支援**delete**運算子的放置形式。 例如：

```cpp
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

## <a name="initializing-object-allocated-with-new"></a>初始化以 new 所配置的物件

選擇性的*初始化運算式*欄位包含在**new**運算子的文法中。 這樣就可讓您以使用者定義的建構函式初始化新物件。 如需如何完成初始化的詳細資訊，請參閱初始化[運算式](../cpp/initializers.md)。 下列範例說明如何搭配**new**運算子使用初始化運算式：

```cpp
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

在此範例中，會使用**new**運算子設定物件 `CheckingAcct`，但不會指定預設初始化。 因此會呼叫 `Acct()` 類別的預設建構函式。 然後以相同方式配置 `SavingsAcct` 物件，不過它會明確初始化為 34.98。 因為34.98 是**double**類型，所以會呼叫接受該類型之引數的函式來處理初始化。 最後，非類別類型 `HowMuch` 會初始化為 43.0。

如果物件屬於類別類型，且該類別具有「函式」（如上述範例所示），則只有在符合下列其中一個條件時，才可以使用**new**運算子來初始化物件：

- 在初始設定式中提供的引數與建構函式中的引數一致。

- 類別有預設建構函式 (可以在沒有引數的情況下呼叫的建構函式)。

使用**new**運算子配置陣列時，不會進行明確的每個元素初始化。只會呼叫預設的函式（如果有的話）。 如需詳細資訊，請參閱[預設引數](../cpp/default-arguments.md)。

如果記憶體配置失敗（**operator new**會傳回值為0），則不會執行任何初始化。 這樣可防止嘗試初始化不存在的資料。

就像函式呼叫一般，不會定義初始化運算式的評估順序。 此外，您不應依賴這些運算式會在執行記憶體配置之前完全評估。 如果記憶體配置失敗，而**new**運算子傳回零，則初始化運算式中的某些運算式可能無法完全評估。

## <a name="lifetime-of-objects-allocated-with-new"></a>以 new 所配置物件的存留期

使用**new**運算子所配置的物件在其定義的範圍結束時，不會終結。 因為**new**運算子會傳回它所設定物件的指標，所以程式必須定義具有適當範圍的指標來存取這些物件。 例如：

```cpp
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

## <a name="how-new-works"></a>new 運作方式

*配置運算式*（包含**new**運算子的運算式）會執行三項動作：

- 為要配置的物件找出並保留存放區。 這個階段完成時會配置正確數量的存放區，但還不是物件。

- 將物件初始化。 初始化完成後，就會出現使配置存放區成為物件的足夠資訊。

- 傳回衍生自*新類型名稱*或*類型名稱*之指標類型的物件指標。 程式會使用此指標來存取新配置的物件。

**New**運算子會叫用**函式 new**函數。 對於任何類型的陣列，以及不屬於**類別**、**結構** **或等**位類型的物件，會呼叫全域**函式：： operator new**，以配置儲存區。 類別型別物件可以根據每個類別來定義自己的**operator new**靜態成員函式。

當編譯器遇到**new**運算子以配置類型**類型**的物件時，它會發出呼叫給 `type` **：： operator new （sizeof （** `type` **））** ，如果未定義使用者定義的**operator new** ，則為，如果是 **： operator new （sizeof （** `type` **））** 。 因此， **new**運算子可以為物件配置正確的記憶體數量。

> [!NOTE]
>  **Operator new**的引數是 `size_t`的類型。 此類型定義于 \<direct. h >、\<malloc. h >、\<memory. h >、\<search .h >、\<stddef.h >、\<stdio.h .h >、\<stdlib.h>. h >、\<string .h > 和 \<time. h >。

文法中的選項允許指定*位置*（請參閱[New 運算子](../cpp/new-operator-cpp.md)的文法）。 *Placement*參數只能用於**operator new**的使用者定義的實值;它允許將額外的資訊傳遞給**operator new**。 如果類別 T 具有成員運算子 new，則會將含有*放置*欄位（例如 `T *TObject = new ( 0x0040 ) T;`）的運算式轉譯為 `T *TObject = T::operator new( sizeof( T ), 0x0040 );`，否則為 `T *TObject = ::operator new( sizeof( T ), 0x0040 );`。

[*放置*] 欄位的原始目的是允許在使用者指定的位址上配置硬體相依物件。

> [!NOTE]
>  雖然上述範例只顯示*位置*欄位中的一個引數，但這種方式不會限制可傳遞給**operator new**的額外引數數目。

即使已定義類別類型的**operator new** ，也可以使用此範例的格式來使用全域運算子：

```cpp
T *TObject =::new TObject;
```

範圍解析運算子（`::`）會強制使用全域**new**運算子。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[new 和 delete 運算子](../cpp/new-and-delete-operators.md)
