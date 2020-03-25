---
title: override 規範
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 82837ae34ab786e607df54038493b14350574a15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188476"
---
# <a name="override-specifier"></a>override 規範

您可以使用**override**關鍵字來指定覆寫基類中虛擬函式的成員函式。

## <a name="syntax"></a>語法

```
function-declaration override;
```

## <a name="remarks"></a>備註

覆**寫**會區分內容，而且只有在成員函式宣告之後使用時才具有特殊意義;否則，它不是保留的關鍵字。

## <a name="example"></a>範例

使用覆**寫**有助於防止程式碼中發生意外的繼承行為。 下列範例示範不使用覆**寫**的 where，衍生類別的成員函式行為可能不是預期的。 編譯器不會對這個程式碼發出任何錯誤。

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

當您使用**override**時，編譯器會產生錯誤，而不是以無訊息方式建立新的成員函式。

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

若要指定無法覆寫函數，而且無法繼承類別，請使用[final](../cpp/final-specifier.md)關鍵字。

## <a name="see-also"></a>另請參閱

[final 規範](../cpp/final-specifier.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
