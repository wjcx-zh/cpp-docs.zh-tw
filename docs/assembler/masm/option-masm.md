---
title: "選項 (MASM) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: option
dev_langs: C++
helpviewer_keywords: OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f449606b143bfbf188e878b261f3d35017846862
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="option-masm"></a>OPTION (MASM)
啟用和停用 「 組合器 」 的功能。  
  
## <a name="syntax"></a>語法  
  
```  
  
OPTION   
optionlist  
  
```  
  
## <a name="remarks"></a>備註  
 可用的選項包括：  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**模擬器**|  
|**NOEMULATOR**|**結尾**|**EXPR16**|**EXPR32**|  
|**語言**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**位移**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**序言**|**READONLY**|**NOREADONLY**|  
|**範圍**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|  
  
 語言的語法是**選項語言：***x*，其中*x*是其中一個 C、 SYSCALL、 STDCALL、 PASCAL、 FORTRAN 或 BASIC。  系統呼叫、 PASCAL、 FORTRAN 和 BASIC 不支援搭配[。模型](../../assembler/masm/dot-model.md)一般。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)