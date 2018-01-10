---
title: "__svm_skinit |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_skinit
dev_langs: C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e02bafc9319a6a3a4c5e07b46c9da6586f440d59
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="svmskinit"></a>__svm_skinit
**Microsoft 特定的**  
  
 開始可驗證安全軟體，例如虛擬機器監視器載入。  
  
## <a name="syntax"></a>語法  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`SLB`|64k 位元組的 32 位元實體位址安全載入器區塊 (SLB)。|  
  
## <a name="remarks"></a>備註  
 `__svm_skinit`函數即相當於`SKINIT`機器指令。 此函式是使用驗證，並載入受信任的軟體，稱為安全性核心 (SK) 的處理器和受信任的平台模組 (TPM) 的安全性系統的一部分。 虛擬機器監視器是安全性核心的範例。 安全性系統會驗證程式元件在初始化過程中，載入並防止竄改插斷、 裝置存取，或另一個程式中，如果電腦是多處理器元件。  
  
 `SLB`參數指定實體位址 64k 區塊的記憶體稱為*安全載入器區塊*(SLB)。 SLB 包含呼叫可建立為電腦作業環境及後續載入安全性核心安全載入器的程式。  
  
 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 在文件編號 24593，修訂 3.11， [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__svm_skinit`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)