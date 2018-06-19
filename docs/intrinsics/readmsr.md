---
title: __readmsr |Microsoft 文件
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
ms.openlocfilehash: 4e8196b25b1507c92542faa6dd8ca59b4632d8f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335909"
---
# <a name="readmsr"></a>__readmsr
**Microsoft 特定的**  
  
 會產生`rdmsr`指令，讀取所指定的模型特定暫存`register`並傳回其值。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `register`  
 讀取模型特定暫存器。  
  
## <a name="return-value"></a>傳回值  
 指定的暫存器中的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__readmsr`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此函式只適用於核心模式，且此常式僅可作為內建。  
  
 如需詳細資訊，請參閱 AMD 文件。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)