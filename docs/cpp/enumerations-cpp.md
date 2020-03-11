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
ms.openlocfilehash: caec9ea7ac5482ff23b73676a3fd7b3d25ad293f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884145"
---
# <a name="enumerations-c"></a>列舉 (C++)

列舉是使用者定義類型，其中包含一組具名的整數常數，稱為列舉值。

> [!NOTE]
>  本文涵蓋 ISO 標準C++語言**列舉**類型，以及在 c + + 11 中引進的範圍（或強型別）**列舉類別**類型。 如需/Cli C++和/cx 中**公用列舉類別**或**私用** C++列舉類別類型的詳細資訊，請參閱[enum 類別](../extensions/enum-class-cpp-component-extensions.md)。

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

*identifier*<br/>
提供給列舉的類型名稱。

*type*<br/>
列舉值的基礎類型，所有列舉值都有相同的基礎類型。 可以是任何整數類資料類型。

*列舉清單*<br/>
在列舉中，列舉值的逗號分隔清單。 範圍內的每個列舉值或變數名稱都必須是唯一的。 不過，值可以重複。 在不限範圍的列舉中，範圍是周圍的範圍;在限定範圍的列舉中，範圍是*列舉清單*本身。  在限定範圍的列舉中，清單可能是空的，這實際上會定義新的整數類資料類型。

*class*<br/>
藉由在宣告中使用此關鍵字，您可以指定列舉的範圍，而且必須提供*識別碼*。 您也可以使用**struct**關鍵字來取代**類別**，因為在此內容中，它們在語義上是相等的。

## <a name="enumerator-scope"></a>列舉值範圍

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

每個列舉值都會被視為常數，而且在定義列舉的範圍內（適用于不限範圍的**列舉**）或在列舉本身內，必須有唯一的名稱（適用于限域的**列舉**）。 指定給名稱的值不需要是唯一的。 例如，如果不限範圍的列舉 `Suit` 宣告如下：

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

然後 `Diamonds`、`Hearts`、`Clubs` 和 `Spades` 的值分別為 5、6、4 和 5。 請注意 5 已多次使用，這是允許的行為，即使可能不適合。 對於限定範圍列舉，這些規則都相同。

## <a name="casting-rules"></a>轉型規則

不限範圍的列舉常數可以隱含地轉換成**int**，但**int**永遠不會隱含地轉換為列舉值。 下列範例顯示，如果您嘗試將不是 `hand` 的值指派給 `Suit` 時，所發生的狀況：

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

需要進行轉換，才能將**int**轉換成限定範圍或不限範圍的列舉值。 不過，您可以將不限範圍的列舉值提升為整數值，而不需要轉型。

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

## <a name="no_enumerators"></a>沒有枚舉器的列舉

**Visual Studio 2017 15.3 和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：藉由定義具有明確基礎類型的列舉（一般或範圍），而不使用任何列舉值，您實際上可以導入不會隱含轉換為任何其他類型的新整數類型。 藉由使用這個類型，而不是其內建的基礎類型，您可以消除因不小心隱含轉換而造成的微妙錯誤的可能性。

```cpp
enum class byte : unsigned char { };
```

新的型別是基礎型別的完整複本，因此具有相同的呼叫慣例，這表示它可以跨 Abi 使用，而不會造成任何效能上的負面影響。 當使用直接清單初始化來初始化類型的變數時，不需要轉換。 下列範例顯示如何在不同的內容中初始化沒有列舉值的列舉：

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

[C 列舉宣告](../c-language/c-enumeration-declarations.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)