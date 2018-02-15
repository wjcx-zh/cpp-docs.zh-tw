---
title: "如果 (MASM) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74d9d223d12164de6a908159eb0d44ea271b0be5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="if-masm"></a>IF (MASM)
授與組件的*ifstatements*如果*expression1*為 true （非零） 或*elseifstatements*如果*expression1*為 false (0) 和*expression2*為 true。  
  
## <a name="syntax"></a>語法  
  
```  
  
   IF expression1  
ifstatements  
[[ELSEIF expression2  
   elseifstatements]]  
[[ELSE  
   elsestatements]]  
ENDIF  
```  
  
## <a name="remarks"></a>備註  
 下列指示詞可能會取代為[ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**， **ELSEIFDEF**， **ELSEIFDIF**， **ELSEIFDIFI**， **ELSEIFE**， **ELSEIFIDN**， **ELSEIFIDNI**， **ELSEIFNB**，和**ELSEIFNDEF**. （選擇性） 會組譯*elsestatements*如果上一個運算式為 false。 請注意，將會評估運算式組件時。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)