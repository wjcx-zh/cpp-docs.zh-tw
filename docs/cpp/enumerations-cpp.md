---
title: "列舉型別 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: enum_cpp
dev_langs: C++
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96b1b29baaa779fda1e1f076daf3d8bd9335403b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="enumerations-c"></a>列舉 (C++)
列舉是使用者定義類型，其中包含一組具名的整數常數，稱為列舉值。  
  
> [!NOTE]
>  本文包含 ISO Standard C++ 語言 `enum` 類型和限定範圍 (或強類型) `enum class` 類型 (在 C++11 中引入)。 如需有關資訊`public enum class`或`private enum class`類型在 C + + /CLI 和 C + + /CX 中，請參閱[列舉類別](../windows/enum-class-cpp-component-extensions.md)。  
  
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
  
```  
// Forward declaration of enumerations  (C++11):  
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```  
  
## <a name="parameters"></a>參數  
 `identifier`  
 提供給列舉的類型名稱。  
  
 `type`  
 列舉值的基礎類型，所有列舉值都有相同的基礎類型。 可以是任何整數類資料類型。  
  
 `enum-list`  
 在列舉中，列舉值的逗號分隔清單。 範圍內的每個列舉值或變數名稱都必須是唯一的。 不過，值可以重複。 在不限範圍的列舉中，範圍是周圍範圍。在限定範圍的列舉中，範圍是 `enum-list` 本身。  中的限定範圍的列舉清單可能是空的作用中定義新的整數類資料類型。
  
 `class`  
 在宣告中使用此關鍵字，您就可以指定列舉已限定範圍，且必須提供 `identifier`。 您也可以使用 `struct` 關鍵字取代 `class`，因為它們在此內容中的語意相同。  
  
## <a name="enumerator-scope"></a>列舉值的範圍  
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
  
 每個列舉值會被視為常數，而且在定義 `enum` 的範圍內 (適用於不限範圍的列舉) 或在列舉本身內 (適用於限定範圍列舉) 必須有唯一名稱。 指定給名稱的值不需要是唯一的。 例如，如果不限範圍的列舉 `Suit` 宣告如下：  
  
```cpp  
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };  
```  
  
 然後 `Diamonds`、`Hearts`、`Clubs` 和 `Spades` 的值分別為 5、6、4 和 5。 請注意 5 已多次使用，這是允許的行為，即使可能不適合。 對於限定範圍列舉，這些規則都相同。  
  
 ## <a name="casting-rules"></a>轉型規則  
  
 不限範圍的列舉常數可以隱含轉換為 `int`，但是 `int` 絕對不能隱含轉換為列舉值。 下列範例顯示，如果您嘗試將不是 `hand` 的值指派給 `Suit` 時，所發生的狀況：  
  
```cpp  
int account_num = 135692;  
Suit hand;  
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'  
  
```  
  
 必須有轉型將 `int` 轉換為限定範圍列舉值或不限範圍的列舉值。 不過，您可以將不限範圍的列舉值提升為整數值，而不需要轉型。  
  
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
  
```  
  
 請注意，程式行 `hand = account_num;` 仍然會導致因為不限範圍的列舉而發生的錯誤，如上所示。 使用明確轉換時，允許這個行為。 不過，使用限定範圍列舉時，不再允許在沒有明確轉型的情況下，於下一個陳述式 `account_num = Suit::Hearts;` 中嘗試轉換。 

## <a name="enums-with-no-enumerators"></a>沒有列舉值的列舉
**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):，您可以藉由定義列舉 （規則或範圍） 具有明確的基礎類型和任何的列舉值，作用中引入新的整數類資料類型已為任何其他型別沒有隱含轉換。 使用這個型別，而非內建的基礎類型，就可以消除不小心的隱含轉換所造成的細微錯誤的可能性。  


```cpp
enum class byte : unsigned char { };
```

新的類型是完全相同複本的基礎類型，便會因此擁有相同的呼叫慣例，這表示它可以利用跨 ABIs 不含任何效能產生負面影響。 類型的變數會初始化使用 direct 清單初始化時，需要轉型。 下列範例會示範如何初始化在不同內容中沒有列舉值的列舉：

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
  
## <a name="see-also"></a>請參閱  
 [C 列舉宣告](../c-language/c-enumeration-declarations.md)   
 [關鍵字](../cpp/keywords-cpp.md)