---
title: new 運算子 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: bcb7784e59966510970bd9b3ae0157ae982e462d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768064"
---
# <a name="new-operator-c"></a>new 運算子 (C++)

物件或物件的陣列配置記憶體*型別名稱*從可用存放區，並傳回適當類型、 非零的指標物件。

> [!NOTE]
>  Microsoft c + + 元件擴充功能可讓您**新**關鍵字加入 vtable 位置項目。 如需詳細資訊，請參閱[新 (新 vtable 中的位置）](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>語法

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>備註

如果不成功，**新**會傳回零或擲回例外狀況，請參閱[新和 delete 運算子](../cpp/new-and-delete-operators.md)如需詳細資訊。 您可以變更此預設行為，方法是撰寫自訂的例外狀況處理常式，並呼叫[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)以您的函式名稱，作為其引數的執行階段程式庫函式。

如需如何在 managed 堆積上建立物件的資訊，請參閱[gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)。

當**新**是用來配置記憶體給 c + + 類別物件，物件的建構函式呼叫之後的記憶體配置。

使用[刪除](../cpp/delete-operator-cpp.md)運算子，取消配置所配置之記憶體**新**運算子。

下列範例會先配置然後再釋放大小為 `dim` 乘以 10 個字元的二維陣列。 配置多維陣列時，第一個維度以外的所有維度都必須是判斷值為正值的常數運算式；最左邊的陣列維度可以是任何判斷值為正值的運算式。 配置陣列使用時**新**運算子，第一個維度可以是零 —**新**運算子會傳回唯一指標。

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*型別名稱*不能包含**const**， **volatile**，類別宣告或列舉宣告。 因此，下列運算式是不合法的：

```cpp
volatile char *vch = new volatile char[20];
```

**新**運算子無法配置參考類型，因為它們不是物件。

**新**運算子不能用來配置函式，但它可以用來配置函式的指標。 下列範例會配置然後再釋放含七個傳回整數之函式指標的陣列。

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

如果您使用的運算子**新**而不需要任何額外的引數和與編譯[/GX](../build/reference/gx-enable-exception-handling.md)， [/EHa](../build/reference/eh-exception-handling-model.md)，或[/EHs](../build/reference/eh-exception-handling-model.md)選項，編譯器會將產生程式碼來呼叫運算子**刪除**如果建構函式會擲回的例外狀況。

下列清單描述的文法項目**新**:

*placement*<br/>
提供一個方式來傳遞其他引數，如果您多載**新**。

*type-name*<br/>
指定要配置的類型；它可以是內建或使用者定義的類型。 如果類型規格是複雜的，請以括號括住類型規格以強制繫結的順序。

*initializer*<br/>
提供初始化物件的值。 初始設定式無法指定給陣列。 **新**運算子只會建立物件的陣列類別具有預設建構函式。

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

如果您使用的放置新的表單**新**運算子，除了大小的引數的形式的配置，編譯器不支援的位置形式**刪除**運算子如果建構函式會擲回例外狀況。 例如: 

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

選擇性*初始設定式*欄位包含在文法**新**運算子。 這樣就可讓您以使用者定義的建構函式初始化新物件。 如需有關如何執行初始化的詳細資訊，請參閱 <<c0> [ 初始設定式](../cpp/initializers.md)。 下列範例說明如何使用初始化運算式**新**運算子：

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

在此範例中，物件`CheckingAcct`使用配置**新**指定運算子，但沒有預設值初始化。 因此會呼叫 `Acct()` 類別的預設建構函式。 然後以相同方式配置 `SavingsAcct` 物件，不過它會明確初始化為 34.98。 由於 34.98 屬於類型**double**，接受該類型的引數的建構函式會呼叫來處理初始化。 最後，非類別類型 `HowMuch` 會初始化為 43.0。

如果物件是類別類型，且該類別具有建構函式 （如上述範例中），可以藉由初始化物件**新**運算子只有在符合下列條件之一符合：

- 在初始設定式中提供的引數與建構函式中的引數一致。

- 類別有預設建構函式 (可以在沒有引數的情況下呼叫的建構函式)。

使用配置陣列時，就可以完成任何明確的每個元素的初始化**新**運算子; 只有預設建構函式，如果有的話，會呼叫。 請參閱[預設引數](../cpp/default-arguments.md)如需詳細資訊。

如果記憶體配置失敗 (**new 運算子**傳回值為 0)，不會執行初始化。 這樣可防止嘗試初始化不存在的資料。

就像函式呼叫一般，不會定義初始化運算式的評估順序。 此外，您不應依賴這些運算式會在執行記憶體配置之前完全評估。 如果記憶體配置失敗，**新**運算子傳回零，則初始設定式中的某些運算式可能不會完全評估。

## <a name="lifetime-of-objects-allocated-with-new"></a>以 new 所配置物件的存留期

使用所配置的物件**新**定義所在的範圍結束時，不會終結運算子。 因為**新**運算子會傳回其所配置的物件的指標，該程式必須定義適當的範圍，才能存取這些物件的指標。 例如: 

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

*配置運算式*--運算式包含**新**運算子，會執行三件事：

- 為要配置的物件找出並保留存放區。 這個階段完成時會配置正確數量的存放區，但還不是物件。

- 將物件初始化。 初始化完成後，就會出現使配置存放區成為物件的足夠資訊。

- 傳回的指標，指標類型的物件衍生自*新類型名稱*或是*型別名稱*。 程式會使用此指標來存取新配置的物件。

**新**運算子會叫用函式**new 運算子**。 任何型別，陣列和物件不屬於**類別**，**結構**，或**union**類型、 全域函式， **:: new 運算子**，是呼叫以將存放裝置配置。 類別類型的物件可以定義自己**new 運算子**每個類別的靜態成員函式。

當編譯器遇到**新**運算子來配置類型的物件**型別**，就會發出呼叫`type` **:: 運算子 new (sizeof (** `type`**))** 或者，如果使用者定義的無**new 運算子**定義，則 **:: 運算子 new (sizeof (** `type` **))**。 因此，**新**運算子可以配置正確數量的記憶體物件。

> [!NOTE]
>  引數**new 運算子**別的`size_t`。 此類型定義於\<direct.h >， \<malloc.h >， \<memory.h> >， \<search.h> >， \<stddef.h >， \<stdio.h >， \<stdlib.h >， \<h >，並\<time.h >。

文法中的選項可讓規格*放置*(請參閱文法[new 運算子](../cpp/new-operator-cpp.md))。 *放置*參數僅用於使用者定義的實作**new 運算子**; 它可讓額外的資訊傳遞給**運算子 new**。 使用運算式*放置*這類欄位`T *TObject = new ( 0x0040 ) T;`轉譯成`T *TObject = T::operator new( sizeof( T ), 0x0040 );`如果類別 T 有成員運算子 new，否則為要`T *TObject = ::operator new( sizeof( T ), 0x0040 );`。

原本*放置*欄位就是要允許在使用者指定的位址配置硬體相關的物件。

> [!NOTE]
>  雖然上述範例顯示中的只有一個引數*放置*欄位中，沒有任何限制在幾個額外的引數可傳遞給**new 運算子**這種方式。

即使**new 運算子**已定義類別類型，全域運算子可供使用此範例的格式：

```cpp
T *TObject =::new TObject;
```

範圍解析運算子 (`::`) 會強制使用全域**新**運算子。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[新和 delete 運算子](../cpp/new-and-delete-operators.md)