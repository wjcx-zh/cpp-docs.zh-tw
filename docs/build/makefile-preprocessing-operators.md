---
title: "Makefile 前置處理運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59007bdabc81b5fe49aa4b5265dc0fc73ef4f0b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="makefile-preprocessing-operators"></a>Makefile 前置處理運算子
Makefile 預先處理運算式可以使用充當常數值、命令結束代碼、字串、巨集和檔案系統路徑的運算子。 若要評估運算式，預先處理器首先會展開巨集，然後執行命令，最後執行運算。 運算會先以括弧明確分組的順序，然後以運算子優先順序，來進行評估。 結果為常數值。  
  
 `DEFINED` 運算子是充當巨集名稱的邏輯運算子。 運算式`DEFINED(`*巨集名稱*`)`成立如果*巨集名稱*定義，即使它沒有指派的值。 `DEFINED` 與 `!IF` 或 `!ELSE IF` 合併相當於 `!IFDEF` 或 `!ELSE IFDEF`。 不過，與這些指示詞不同，`DEFINED` 可以在複雜運算式中使用。  
  
 `EXIST` 運算子是充當檔案系統路徑的邏輯運算子。 `EXIST(`*路徑*`)`成立如果*路徑*存在。 `EXIST` 的結果可用於二進位運算式。 如果*路徑*包含空格，請將它括在雙引號中。  
  
 若要比較兩個字串，請使用相等 (`==`) 運算子或不等 (`!=`) 運算子。 以雙引號含括字串。  
  
 整數常數可以對數值負 (`-`)、一補數 (`~`) 及邏輯負 (`!`) 使用一元運算子。  
  
 運算式可使用下列運算子。 相同優先順序的運算子會分組在一起，這些群組按優先順序從高到低列出。 一元運算子與右側運算元相關聯。 相同優先順序的二元運算子會從左向右關聯運算元。  
  
|運算子|描述|  
|--------------|-----------------|  
|`DEFINED(`*巨集名稱*`)`|產生目前定義狀態的邏輯值*巨集名稱*。|  
|`EXIST(`*路徑*`)`|產生的檔案是否存在的邏輯值*路徑*。|  
|||  
|`!`|一元邏輯 NOT。|  
|`~`|一元一補數。|  
|`-`|一元負運算。|  
|||  
|`*`|乘法。|  
|`/`|除法。|  
|`%`|模數 (餘數)。|  
|||  
|`+`|加法。|  
|`-`|減法。|  
|||  
|`<<`|位元左移。|  
|`>>`|位元右移。|  
|||  
|`<=`|小於或等於。|  
|`>=`|大於或等於。|  
|`<`|小於。|  
|`>`|大於。|  
|||  
|`==`|相等。|  
|`!=`|不等。|  
|||  
|`&`|位元 AND。|  
|`^`|位元 XOR。|  
|`&#124;`|位元 OR。|  
|||  
|`&&`|邏輯 AND。|  
|||  
|`&#124;&#124;`|邏輯 OR。|  
  
> [!NOTE]
>  位元 XOR 運算子 (`^`) 與逸出字元相同，當在運算式中使用時，必須逸出 (`^^`)。  
  
## <a name="see-also"></a>請參閱  
 [Makefile 前置處理中的運算式](../build/expressions-in-makefile-preprocessing.md)