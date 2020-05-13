---
title: Makefile 前置處理運算子
ms.date: 06/14/2018
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
ms.openlocfilehash: 212f39ee62008b391977aaa91d5c8c4fadfd9730
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336463"
---
# <a name="makefile-preprocessing-operators"></a>Makefile 前置處理運算子

Makefile 預先處理運算式可以使用充當常數值、命令結束代碼、字串、巨集和檔案系統路徑的運算子。 若要評估運算式，預先處理器首先會展開巨集，然後執行命令，最後執行運算。 運算會先以括弧明確分組的順序，然後以運算子優先順序，來進行評估。 結果為常數值。

**定義**運算符是一個邏輯運算符,作用於宏名稱。 如果定義了*宏名*,則表達式**DEFINED(**_宏名_**)** 為 true,即使它沒有賦值也是如此。 **與** **!IF**或 **!ELSE IF**等效於 **!IFDEF**或 **!否則IFDEF**. 但是,與這些指令不同 **,DEFINED**可用於複雜的運算式。

**存在**運算子是一個邏輯運算符,作用於文件系統路徑。 如果*路徑*存在,**則存在(**_路徑_**)。** **存在**的結果可用於二進位表達式。 如果*路徑*包含空格,則用雙引弧括上路徑。

要比較兩個字串,請使用相等**==**( ) 運算子或不等式 (**!***) 運算符。 以雙引號含括字串。

整數常數可以使用一元運算元進行數值否定 ()、**-** 一個人的補數 ()**~** 和邏輯否定 **(!**

運算式可使用下列運算子。 相同優先順序的運算子會分組在一起，這些群組按優先順序從高到低列出。 一元運算子與右側運算元相關聯。 相同優先順序的二元運算子會從左向右關聯運算元。

|運算子|描述|
|--------------|-----------------|
|**定義(***巨集名***)**|為*宏名*的當前定義狀態生成邏輯值。|
|**存在(***路徑***)**|為*路徑*上存在檔生成邏輯值。|
|||
|**!**|一元邏輯 NOT。|
|**~**|一元的補充。|
|**-**|一元負運算。|
|||
|**&#42;**|乘法。|
|**/**|除法。|
|**%**|模數 (餘數)。|
|||
|**+**|加法。|
|**-**|減法。|
|||
|**\<\<**|位元左移。|
|**>>**|位元右移。|
|||
|**\<=**|小於或等於。|
|**>=**|大於或等於。|
|**\<**|小於。|
|**>**|大於。|
|||
|**==**|相等。|
|**!=**|不等。|
|||
|**&**|位元 AND。|
|**^**|位元 XOR。|
|**&#124;**|位元 OR。|
|||
|**&&**|邏輯 AND。|
|||
|**&#124;&#124;**|邏輯 OR。|

> [!NOTE]
> XOR 運算子**^**( ) 與轉義字元相同,並且在表示式中使用**^^** 時必須 轉義 (如 )

## <a name="see-also"></a>另請參閱

- [Makefile 前置處理中的運算式](expressions-in-makefile-preprocessing.md)
