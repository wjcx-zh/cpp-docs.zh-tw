---
title: 虛擬函式
ms.date: 09/10/2019
helpviewer_keywords:
- functions [C++], virtual functions
- derived classes [C++], virtual functions
- virtual functions
ms.assetid: b3e1ed88-2a90-4af8-960a-16f47deb3452
ms.openlocfilehash: 4296d66af8f8bb9aed4946d6dc57871f447108d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231035"
---
# <a name="virtual-functions"></a>虛擬函式

虛擬函式是您必須在衍生類別中重新定義的成員函式。 當您使用基底類別的參考或指標參考衍生類別物件時，可以呼叫該物件的虛擬函式，並執行函式的衍生類別版本。

不論呼叫函式時使用的運算式為何，虛擬函式都可確保針對物件呼叫正確的函式。

假設基類包含宣告為[virtual](../cpp/virtual-cpp.md)的函式，且衍生類別定義相同的函式。 針對衍生類別的物件會叫用來自衍生類別的函式 (即使是使用基底類別的指標或參考呼叫)。 下列範例將示範基底類別，它會提供 `PrintBalance` 函式和兩個衍生類別的實作

```cpp
// deriv_VirtualFunctions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Account {
public:
   Account( double d ) { _balance = d; }
   virtual ~Account() {}
   virtual double GetBalance() { return _balance; }
   virtual void PrintBalance() { cerr << "Error. Balance not available for base type." << endl; }
private:
    double _balance;
};

class CheckingAccount : public Account {
public:
   CheckingAccount(double d) : Account(d) {}
   void PrintBalance() { cout << "Checking account balance: " << GetBalance() << endl; }
};

class SavingsAccount : public Account {
public:
   SavingsAccount(double d) : Account(d) {}
   void PrintBalance() { cout << "Savings account balance: " << GetBalance(); }
};

int main() {
   // Create objects of type CheckingAccount and SavingsAccount.
   CheckingAccount checking( 100.00 );
   SavingsAccount  savings( 1000.00 );

   // Call PrintBalance using a pointer to Account.
   Account *pAccount = &checking;
   pAccount->PrintBalance();

   // Call PrintBalance using a pointer to Account.
   pAccount = &savings;
   pAccount->PrintBalance();
}
```

在上述程式碼中，除了針對 `PrintBalance` 所指向的物件之外，`pAccount` 的呼叫都相同。 由於 `PrintBalance` 是虛擬的，因此會呼叫為每個物件定義的函式版本。 衍生類別 `PrintBalance` 和 `CheckingAccount` 中的 `SavingsAccount` 函式會「覆寫」基底類別 `Account` 中的函式。

如果宣告的類別未提供 `PrintBalance` 函式的覆寫實作，則會使用基底類別 `Account` 的預設實作。

衍生類別中的函式只有在類型相同時，才會覆寫基底類別中的虛擬函式。 衍生類別內的函式不能只使用傳回類型與基底類別內的虛擬函式作區別，引數清單也必須加以區別。

使用指標或參考呼叫函式時，適用下列規則：

- 對虛擬函式的呼叫會根據為其進行呼叫之物件的基礎類型進行解析。

- 對非虛擬函式的呼叫是根據指標或參考的類型進行解析。

下列範例將示範透過指標呼叫時，虛擬和非虛擬函式的行為：

```cpp
// deriv_VirtualFunctions2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base {
public:
   virtual void NameOf();   // Virtual function.
   void InvokingClass();   // Nonvirtual function.
};

// Implement the two functions.
void Base::NameOf() {
   cout << "Base::NameOf\n";
}

void Base::InvokingClass() {
   cout << "Invoked by Base\n";
}

class Derived : public Base {
public:
   void NameOf();   // Virtual function.
   void InvokingClass();   // Nonvirtual function.
};

// Implement the two functions.
void Derived::NameOf() {
   cout << "Derived::NameOf\n";
}

void Derived::InvokingClass() {
   cout << "Invoked by Derived\n";
}

int main() {
   // Declare an object of type Derived.
   Derived aDerived;

   // Declare two pointers, one of type Derived * and the other
   //  of type Base *, and initialize them to point to aDerived.
   Derived *pDerived = &aDerived;
   Base    *pBase    = &aDerived;

   // Call the functions.
   pBase->NameOf();           // Call virtual function.
   pBase->InvokingClass();    // Call nonvirtual function.
   pDerived->NameOf();        // Call virtual function.
   pDerived->InvokingClass(); // Call nonvirtual function.
}
```

```Output
Derived::NameOf
Invoked by Base
Derived::NameOf
Invoked by Derived
```

請注意，無論 `NameOf` 函式是經由 `Base` 的指標或 `Derived` 的指標叫用，都會呼叫 `Derived` 的函式。 它會呼叫 `Derived` 的函式是因為 `NameOf` 是虛擬函式，而且 `pBase` 和 `pDerived` 都指向 `Derived` 類型的物件。

因為只會針對類別類型的物件呼叫虛擬函式，所以您無法將全域或靜態函式宣告為 **`virtual`** 。

在 **`virtual`** 衍生類別中宣告覆寫函式時，可以使用關鍵字，但這是不必要的; 虛擬函式的覆寫一律是虛擬的。

必須定義基類中的虛擬函式，除非它們是使用*純規範*來宣告。 （如需純虛擬函式的詳細資訊，請參閱[抽象類別](../cpp/abstract-classes-cpp.md)）。

使用範圍解析運算子 (`::`) 就可透過明確限定函式名稱的方式隱藏虛擬函式呼叫機制。 請參考先前包含 `Account` 類別的範例。 若要呼叫基底類別中的 `PrintBalance`，請使用下列範例程式碼：

```cpp
CheckingAccount *pChecking = new CheckingAccount( 100.00 );

pChecking->Account::PrintBalance();  //  Explicit qualification.

Account *pAccount = pChecking;  // Call Account::PrintBalance

pAccount->Account::PrintBalance();   //  Explicit qualification.
```

上述範例中對 `PrintBalance` 的兩個呼叫都會隱藏虛擬函式呼叫機制。
