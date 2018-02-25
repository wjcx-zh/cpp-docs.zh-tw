---
title: __vmx_vmwrite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08cd68256e1219df36ce6f9ea22165938fba44af
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Microsoft 特定的**  
  
 將指定的值寫入目前的虛擬機器控制結構 (VMCS) 中的指定欄位。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char __vmx_vmwrite(   
   size_t Field,  
   size_t FieldValue  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `Field`|要寫入的 VMCS 欄位。|  
|[輸入] `FieldValue`|要寫入的 VMCS 欄位的值。|  
  
## <a name="return-value"></a>傳回值  
 0  
 作業成功。  
  
 1  
 作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。  
  
 2  
 作業失敗，無可用的狀態。  
  
## <a name="remarks"></a>備註  
 `__vmx_vmwrite`函數即相當於`VMWRITE`機器指令。 值`Field`參數是 Intel 文件中所述的編碼的欄位索引。 如需詳細資訊，搜尋文件，而 < Intel 虛擬化技術規格的 ia-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)的站台、，然後再參閱旓紵 C 的文件。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_vmwrite`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)