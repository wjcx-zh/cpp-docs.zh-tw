---
title: __vmx_vmread |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmread
dev_langs:
- C++
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81feddd403c96d0b3f9402aaa744d0c79dbec21e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340667"
---
# <a name="vmxvmread"></a>__vmx_vmread
**Microsoft 特定的**  
  
 從目前的虛擬機器控制結構 (VMCS) 讀取指定的欄位，並將它放在指定的位置。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `Field`|要讀取的 VMCS 欄位。|  
|[輸入] `FieldValue`|從所指定的 VMCS 欄位，讀取儲存的值位置的指標`Field`參數。|  
  
## <a name="return-value"></a>傳回值  
  
|值|意義|  
|-----------|-------------|  
|0|作業成功。|  
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|  
|2|作業失敗，無可用的狀態。|  
  
## <a name="remarks"></a>備註  
 `__vmx_vmread`函數即相當於`VMREAD`機器指令。 值`Field`參數是 Intel 文件中所述的編碼的欄位索引。 如需詳細資訊，搜尋文件，而 < Intel 虛擬化技術規格的 ia-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站台，然後參閱該文件的附錄 C.  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_vmread`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)