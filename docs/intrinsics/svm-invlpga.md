---
title: __svm_invlpga | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0343222a08b1ab192be733a1f583cc287a9d3377
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="svminvlpga"></a>__svm_invlpga
**Microsoft 特定的**  
  
 使電腦的轉譯後備緩衝區中的位址對應項目。 參數會指定的虛擬位址和位址空間識別碼使頁面。  
  
## <a name="syntax"></a>語法  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `Va`|要使頁面的虛擬位址。|  
|[輸入] `ASID`|位址空間 (ASID) 頁面的識別碼失效。|  
  
## <a name="remarks"></a>備註  
 `__svm_invlpga`函數即相當於`INVLPGA`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 在文件編號 24593，修訂 3.11， [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__svm_invlpga`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)