---
title: 抽象類別 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c35ea26bc5dda6c0dce27217cc75784034a77554
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705357"
---
# <a name="abstract-classes-c"></a>抽象類別 (C++)

抽象類別用於表示可衍生更明確類別的一般概念。 您無法建立抽象類別類型的物件，但是可以使用抽象類別類型的指標和參考。

至少包含一個純虛擬函式的類別會被視為抽象類別。 衍生自抽象類別的類別必須實作純虛擬函式，否則這些類別也是抽象類別。

虛擬函式宣告可為 「 單純的 」 透過*純規範*語法 (述[類別通訊協定實作](http://msdn.microsoft.com/en-us/a319f1b3-05e8-400e-950a-1ca6eb105ab5))。 中的範例，請考慮[虛擬函式](../cpp/virtual-functions.md)。 `Account` 類別的目的是要提供一般功能，但 `Account` 類型的物件則過於籠統，實用性不高。 因此，`Account` 非常適合作為抽象類別：

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

此宣告和上一個宣告之間唯一的差別，在於 `PrintBalance` 是使用純指定名稱 (`= 0`) 宣告的。

## <a name="restrictions-on-abstract-classes"></a>抽象類別的限制

抽象類別不能用於：

- 變數或成員資料

- 引數類型

- 函式傳回型別

- 明確轉換的類型

另一項限制是，如果抽象類別的建構函式直接或間接呼叫純虛擬函式，則結果會是未定義。 不過，抽象類別的建構函式和解構函式可以呼叫其他成員函式。

您可以為抽象類別定義純虛擬函式，但是只能使用下列語法直接呼叫：

*抽象類別名稱*::*函式名稱*（)

這在設計基底類別包含純虛擬解構函式的類別階層架構時很有幫助，因為基底類別解構函式會一律在終結物件的處理序中呼叫。 參考下列範例：

```cpp
// Declare an abstract base class with a pure virtual destructor.
// deriv_RestrictionsonUsingAbstractClasses.cpp
class base {
public:
    base() {}
    virtual ~base()=0;
};

// Provide a definition for destructor.
base::~base() {}

class derived:public base {
public:
    derived() {}
    ~derived(){}
};

int main() {
    derived *pDerived = new derived;
    delete pDerived;
}
```

當 `pDerived` 所指向的物件已刪除時，就會呼叫 `derived` 類別的解構函式，然後呼叫 `base` 類別的解構函式。 純虛擬函式的空白實作可確保函式至少有某種實作存在。

> [!NOTE]
> 在上述範例中，純虛擬函式 `base::~base` 是從 `derived::~derived` 隱含呼叫。 另外也可以使用完整限定的成員函式名稱明確呼叫純虛擬函式。

## <a name="see-also"></a>另請參閱

- [繼承](../cpp/inheritance-cpp.md)
