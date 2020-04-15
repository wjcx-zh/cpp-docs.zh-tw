---
title: new 運算子 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: ac89bf37b8aaaa9d77393b714a233f8a4c998139
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367878"
---
# <a name="new-operator-c"></a>new 運算子 (C++)

從空閒儲存為*類型名稱*的物件或數位分配記憶體,並返回指向物件的適當類型非零指標。

> [!NOTE]
> Microsoft C++元件擴展程式支援**新**關鍵字添加可訪問槽條目。 有關詳細資訊,請參閱[新插槽(vtable 中的新插槽)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>語法

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>備註

如果不成功,新返回零或引發異常;如果失敗,**則返回**零或引發異常。關於詳細資訊[,請參閱新運算子與刪除運算子](../cpp/new-and-delete-operators.md)。 可以通過編寫自定義異常處理例程並將[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)執行時庫函數與函數名稱作為其參數來更改此默認行為。

有關如何在託管堆上創建物件的資訊,請參閱[gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)。

當**new**用於為C++類物件分配記憶體時,將在分配記憶體後調用物件的構造函數。

使用[delete](../cpp/delete-operator-cpp.md)運算子取消分配**與新運算符一**起分配的記憶體。

下列範例會先配置然後再釋放大小為 `dim` 乘以 10 個字元的二維陣列。 配置多維陣列時，第一個維度以外的所有維度都必須是判斷值為正值的常數運算式；最左邊的陣列維度可以是任何判斷值為正值的運算式。 使用**新**運算符分配陣列時,第一個維度可以是零 -**新**運算符返回唯一指標。

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*類型名稱*不能包含**const、****易失性**、類聲明或枚舉聲明。 因此，下列運算式是不合法的：

```cpp
volatile char *vch = new volatile char[20];
```

**新**運算元不分配引用類型,因為它們不是物件。

**新**運算子不能用於分配函數,但可用於分配指向函數的指標。 下列範例會配置然後再釋放含七個傳回整數之函式指標的陣列。

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

如果使用運算符**new**而不提供任何額外的參數,並使用[/GX](../build/reference/gx-enable-exception-handling.md) [、/EHa](../build/reference/eh-exception-handling-model.md)或[/EHs](../build/reference/eh-exception-handling-model.md)選項進行編譯,則編譯器將生成代碼,在建構函數引發異常時調用運算符**刪除**。

下面的清單描述了**新的**語法元素:

*位置*<br/>
提供其他參數的方法,如果重載**new**。

*類型名稱*<br/>
指定要配置的類型；它可以是內建或使用者定義的類型。 如果類型規格是複雜的，請以括號括住類型規格以強制繫結的順序。

*初始設定式*<br/>
提供初始化物件的值。 初始設定式無法指定給陣列。 只當類具有預設建構函數時,**新**運算元才會創建物件的陣列。

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

如果使用**新**運算符的放置新窗體(除了分配大小之外帶有參數的窗體),則如果建構函數引發異常,編譯器不支援**delete**運算符的放置形式。 例如：

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

**新**運算子的語法中包含可選的初始*化器*欄位。 這樣就可讓您以使用者定義的建構函式初始化新物件。 關於如何初始化的詳細資訊,請參閱[初始化器](../cpp/initializers.md)。 以下範例說明了如何**與新運算符一**起使用初始化運算式:

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

在此範例中,使用**新**運算符分配`CheckingAcct`物件,但不指定預設初始化。 因此會呼叫 `Acct()` 類別的預設建構函式。 然後以相同方式配置 `SavingsAcct` 物件，不過它會明確初始化為 34.98。 由於 34.98 的類型為**雙**,因此調用採用該類型參數的構造函數來處理初始化。 最後，非類別類型 `HowMuch` 會初始化為 43.0。

如果物件是類類型,並且該類具有構造函數(如前面的範例所示),則只有在滿足以下條件之一時,**新**運算元才能初始化該物件:

- 在初始設定式中提供的引數與建構函式中的引數一致。

- 類別有預設建構函式 (可以在沒有引數的情況下呼叫的建構函式)。

使用**新**運算符分配陣組時,無法執行顯式每個元素初始化;僅調用預設構造函數(如果存在)。 有關詳細資訊[,請參閱預設參數](../cpp/default-arguments.md)。

如果記憶體配置失敗(**運算符 new**返回值 0),則不執行初始化。 這樣可防止嘗試初始化不存在的資料。

就像函式呼叫一般，不會定義初始化運算式的評估順序。 此外，您不應依賴這些運算式會在執行記憶體配置之前完全評估。 如果記憶體配置失敗,**並且新**運算符返回零,則初始化器中的某些運算式可能無法完全計算。

## <a name="lifetime-of-objects-allocated-with-new"></a>以 new 所配置物件的存留期

退出使用**新**運算符分配的物件時,不會銷毀它們的定義範圍。 由於**新**運算符返回指向其分配的物件的指標,因此程式必須定義具有適當作用域的指標才能訪問這些物件。 例如：

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

*配置表示式*(包含**新**運算子的運算式)執行三件事:

- 為要配置的物件找出並保留存放區。 這個階段完成時會配置正確數量的存放區，但還不是物件。

- 將物件初始化。 初始化完成後，就會出現使配置存放區成為物件的足夠資訊。

- 返回指向從*新類型名稱*或*類型名稱*派生的指標類型的物件的指標。 程式會使用此指標來存取新配置的物件。

**新**運算子呼叫函數**運算符 new**。 對於任何類型的陣列,對於不是**類**、**結構**類型或**聯合**類型的物件,調用全域函數 **::運算符 new,** 以分配存儲。 類類型物件可以基於每個類定義自己的**運算符新的**靜態成員函數。

當編譯器遇到**新**運算符以分配**類型類型**的物件時,它將`type`發出呼叫 **:: 運算子 new(sizeof)),**`type`**) )** 或者,如果沒有定義使用者定義的運算符**new(sizeof)** `type` **。** **operator new** 因此,**新**運算符可以為物件分配正確的記憶體量。

> [!NOTE]
> 運算子**new**的參數`size_t`是型態 。 \<此類型在直接.h \<>、malloc.h>、memory.h \<>、search.h \< \<>、stddef.h \<>、stdio.h>、stdlib.h \< \<>、string.h> 和\<time.h>中定义。

語法中的選項允許指定*放置*(請參閱[新運算符](../cpp/new-operator-cpp.md)的語法)。 *放置*參數只能用於**運算符 new**的使用者定義的實現。它允許將額外的資訊傳遞給**管理員新**。 如果類別 T 具有`T *TObject = new ( 0x0040 ) T;`新成員 運算子`T *TObject = T::operator new( sizeof( T ), 0x0040 );`,`T *TObject = ::operator new( sizeof( T ), 0x0040 );`否則將轉換為 具有*放置欄位的*表示式,例如轉換成 。

*放置*欄位的初衷是允許在使用者指定的位址分配與硬體相關的物件。

> [!NOTE]
> 儘管前面的示例在*放置*欄位中只顯示一個參數,但對於以這種方式傳遞給**新運算元**的額外參數數沒有限制。

即使為類別定義了**運算子 new,** 也可以使用此範例的形式使用全域運算符號:

```cpp
T *TObject =::new TObject;
```

範圍解析運算子 (`::`) 強制使用全域**新**運算子。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[新增運算子與刪除運算子](../cpp/new-and-delete-operators.md)
