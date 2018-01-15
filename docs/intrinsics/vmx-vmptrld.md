---
title: "__vmx_vmptrld |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmptrld
dev_langs: C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 78c6ba1a4545a03ae7f67821cf649eb936b4ed8a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld
**Microsoft 特定的**  
  
 載入到目前的虛擬機器控制結構 (VMCS) 的指標，從指定的位址。  
  
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
  
 `__vmx_vmptrld`函數即相當於`VMPTRLD`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件，而 < Intel 虛擬化技術規格的 ia-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_vmptrld`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)