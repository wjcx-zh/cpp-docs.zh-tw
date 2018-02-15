---
title: "ML 非嚴重錯誤 A2085 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29d0d58e5cd65c16c848b3cc05e10b9f57488639
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非嚴重錯誤 A2085
**指示或在目前的 CPU 模式中不被接受的暫存器**  
  
 您嘗試使用指示、 暫存器或目前的處理器模式中無效的關鍵字。  
  
 例如，32 位元暫存器需要[.386](../../assembler/masm/dot-386.md)或更新版本。 控制暫存器，例如 CR0 需要特殊權限的模式[.386P](../../assembler/masm/dot-386p.md)或更新版本。 此錯誤也可能產生的**NEAR32**， **FAR32**，和**一般**需要的關鍵字。**386**或更新版本。  
  
## <a name="see-also"></a>請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)