---
title: __readcr0 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr0
dev_langs:
- C++
helpviewer_keywords:
- __readcr0 intrinsic
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffb1abfadbe793f49eae53e2ee35f820c947685c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="readcr0"></a>__readcr0
**Microsoft 特定的**  
  
 讀取 CR0 暫存器，並傳回其值。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned long __readcr0(void);  /* X86 */  
unsigned __int64 __readcr0(void);  /* X64 */  
  
```  
  
## <a name="return-value"></a>傳回值  
 CR0 暫存器中的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__readcr0`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建只適用於核心模式，且此常式僅可作為內建常式使用。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)