---
title: __if_not_exists 陳述式
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: e99fcee440bd69eabafec693df99d347f3aee828
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560279"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists 陳述式

**`__if_not_exists`** 語句會測試指定的識別碼是否存在。 如果識別項不存在，就會執行指定的陳述式區塊。

## <a name="syntax"></a>語法

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>參數

*識別碼*\
要測試其是否存在的識別項。

*語句*\
當 *識別碼* 不存在時要執行的一或多個語句。

## <a name="remarks"></a>備註

> [!CAUTION]
> 若要達到最可靠的結果，請使用 **`__if_not_exists`** 下列條件約束底下的語句。

- 只將 **`__if_not_exists`** 語句套用至簡單類型，而不是範本。

- 將 **`__if_not_exists`** 語句套用至類別內部或外部的識別碼。 請勿將語句套用 **`__if_not_exists`** 至本機變數。

- 請 **`__if_not_exists`** 只在函式主體中使用語句。 在函式主體之外， **`__if_not_exists`** 語句只能測試完整定義的類型。

- 當您對多載函式進行測試時，無法對特定形式的多載進行測試。

語句的補數 **`__if_not_exists`** 是 [__if_exists](../cpp/if-exists-statement.md) 語句。

## <a name="example"></a>範例

如需如何使用的範例 **`__if_not_exists`** ，請參閱 [__if_exists 語句](../cpp/if-exists-statement.md)。

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[__if_exists 語句](../cpp/if-exists-statement.md)
