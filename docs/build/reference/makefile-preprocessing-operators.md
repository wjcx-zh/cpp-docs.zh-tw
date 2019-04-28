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
ms.openlocfilehash: 4101c2fe30bcba44e9b69ed4d6d022845e6e8904
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321575"
---
# <a name="makefile-preprocessing-operators"></a>Makefile 前置處理運算子

Makefile 預先處理運算式可以使用充當常數值、命令結束代碼、字串、巨集和檔案系統路徑的運算子。 若要評估運算式，預先處理器首先會展開巨集，然後執行命令，最後執行運算。 運算會先以括弧明確分組的順序，然後以運算子優先順序，來進行評估。 結果為常數值。

**定義**運算子是充當巨集名稱的邏輯運算子。 運算式**定義 (**_macroname_**)** 成立如果*macroname*定義，即使它沒有指派的值。 **定義**結合 **！如果**或 **！ELSE IF**相當於 **！IFDEF**或 **！其他 IFDEF**。 不過，與這些指示詞，不同**定義**可以用於複雜的運算式。

**存在**運算子是充當檔案系統路徑的邏輯運算子。 **EXIST (**_路徑_**)** 成立如果*路徑*存在。 從結果**存在**可以用於二進位運算式。 如果*路徑*包含空格，將它括在雙引號中。

若要比較兩個字串，使用等號 (**==**) 運算子或不等比較 (**！ =**) 運算子。 以雙引號含括字串。

整數常數可以對數值負使用一元運算子 (**-**)、 一補數 (**~**)，及邏輯負 (**！**)。

運算式可使用下列運算子。 相同優先順序的運算子會分組在一起，這些群組按優先順序從高到低列出。 一元運算子與右側運算元相關聯。 相同優先順序的二元運算子會從左向右關聯運算元。

|運算子|描述|
|--------------|-----------------|
|**DEFINED(** *macroname* **)**|產生目前定義狀態的邏輯值*macroname*。|
|**EXIST(** *path* **)**|產生的邏輯值的檔案是否存在*路徑*。|
|||
|**\!**|一元邏輯 NOT。|
|**~**|一元一補數。|
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
|**\!=**|不等。|
|||
|**&**|位元 AND。|
|**^**|位元 XOR。|
|**&#124;**|位元 OR。|
|||
|**&&**|邏輯 AND。|
|||
|**&#124;&#124;**|邏輯 OR。|

> [!NOTE]
> 位元 XOR 運算子 (**^**) 的逸出字元相同，而且必須逸出 (作為**^^**) 在運算式中使用時。

## <a name="see-also"></a>另請參閱

- [Makefile 前置處理中的運算式](expressions-in-makefile-preprocessing.md)