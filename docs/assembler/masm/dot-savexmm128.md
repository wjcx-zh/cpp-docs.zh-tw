---
title: ".SAVEXMM128 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEXMM128
dev_langs: C++
helpviewer_keywords: .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 384615a0c58c3c28a2e0958d6909546f5753ce6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="savexmm128"></a>.SAVEXMM128
會產生 `UWOP_SAVE_XMM128`或`UWOP_SAVE_XMM128_FAR`回溯程式碼項目指定 xmm 暫存器和位移使用目前的序言位移。 MASM 會選擇最有效率的編碼方式。  
  
## <a name="syntax"></a>語法  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## <a name="remarks"></a>備註  
 .SAVEXMM128 允許 ml64.exe 使用者指定框架的函式的回溯時，如何，而且只允許序言，會從延伸內[PROC](../../assembler/masm/proc.md)框架宣告[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼。它們只會產生`.xdata`和`.pdata`。 .SAVEXMM128 之前應該加實際實作卸載動作的指示。 它是最好的作法是包裝回溯指示詞，以確保協議為了在巨集中的回溯程式碼。  
  
 `offset`必須是 16 的倍數。  
  
 如需詳細資訊，請參閱[MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)