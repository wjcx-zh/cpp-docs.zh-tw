---
title: 選項 (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2dcbc55d6a2d033cde3b6189618afd67bdc3fb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221505"
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
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**序言**|**唯讀**|**NOREADONLY**|  
|**範圍**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|  
  
 語言的語法是**選項的語言：**<em>x</em>，其中*x*是 C，SYSCALL、 STDCALL、 PASCAL、 FORTRAN、 或 BASIC 的其中一個。  SYSCALL、 PASCAL、 FORTRAN、 BASIC 不支援與搭配[。模型](../../assembler/masm/dot-model.md)一般。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)