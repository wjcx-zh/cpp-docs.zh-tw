---
title: __vmx_vmptrld |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrld
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f12ff4f0f109ac97f9e9e2e4f8d800455159a10b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540575"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld
**Microsoft 專屬**  
  
 載入至目前的虛擬機器控制結構 (VMCS) 的指標，從指定的位址。  
  
## <a name="syntax"></a>語法  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] *`VmcsPhysicalAddress`  
 儲存 VMCS 指標位址。  
  
## <a name="return-value"></a>傳回值  
 0  
 作業成功。  
  
 1  
 作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。  
  
 2  
 作業失敗，無可用的狀態。  
  
## <a name="remarks"></a>備註  
 VMCS 指標是 64 位元的實體位址。  
  
 `__vmx_vmptrld`函式相當於`VMPTRLD`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_vmptrld`|X64|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)