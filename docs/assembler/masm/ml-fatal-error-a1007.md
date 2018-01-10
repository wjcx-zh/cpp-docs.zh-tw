---
title: "ML 嚴重錯誤 A1007 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1007
dev_langs: C++
helpviewer_keywords: A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 619f1eae458b52eb7851118d6702dccec769a1ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1007"></a>ML 嚴重錯誤 A1007
**太深的巢狀層級**  
  
 組譯工具已達到其巢狀限制。 限制為 20 的層級，除非註明否則。  
  
 下列其中一種是巢狀結構太深：  
  
-   高層級的指示詞，例如[。如果](../../assembler/masm/dot-if.md)， [。重複](../../assembler/masm/dot-repeat.md)，或[。雖然](../../assembler/masm/dot-while.md)。  
  
-   結構定義。  
  
-   條件式組件指示詞。  
  
-   程序定義。  
  
-   A [PUSHCONTEXT](../../assembler/masm/pushcontext.md)指示詞 （限制為 10）。  
  
-   區段定義。  
  
-   Include 檔。  
  
-   巨集。  
  
## <a name="see-also"></a>請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)