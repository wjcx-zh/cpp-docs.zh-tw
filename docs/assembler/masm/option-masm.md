---
title: "選項 (MASM) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d8e8049ecea3775b9df85eb1d5c8ee5e94a9243
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
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
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**PROLOGUE**|**READONLY**|**NOREADONLY**|  
|**SCOPED**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|  
  
 語言的語法是 **選項語言: * * * x*，其中*x*是其中一個 C、 SYSCALL、 STDCALL、 PASCAL、 FORTRAN 或 BASIC。  系統呼叫、 PASCAL、 FORTRAN 和 BASIC 不支援搭配[。模型](../../assembler/masm/dot-model.md)一般。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)