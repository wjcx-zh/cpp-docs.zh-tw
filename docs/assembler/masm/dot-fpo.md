---
title: .FPO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df5185c0dc699764427989b2f46345d90ded1729
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055927"
---
# <a name="fpo"></a>.FPO
。FPO 指示詞會控制如何發出偵錯記錄，到.debug$ F 區段或區段。  
  
## <a name="syntax"></a>語法  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### <a name="parameters"></a>參數  
 `cdwLocals`  
 本機變數、 不帶正負號的 32 位元值數目。  
  
 `cdwParams`  
 DWORD，而不帶正負號的 16 位元值參數的大小。  
  
 *cbProlog*  
 在函式初構程式碼中不帶正負號的 8 位元值的位元組數目。  
  
 `cbRegs`  
 儲存的暫存器號碼。  
  
 `fUseBP`  
 指出是否已配置的 ebp 暫存器。 0 或 1。  
  
 *cbFrame*  
 表示框架類型。  請參閱[FPO_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)