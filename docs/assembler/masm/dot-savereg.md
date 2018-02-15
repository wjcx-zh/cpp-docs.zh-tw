---
title: .SAVEREG | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .SAVEREG
dev_langs:
- C++
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8ccd097215da57222071ad748852af46d920473
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="savereg"></a>.SAVEREG
會產生 `UWOP_SAVE_NONVOL`或`UWOP_SAVE_NONVOL_FAR`回溯程式碼項目指定的暫存器 (`reg`) 和位移 (`offset`) 使用目前的序言位移。 MASM 會選擇最有效率的編碼方式。  
  
## <a name="syntax"></a>語法  
  
```  
.SAVEREG reg, offset  
```  
  
## <a name="remarks"></a>備註  
 .SAVEREG 允許 ml64.exe 使用者指定框架的函式的會回溯，而且只允許序言，會從延伸內[PROC](../../assembler/masm/proc.md)框架宣告[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼。它們只會產生`.xdata`和`.pdata`。 .SAVEREG 之前應該加實際實作卸載動作的指示。 它是最好的作法是包裝回溯指示詞，以確保協議為了在巨集中的回溯程式碼。  
  
 如需詳細資訊，請參閱[MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)