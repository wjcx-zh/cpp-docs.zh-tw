---
title: __if_not_exists 陳述式
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 7372ac127a7b4dd5c05d58cfecca25f87690b0ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178171"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists 陳述式

**__If_not_exists**語句會測試指定的識別碼是否存在。 如果識別項不存在，就會執行指定的陳述式區塊。

## <a name="syntax"></a>語法

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*identifier*|要測試其是否存在的識別項。|
|*報表*|如果*識別碼*不存在，要執行的一或多個語句。|

## <a name="remarks"></a>備註

> [!CAUTION]
>  若要達到最可靠的結果，請使用下列條件約束底下的 **__if_not_exists**語句。

- 只將 **__if_not_exists**語句套用至簡單類型，而不套用至範本。

- 將 **__if_not_exists**語句套用至類別內部或外部的識別碼。 請勿將 **__if_not_exists**語句套用至本機變數。

- 請只在函式主體中使用 **__if_not_exists**語句。 在函式的主體之外， **__if_not_exists**語句只能測試完整定義的類型。

- 當您對多載函式進行測試時，無法對特定形式的多載進行測試。

**__If_not_exists**語句的補數是[__if_exists](../cpp/if-exists-statement.md)語句。

## <a name="example"></a>範例

如需如何使用 **__if_not_exists**的範例，請參閱[__if_exists 語句](../cpp/if-exists-statement.md)。

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[__if_exists 陳述式](../cpp/if-exists-statement.md)
