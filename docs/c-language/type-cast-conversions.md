---
title: 類型轉換
ms.date: 11/04/2016
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
ms.openlocfilehash: cc2b6d87d6fedf8d36373c901cdb6a6ba8b5f0e7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231451"
---
# <a name="type-cast-conversions"></a>類型轉換

您可以使用類型轉換明確地轉換類型。

**語法**

*cast-運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*一元運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**（**  *類型名稱*  **）**  *cast 運算式*

*類型名稱*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *abstract-declarator*<sub>opt</sub>

*type-name* 是一種類型，而 *cast-expression*是要轉換為該類型的值。 具有類型轉換的運算式不是左值。 *cast-expression* 會根據其指派給類型 *type-name* 的變數進行轉換。 指派的轉換規則 (於[指派轉換](../c-language/assignment-conversions.md)中說明) 也適用於類型轉換。 下表顯示可以轉換為任何指定類型的類型。

### <a name="legal-type-casts"></a>合法的類型轉換

|目的類型|潛在來源|
|-----------------------|-----------------------|
|整數類資料型別|任何整數類型或浮點類型，或物件的指標|
|浮點|任何算術類型|
|物件的指標，或（ **`void`** <strong>\*</strong> ）|任何整數類型、（ **`void`** <strong>\*</strong> ）、物件的指標，或函式指標|
|函式指標|任何整數類型、物件的指標，或函式指標|
|結構、等位或陣列|無|
|Void 類型|任何型別|

任何識別碼都可以轉換成 **`void`** 類型。 不過，如果類型轉換運算式中指定的類型不是，則 **`void`** 轉換成該類型的識別碼不可以是 **`void`** 運算式。 任何運算式都可以轉換成 **`void`** ，但是類型的運算式 **`void`** 無法轉換成任何其他類型。 例如，具有傳回類型的 **`void`** 函式不能將其傳回轉換成另一個類型。

請注意 **`void`** <strong>\*</strong> ，運算式具有的類型指標 **`void`** ，而不是類型 **`void`** 。 如果物件轉換成型別 **`void`** ，則產生的運算式無法指派給任何專案。 同樣地，類型轉換物件無法接受左值，因此無法對類型轉換物件進行指派。

**Microsoft 特定的**

只要識別項的大小不會變更，類型轉換可以是左值運算式。 如需左值運算式的詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。

**結束 Microsoft 專有**

您可以使用轉換將運算式轉換成類型 **`void`** ，但是產生的運算式只能用在不需要值的位置。 轉換成 **`void`** <strong>\*</strong> 原始類型的物件指標會回到其原始值。

## <a name="see-also"></a>另請參閱

[類型轉換](../c-language/type-conversions-c.md)
