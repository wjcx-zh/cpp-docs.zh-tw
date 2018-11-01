---
title: override 規範
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 71505f8b9b4dc2800e80a78a64f0ca6984af1349
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430026"
---
# <a name="override-specifier"></a>override 規範

您可以使用**覆寫**關鍵字指定成員覆寫基底類別中的虛擬函式的函式。

## <a name="syntax"></a>語法

```
function-declaration override;
```

## <a name="remarks"></a>備註

**覆寫**具備內容相關性，具有特殊意義時，才使用成員函式宣告之後; 否則它不是保留的關鍵字。

## <a name="example"></a>範例

使用**覆寫**來協助防止意外的繼承行為，在您的程式碼。 下列範例將示範在不用**覆寫**，衍生的類別成員函式行為可能會非預期。 編譯器不會對這個程式碼發出任何錯誤。

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

當您使用**覆寫**，編譯器會產生錯誤，而不是以無訊息方式建立新的成員函式。

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

若要指定無法覆寫函式和類別無法被繼承，請使用[最終](../cpp/final-specifier.md)關鍵字。

## <a name="see-also"></a>另請參閱

[final 規範](../cpp/final-specifier.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)