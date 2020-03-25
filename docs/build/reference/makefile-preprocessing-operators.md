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
ms.openlocfilehash: 2276f6a3c28c6f2fac509ef0e4bc14cce9932582
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170459"
---
# <a name="makefile-preprocessing-operators"></a>Makefile 前置處理運算子

Makefile 預先處理運算式可以使用充當常數值、命令結束代碼、字串、巨集和檔案系統路徑的運算子。 若要評估運算式，預先處理器首先會展開巨集，然後執行命令，最後執行運算。 運算會先以括弧明確分組的順序，然後以運算子優先順序，來進行評估。 結果為常數值。

**定義**的運算子是作用於宏名稱的邏輯運算子。 如果已定義*macroname* ，則定義的運算式 **（** _macroname_ **）** 為 true，即使它沒有指派的值。 **定義**搭配 **！IF**或 **！如果**等於，則為; 否則為。 **IFDEF**或 **！ELSE IFDEF**。 不過，不同于這些指示詞，**定義**的可用於複雜運算式中。

「**存在**運算子」是在檔案系統路徑上作用的邏輯運算子。 如果*路徑*存在，則**存在（** _路徑_ **）** 為 true。 **存在**的結果可以在二進位運算式中使用。 如果*path*包含空格，請將其括在雙引號中。

若要比較兩個字串，請使用相等（ **==** ）運算子或不等號（ **！ =** ）運算子。 以雙引號含括字串。

整數常數可以針對數值否定（ **-** ）、一補數（ **~** ）和邏輯否定（ **！** ）使用一元運算子。

運算式可使用下列運算子。 相同優先順序的運算子會分組在一起，這些群組按優先順序從高到低列出。 一元運算子與右側運算元相關聯。 相同優先順序的二元運算子會從左向右關聯運算元。

|運算子|描述|
|--------------|-----------------|
|**已定義（** *macroname* **）**|產生*macroname*目前定義狀態的邏輯值。|
|**存在（** *路徑* **）**|產生*路徑*的檔案是否存在的邏輯值。|
|||
|**!**|一元邏輯 NOT。|
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
> 位 XOR 運算子（ **^** ）與 escape 字元相同，而且必須在運算式中使用時，以轉義（如 **^^** ）。

## <a name="see-also"></a>另請參閱

- [Makefile 前置處理中的運算式](expressions-in-makefile-preprocessing.md)
