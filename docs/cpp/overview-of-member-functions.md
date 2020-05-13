---
title: 成員函式概觀
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: 6dec4ee53cd840c47d76ac0579daca710b0eeb68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358414"
---
# <a name="overview-of-member-functions"></a>成員函式概觀

成員函式不是靜態就是非靜態。 靜態成員函數的行為不同於其他成員函數,因為靜態成員函數沒有隱式**此**參數。 非靜態成員函數具有**此**指標。 無論是靜態或非靜態的成員函式，都可以在類別宣告之內或之外定義。

如果成員函式是在類別宣告內定義，則會將它視為內嵌函式，而且不需要使用其類別名稱限定函式名稱。 儘管在類聲明中定義的函數已被視為內聯函數,但您可以使用**內聯**關鍵字來記錄代碼。

以下是在類別宣告內宣告函式的範例：

```cpp
// overview_of_member_functions1.cpp
class Account
{
public:
    // Declare the member function Deposit within the declaration
    //  of class Account.
    double Deposit( double HowMuch )
    {
        balance += HowMuch;
        return balance;
    }
private:
    double balance;
};

int main()
{
}
```

如果成員函數的定義在類聲明之外,則僅當成員函數顯式聲明為**內聯**時,它才會被視為內聯函數。 此外，定義中的函式名稱必須使用範圍解析運算子 (`::`) 以其類別名稱加以限定。

下列範例與上述 `Account` 類別宣告相同，唯一的差異在於 `Deposit` 函式是在類別宣告之外定義：

```cpp
// overview_of_member_functions2.cpp
class Account
{
public:
    // Declare the member function Deposit but do not define it.
    double Deposit( double HowMuch );
private:
    double balance;
};

inline double Account::Deposit( double HowMuch )
{
    balance += HowMuch;
    return balance;
}

int main()
{
}
```

> [!NOTE]
> 雖然成員函式可以在類別宣告內或分開定義，但是在類別定義之後，成員函式不可加入至該類別。

包含成員函式的類別可以具有多個宣告，不過成員函式本身在程式中只能有一個定義。 若有多個定義，則會在連結時產生錯誤訊息。 如果類別包含內嵌函式定義，則函式定義必須一致，以遵守這項「一個定義」的規則。
