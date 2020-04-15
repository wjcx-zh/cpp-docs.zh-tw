---
title: 列舉 (C++)
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: 2a1b3d33534887568c6a55e320e77e0a018cafff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366327"
---
# <a name="enumerations-c"></a>列舉 (C++)

列舉是使用者定義類型，其中包含一組具名的整數常數，稱為列舉值。

> [!NOTE]
> 本文介紹了 iSO 標準C++語言**枚舉**類型以及 C++11 中介紹的作用域(或強類型)**枚舉類**類型。 有關C++/CLI 和C++/CX**中的公共枚舉類**或**私有枚舉類**類型的資訊,請參閱[枚舉類](../extensions/enum-class-cpp-component-extensions.md)。

## <a name="syntax"></a>語法

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>參數

*識別碼*<br/>
提供給列舉的類型名稱。

*型別*<br/>
列舉值的基礎類型，所有列舉值都有相同的基礎類型。 可以是任何整數類資料類型。

*列舉清單*<br/>
在列舉中，列舉值的逗號分隔清單。 範圍內的每個列舉值或變數名稱都必須是唯一的。 不過，值可以重複。 在未作用域的枚舉中,範圍是周圍的範圍;在作用域的枚舉中,作用域是*枚舉清單*本身。  在作用域的枚舉中,清單可能為空,這實際上定義了新的積分類型。

*class*<br/>
透過在宣告中使用此關鍵字,可以指定枚舉的範圍,並且必須提供*識別子*。 您還可以使用**結構**關鍵字代替**類**,因為它們在此上下文中在語義上等效。

## <a name="enumerator-scope"></a>列舉器範圍

列舉提供內容，描述表示為具名常數的值範圍 (也稱為列舉值)。 在原始 C 和 C++ 列舉類型中，不合格的列舉值會顯示在宣告列舉的範圍中。 在限定範圍列舉中，列舉值名稱必須由列舉類型名稱來限定。 下列範例示範這兩種列舉之間的這項基本差異：

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

列舉中的每個名稱被指派整數值，這個值對應於它在列舉值順序中的位置。 根據預設，第一個指派的值是 0，下一個指派的是 1，依此類推，不過，您可以明確設定列舉程式的值，如下所示：

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

指派給列舉值 `Diamonds` 的值為 `1`。 後續列舉值，如果未提供其明確值，則接收前一個列舉值的值加一。 在上述範例中，`Hearts` 會有值 2，而 `Clubs` 會有 3，依此類推。

每個枚舉器都被視為常量,必須在定義**枚舉**的作用域(對於未界定的枚舉)或**枚舉**本身(對於作用域枚舉)內具有唯一的名稱。 指定給名稱的值不需要是唯一的。 例如，如果不限範圍的列舉 `Suit` 宣告如下：

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

然後 `Diamonds`、`Hearts`、`Clubs` 和 `Spades` 的值分別為 5、6、4 和 5。 請注意 5 已多次使用，這是允許的行為，即使可能不適合。 對於限定範圍列舉，這些規則都相同。

## <a name="casting-rules"></a>轉型規則

未作用網域的枚舉常量可以隱式轉換為**int,** 但**int**永遠不會隱式轉換為枚舉值。 下列範例顯示，如果您嘗試將不是 `hand` 的值指派給 `Suit` 時，所發生的狀況：

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

需要強制轉換**int**到作用域或未範圍的枚舉器。 不過，您可以將不限範圍的列舉值提升為整數值，而不需要轉型。

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

以這種方式使用隱含轉換，可能造成非預期的副作用。 為了協助排除與不限範圍的列舉關聯之程式設計錯誤，範圍列舉值是強類型。 限定範圍列舉值必須由列舉類型名稱 (識別項) 來限定，且無法以隱含方式轉換為 int，如下列範例所示：

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

請注意，程式行 `hand = account_num;` 仍然會導致因為不限範圍的列舉而發生的錯誤，如上所示。 使用明確轉換時，允許這個行為。 不過，使用限定範圍列舉時，不再允許在沒有明確轉型的情況下，於下一個陳述式 `account_num = Suit::Hearts;` 中嘗試轉換。

## <a name="enums-with-no-enumerators"></a><a name="no_enumerators"></a>沒有枚舉器的枚舉

**Visual Studio 2017 版本 15.3 及更高版本**(隨[/std:c++17 提供](../build/reference/std-specify-language-standard-version.md)):通過定義具有顯式基礎類型且無枚舉例的枚舉(常規或作用域),實際上可以引入一種沒有隱式轉換為任何其他類型的新積分類型。 通過使用此類型而不是其內置基礎類型,可以消除由無意隱式轉換引起的細微錯誤的可能性。

```cpp
enum class byte : unsigned char { };
```

新類型是基礎類型的準確副本,因此具有相同的調用約定,這意味著它可以跨 AI 使用,而不會造成任何性能損失。 使用直接清單初始化初始化類型變數時,不需要強制轉換。 下面的範例展示如何在不同上下文中沒有枚舉器的情況下初始化枚舉:

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>另請參閱

[C 宣告聲明](../c-language/c-enumeration-declarations.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
