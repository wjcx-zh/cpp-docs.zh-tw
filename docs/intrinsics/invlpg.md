---
title: __invlpg |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __invlpg
- __invlpg_cpp
dev_langs:
- C++
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 373e9c1f8cc24ca4de4f0a78dd75011681c78056
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="invlpg"></a>__invlpg
**Microsoft 特定的**  
  
 會產生 x86`invlpg`指令，這會使得轉譯對應緩衝區 (TLB) 失效所指向的記憶體與相關聯的頁面`Address`。  
  
## <a name="syntax"></a>語法  
  
```  
void __invlpg(  
   void* Address  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in]  `Address`  
 64 位元的位址。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__invlpg`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建`__invlpg`發出特殊權限的指令，而且僅適用於核心模式與 0 權限層級 (CPL)。  
  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)