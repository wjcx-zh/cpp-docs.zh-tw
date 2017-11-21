---
title: "__vmx_vmclear |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmclear
dev_langs: C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aa331ebc9ae1d7d18ccb5dd613e55cb1303d4c94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="vmxvmclear"></a>__vmx_vmclear
**Microsoft 特定的**  
  
 初始化指定的虛擬機器控制結構 (VMCS)，並將其啟動狀態設為`Clear`。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `VmcsPhysicalAddress`|包含以清除 VMCS 的實體位址的 64 位元記憶體位置的指標。|  
  
## <a name="return-value"></a>傳回值  
  
|值|意義|  
|-----------|-------------|  
|0|作業成功。|  
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|  
|2|作業失敗，無可用的狀態。|  
  
## <a name="remarks"></a>備註  
 應用程式可以執行 VM 輸入作業使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函數只能搭配其啟動狀態的 VMCS `Clear`，而[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函數只能搭配其啟動狀態的 VMCS `Launched`。 因此，使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函式可設定以 VMCS 的啟動狀態`Clear`。 使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函式的第一個 VM 輸入作業和[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式，針對後續的 VM 輸入作業。  
  
 `__vmx_vmclear`函數即相當於`VMCLEAR`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件，而 < Intel 虛擬化技術規格的 ia-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_vmclear`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)