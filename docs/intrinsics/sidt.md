---
title: __sidt |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29e41b0edd9b2a3da1046888f16a55e19f2d9f20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324508"
---
# <a name="sidt"></a>__sidt
**Microsoft 特定的**  
  
 將中斷描述元資料表 (IDTR) 登錄值儲存在指定的記憶體位置。  
  
## <a name="syntax"></a>語法  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `Destination`|儲存 IDTR 記憶體位置指標。|  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__sidt`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `__sidt`函數即相當於`SIDT`機器指令。 如需詳細資訊，搜尋文件中，「 Intel 架構軟體開發人員的手動、 磁碟區 2： 指令集的參考，「 在[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站台。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__lidt](../intrinsics/lidt.md)