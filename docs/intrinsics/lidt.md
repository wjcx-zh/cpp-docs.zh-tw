---
title: __lidt |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5184d925e5d6712dd547e34341d84919c50e0a43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724707"
---
# <a name="lidt"></a>__lidt
**Microsoft 專屬**  
  
 載入中斷描述項表登錄 (IDTR) 中指定的記憶體位置的值。  
  
## <a name="syntax"></a>語法  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*Source*|[in]要複製到 IDTR 值指標。|  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__lidt`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `__lidt`函式相當於`LIDT`機器指令，且只適用於核心模式。 如需詳細資訊，搜尋文件中，「 Intel 架構軟體開發人員的手動、 磁碟區 2： 指令集參考，「 在[Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm)站台。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__sidt](../intrinsics/sidt.md)