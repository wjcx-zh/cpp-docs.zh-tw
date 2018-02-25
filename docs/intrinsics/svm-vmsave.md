---
title: __svm_vmsave | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_vmsave
dev_langs:
- C++
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa5ebe1841522da8a5e2a62ae71ebb9d04b2865
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="svmvmsave"></a>__svm_vmsave
**Microsoft 特定的**  
  
 指定的虛擬機器控制區 (VMCB) 中儲存處理器狀態的子集。  
  
## <a name="syntax"></a>語法  
  
```  
void __svm_vmsave(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `VmcbPhysicalAddress`|VMCB 實體位址。|  
  
## <a name="remarks"></a>備註  
 `__svm_vmsave`函數即相當於`VMSAVE`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計 」 文件編號 24593、 修訂 3.11 或更新版本，在[AMD Corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__svm_vmsave`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)