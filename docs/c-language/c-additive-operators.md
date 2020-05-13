---
title: C 加法類運算子
ms.date: 10/18/2018
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
ms.openlocfilehash: 29bea87e56aa90a8deab7ad7280b3fbdfb45c82b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326896"
---
# <a name="c-additive-operators"></a>C 加法類運算子

加法類運算子會執行加法**+**（）和減法**-**（）。

## <a name="syntax"></a>語法

*加法類運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*加法運算式* **+** *乘法運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*加法運算式* **-** *乘法運算式*

> [!NOTE]
> 雖然 *additive-expression* 的語法包括 *multiplicative-expression*，但這並不表示需要使用乘法的運算式。 請參閱 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)中有關 *multiplicative-expression*、*cast-expression* 和 *unary-expression* 的語法。

運算元可以是整數值或浮點值。 某些加法類運算也可以在指標值上執行，如每個運算子的討論中所述。

加法類運算子會對整數和浮點運算元執行一般算術轉換。 結果的類型是轉換後的運算元類型。 由於加法類運算子所執行的轉換不提供溢位或反向溢位條件，因此，如果加法類運算的結果無法以運算元轉換後的類型表示，則可能會遺失資訊。

## <a name="see-also"></a>請參閱

[加法類運算子：+ 和 -](../cpp/additive-operators-plus-and.md)
