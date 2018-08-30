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
ms.openlocfilehash: 234ec5bd703a390d1e2ee60e48d99d346d4aad95
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203109"
---
# <a name="fpo"></a>.FPO
。FPO 指示詞會控制偵錯記錄至.debug$ F 區段或區段的發出。  
  
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
 本機變數，不帶正負號的 32 位元值數目。  
  
 `cdwParams`  
 DWORD，不帶正負號的 16 位元值參數的大小。  
  
 *cbProlog*  
 在函式初構程式碼，不帶正負號的 8 位元值的位元組數目。  
  
 `cbRegs`  
 數字儲存的暫存器。  
  
 `fUseBP`  
 指出是否已配置的 ebp 暫存器。 0 或 1。  
  
 *cbFrame*  
 指出畫面格型別。  請參閱[FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)