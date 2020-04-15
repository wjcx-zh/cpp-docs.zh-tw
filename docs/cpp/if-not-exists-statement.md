---
title: __if_not_exists 陳述式
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 1118f9fcca525b2b2d5869fb507ee974d2b0d28f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374132"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists 陳述式

**__if_not_exists**語句測試指定的標識符是否存在。 如果識別項不存在，就會執行指定的陳述式區塊。

## <a name="syntax"></a>語法

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*識別碼*|要測試其是否存在的識別項。|
|*語句*|如果*識別符*不存在,要執行的一個或多個語句。|

## <a name="remarks"></a>備註

> [!CAUTION]
> 要獲得最可靠的結果,請使用以下約束下的 **__if_not_exists**語句。

- 將 **__if_not_exists**語句僅應用於簡單類型,而不是範本。

- 將 **__if_not_exists**語句應用於類內部或外部的標識碼。 不要將 **__if_not_exists**語句應用於局部變數。

- 僅在函數正文中使用 **__if_not_exists**語句。 在函數的正文之外 **,__if_not_exists**語句只能測試完全定義的類型。

- 當您對多載函式進行測試時，無法對特定形式的多載進行測試。

**__if_not_exists**語句的補充是[__if_exists](../cpp/if-exists-statement.md)語句。

## <a name="example"></a>範例

有關如何使用 **__if_not_exists**的範例,請參閱[__if_exists 語句](../cpp/if-exists-statement.md)。

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[__if_exists 陳述式](../cpp/if-exists-statement.md)
