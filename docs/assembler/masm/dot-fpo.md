---
title: ".FPO |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .FPO
dev_langs: C++
helpviewer_keywords: .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 61d9209b5cf817d89e9e017626222a9cc73e209e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)