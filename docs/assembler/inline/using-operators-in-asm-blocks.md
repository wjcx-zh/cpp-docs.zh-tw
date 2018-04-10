---
title: 在 __asm 區塊中使用運算子 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca8ac739793c81ef18f8657cbf53c9cb018b3e38
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="using-operators-in-asm-blocks"></a>在 __asm 區塊中使用運算子
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `__asm`區塊不能使用 C 或 c + + 特定的運算子，例如**<<**運算子。 不過，共用的運算子 C 和 MASM，例如\*運算子，會解譯為組合語言運算子。 例如，外部`__asm`封鎖，方括號 (**[]**) 會解譯為封閉陣列註標，C 自動調整大小的陣列中的項目。 在 `__asm` 區塊內，方括號會視為 MASM 索引運算子，其會產生從任何資料物件或標籤 (不只是陣列) 的未縮放位元組位移。 下列程式碼將說明這項差異：  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 `array` 的第一個參考不會加以縮放，但是第二個會加以縮放。 請注意，您可以使用**類型**進行縮放運算子依據常數。 例如，以下為相等的陳述式：  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)