---
title: GOTO (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c86a9b5bc83110f20dccf73f51b1e1aabc693db2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="goto-masm"></a>GOTO (MASM)
將組件傳送至標記的一行 **: * * * macrolabel*。  
  
## <a name="syntax"></a>語法  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## <a name="remarks"></a>備註  
 **GOTO**只允許在[巨集](../../assembler/masm/macro.md)，[如](../../assembler/masm/for-masm.md)， [FORC](../../assembler/masm/forc.md)，[重複](../../assembler/masm/repeat.md)，和**時**區塊。 標籤必須是該行的唯一指示詞，而且前面必須有開頭的冒號。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)