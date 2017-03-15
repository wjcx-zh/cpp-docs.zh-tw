---
title: "__svm_skinit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_skinit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SKINIT 指令"
  - "內建 __svm_skinit"
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __svm_skinit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 啟動可驗證安全的軟體，例如虛擬機器監視器的載入。  
  
## 語法  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`SLB`|64K 位元組的 32 位元實體位址安全載入器區塊 \(SLB\)。|  
  
## 備註  
 `__svm_skinit`函式相當於`SKINIT`機器指令。  這個函數是以驗證並載入受信任的軟體，稱為安全性核心 \(SK\) 會使用處理器和受信任的平台模組 \(TPM\) 安全性系統的一部份。  虛擬機器監視器是安全性核心的範例。  安全性系統驗證程式元件載入期間初始化程序，防止他人篡改插斷、 裝置存取權或另一個程式如果是多處理器的電腦元件。  
  
 `SLB`參數會指定 64k 記憶體區塊的呼叫的實體位址*安全載入器區塊* \(SLB\)。  SLB 包含稱為安全載入器所建立的作業環境的電腦\]，並接著載入安全性核心的程式。  
  
 這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋的文件中，"AMD64 架構程式設計人員手動磁碟區 2: 系統程式設計 」 在記錄號碼 24593，修訂 3.11， [AMD 公司](http://go.microsoft.com/fwlink/?LinkId=23746)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__svm_skinit`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)