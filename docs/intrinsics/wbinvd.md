---
title: __wbinvd |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __wbinvd
dev_langs:
- C++
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be74b466ed641474283e26217ae728c57f28edd8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="wbinvd"></a>__wbinvd
**Microsoft 特定的**  
  
 會產生回寫，以及使快取 (`wbinvd`) 指令。  
  
## <a name="syntax"></a>語法  
  
```  
void __wbinvd(void);  
```  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__wbinvd`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此函式只適用於核心模式具有特殊權限層級 (CPL) 為 0，且此常式僅可作為內建。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)