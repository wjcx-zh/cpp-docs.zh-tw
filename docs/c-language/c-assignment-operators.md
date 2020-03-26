---
title: C 指派運算子
ms.date: 06/14/2018
helpviewer_keywords:
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
ms.openlocfilehash: e8ada96daaec249a05882aceae9b7d9e86b92065
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168795"
---
# <a name="c-assignment-operators"></a>C 指派運算子

指派作業會將右方運算元的值指派到左方運算元命名的儲存位置。 因此，指派運算的左方運算元必須是可修改的左值。 在進行指派之後，指派運算式會具有左運算元的值，但不是左值。

## <a name="syntax"></a>語法

*assignment-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*一元運算式* *指派-運算子* *指派運算式*

*assignment-operator*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **=** **\*=** **/=%=+=** **-=\<** **\<=** **>>=** **>>=** **&=** **^=** **|=** **&=^=|=**

C 中的指派運算子可以在單一操作中轉換以及指派值。 C 會提供下列指派運算子：

|運算子|作業已執行|
|--------------|-------------------------|
|**=**|單一指派|
|**&#42;=**|乘法指派|
|**/=**|除法指派|
|**%=**|餘數指派|
|**+=**|加法指派|
|**-=**|減法指派|
|**<\<=**|左移指派|
|**>>=**|右移指派|
|**&=**|位元 AND 指派|
|**^=**|位元互斥 OR 指派|
|**&#124;=**|位元包含 OR 指派|

在指派之中，右方值的類型會轉換為左方值的類型，因此，在完成指派之後，值會儲存在左運算元中。 左運算元不可以是陣列、函式或常數。 特定的轉換路徑取決於轉換的兩個類型，並詳述於[類型轉換](../c-language/type-conversions-c.md)中。

## <a name="see-also"></a>另請參閱

- [指派運算子](../cpp/assignment-operators.md)
