---
title: 選項 (MASM) |Microsoft 文件
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
ms.openlocfilehash: 80291c805cad3ef041fffc58983ff399da07c9d9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057717"
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
|**PROC**|**序言**|**READONLY**|**NOREADONLY**|  
|**範圍**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|  
  
 語言的語法是 **選項語言: * * * x*，其中*x*是其中一個 C、 SYSCALL、 STDCALL、 PASCAL、 FORTRAN 或 BASIC。  系統呼叫、 PASCAL、 FORTRAN 和 BASIC 不支援搭配[。模型](../../assembler/masm/dot-model.md)一般。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)