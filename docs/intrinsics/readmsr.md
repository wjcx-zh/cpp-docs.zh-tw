---
title: __readmsr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readmsr
dev_langs:
- C++
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26fb2637c5a92a430d72e496cabeb8f5749ccaa1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711788"
---
# <a name="readmsr"></a>__readmsr
**Microsoft 專屬**  
  
 會產生`rdmsr`的指示，它會讀取所指定的模型特定暫存`register`並傳回其值。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### <a name="parameters"></a>參數  
*register*<br/>
[in]讀取模型特定暫存器。  
  
## <a name="return-value"></a>傳回值  
 指定的暫存器中的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__readmsr`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此函式只適用於核心模式，且此常式僅可作為內建。  
  
 如需詳細資訊，請參閱 AMD 文件。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)