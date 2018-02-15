---
title: "ML 嚴重錯誤 A1010 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 553071ff10688f0b49909b16c8c60d95899247d1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ml-fatal-error-a1010"></a>ML 嚴重錯誤 A1010
**不相符的區塊的巢狀結構：**  
  
 區塊開頭沒有對應的結尾，或區塊結尾沒有相對應的開頭。 可能包含下列其中一項：  
  
-   高層級的指示詞，例如[。如果](../../assembler/masm/dot-if.md)， [。重複](../../assembler/masm/dot-repeat.md)，或[。雖然](../../assembler/masm/dot-while.md)。  
  
-   條件式組件指示詞，例如[如果](../../assembler/masm/if-masm.md)，[重複](../../assembler/masm/repeat.md)，或**時**。  
  
-   結構或等位的定義。  
  
-   程序定義。  
  
-   區段定義。  
  
-   A [POPCONTEXT](../../assembler/masm/popcontext.md)指示詞。  
  
-   條件式組件指示詞，例如[ELSE](../../assembler/masm/else-masm.md)， [ELSEIF](../../assembler/masm/elseif-masm.md)，或**ENDIF**但沒有對應的[如果](../../assembler/masm/if-masm.md)。  
  
## <a name="see-also"></a>請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)