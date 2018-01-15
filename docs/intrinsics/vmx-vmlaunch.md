---
title: "__vmx_vmlaunch |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmlaunch
dev_langs: C++
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45986af1a63f79e4466227f767fdf96fd1c2cb35
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="vmxvmlaunch"></a>__vmx_vmlaunch
**Microsoft 特定的**  
  
 使用目前的虛擬機器控制結構 (VMCS) 會將呼叫的應用程式在 VMX 非根作業狀態 （輸入 VM）。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char __vmx_vmlaunch(  
   void);  
```  
  
## <a name="return-value"></a>傳回值  
  
|值|意義|  
|-----------|-------------|  
|0|作業成功。|  
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|  
|2|作業失敗，無可用的狀態。|  
  
## <a name="remarks"></a>備註  
 應用程式可以執行 VM 輸入作業使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函數只能搭配其啟動狀態的 VMCS `Clear`，而[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函數只能搭配其啟動狀態的 VMCS `Launched`。 因此，使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函式可設定以 VMCS 的啟動狀態`Clear`，然後使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函式的第一個 VM 輸入作業和[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式，針對後續的 VM 輸入作業。  
  
 `__vmx_vmlaunch`函數即相當於`VMLAUNCH`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件，而 < Intel 虛擬化技術規格的 ia-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_vmlaunch`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)   
 [__vmx_vmclear](../intrinsics/vmx-vmclear.md)