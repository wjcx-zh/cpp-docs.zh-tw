---
title: "Makefile 前置處理運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINED 運算子"
  - "EXIST 運算子"
  - "Makefile, 前置處理運算子"
  - "NMAKE 程式, 運算子"
  - "運算子 [C++], Makefile 前置處理"
  - "前置處理 NMAKE Makefile 運算子"
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Makefile 前置處理運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Makefile 預先處理運算式可以使用充當常數值、命令結束代碼、字串、巨集和檔案系統路徑的運算子。  若要評估運算式，預先處理器首先會展開巨集，然後執行命令，最後執行運算。  運算會先以括弧明確分組的順序，然後以運算子優先順序，來進行評估。  結果為常數值。  
  
 `DEFINED` 運算子是充當巨集名稱的邏輯運算子。  如果已定義 *macroname*，則運算式 `DEFINED(`*macroname*`)` 為 true，即使它沒有已指派的值也是一樣。  `DEFINED` 與 `!IF` 或 `!ELSE IF` 合併相當於 `!IFDEF` 或 `!ELSE IFDEF`。  不過，與這些指示詞不同，`DEFINED` 可以在複雜運算式中使用。  
  
 `EXIST` 運算子是充當檔案系統路徑的邏輯運算子。  如果 *path* 存在的話，則 `EXIST(`*path*`)` 為 true。  `EXIST` 的結果可用於二進位運算式。  如果 *path* 包含空格，請將其含括在雙引號中。  
  
 若要比較兩個字串，請使用相等 \(`==`\) 運算子或不等 \(`!=`\) 運算子。  以雙引號含括字串。  
  
 整數常數可以對數值負 \(`–`\)、一補數 \(`~`\) 及邏輯負 \(`!`\) 使用一元運算子。  
  
 運算式可使用下列運算子。  相同優先順序的運算子會分組在一起，這些群組按優先順序從高到低列出。  一元運算子與右側運算元相關聯。  相同優先順序的二元運算子會從左向右關聯運算元。  
  
|運算子|描述|  
|---------|--------|  
|`DEFINED(` *macroname* `)`|產生 *macroname* 目前定義狀態的邏輯值。|  
|`EXIST(` *path* `)`|產生 *path* 處所存在檔案的邏輯值。|  
|||  
|`!`|一元邏輯 NOT。|  
|`~`|一元一補數。|  
|`-`|一元負運算。|  
|||  
|`*`|乘法。|  
|`/`|除法。|  
|`%`|模數 \(餘數\)。|  
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
>  位元 XOR 運算子 \(`^`\) 與逸出字元相同，當在運算式中使用時，必須逸出 \(`^^`\)。  
  
## 請參閱  
 [Makefile 前置處理中的運算式](../build/expressions-in-makefile-preprocessing.md)