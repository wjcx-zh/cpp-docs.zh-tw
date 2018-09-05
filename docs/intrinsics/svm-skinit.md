---
title: __svm_skinit |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_skinit
dev_langs:
- C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8c59ad4af53a38ee28450e51adf9cdf81ec7bad
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687281"
---
# <a name="svmskinit"></a>__svm_skinit
**Microsoft 專屬**  
  
 啟始載入可驗證安全的軟體，例如虛擬機器監視器。  
  
## <a name="syntax"></a>語法  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`SLB`|32 位元的實體位址為 64k 位元組的安全載入器區塊 (SLB)。|  
  
## <a name="remarks"></a>備註  
 `__svm_skinit`函式相當於`SKINIT`機器指令。 此函式是使用處理器和受信任的平台模組 (TPM) 來確認，然後載入呼叫安全性核心 (SK) 的受信任的軟體安全性系統的一部分。 虛擬機器監視器是一個安全性核心的範例。 安全性系統會驗證程式元件在初始化過程中，載入並防止竄改插斷、 裝置的存取，或另一個程式，如果電腦是多處理器的元件。  
  
 `SLB`參數指定實體位址的記憶體稱為 64k 區塊*安全載入器區塊*(SLB)。 SLB 會包含呼叫安全載入器，會建立作業環境的電腦，並且後續載入安全性核心的程式。  
  
 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 文件數目 24593，修訂 3.11，位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__svm_skinit`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)