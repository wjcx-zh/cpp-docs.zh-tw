---
title: final 規範
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: 93e8d9b0b445d1120ec15911eb763ae1d7d2d359
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188649"
---
# <a name="final-specifier"></a>final 規範

您可以使用**final**關鍵字來指定無法在衍生類別中覆寫的虛擬函式。 您也可以用它來指定無法被繼承的類別。

## <a name="syntax"></a>語法

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>備註

**final**是內容相關的，只有在函式宣告或類別名稱之後使用時才具有特殊意義;否則，它不是保留的關鍵字。

當在類別宣告中使用**final**時，`base-classes` 是宣告的選擇性部分。

## <a name="example"></a>範例

下列範例會使用**final**關鍵字來指定無法覆寫虛擬函式。

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

如需如何指定可覆寫成員函式的詳細資訊，請參閱覆[寫規範](../cpp/override-specifier.md)。

下一個範例會使用**final**關鍵字來指定無法繼承類別。

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
