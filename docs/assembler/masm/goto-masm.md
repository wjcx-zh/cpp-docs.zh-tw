---
title: GOTO (MASM) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9eecdab2fe91de0aae656b37c6fddafe658e60c0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
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
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)