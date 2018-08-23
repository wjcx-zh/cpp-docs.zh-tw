---
title: __vmx_vmwrite |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec022fe2d317ec38bc1d9b06f459b9efc7818c92
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538611"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Microsoft 專屬**  
  
 將指定的值寫入目前的虛擬機器控制結構 (VMCS) 中指定的欄位。  
  
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
 `__vmx_vmwrite`函式相當於`VMWRITE`機器指令。 值`Field`參數是 Intel 文件中所述的編碼的欄位索引。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)網站的 url，並請參考 旓紵 C 的文件。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_vmwrite`|X64|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)