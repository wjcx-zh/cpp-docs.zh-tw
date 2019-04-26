---
title: final 規範
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: c6400c8060664713fdd004a5aa9536e0617bc0c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154772"
---
# <a name="final-specifier"></a>final 規範

您可以使用**最終**關鍵字指定無法在衍生類別中覆寫虛擬函式。 您也可以用它來指定無法被繼承的類別。

## <a name="syntax"></a>語法

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>備註

**最終**具備內容相關性，有特殊意義，只有當它用函式宣告之後，或類別名稱; 否則它不是保留的關鍵字。

當**最終**會在類別宣告`base-classes`屬於選擇性宣告。

## <a name="example"></a>範例

下列範例會使用**最終**關鍵字來指定無法覆寫虛擬函式。

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

如需有關如何指定可以覆寫成員函式的資訊，請參閱[覆寫規範](../cpp/override-specifier.md)。

下一個範例會使用**最終**關鍵字來指定類別無法被繼承。

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[override 規範](../cpp/override-specifier.md)