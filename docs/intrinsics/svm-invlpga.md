---
title: "__svm_invlpga | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_invlpga"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __svm_invlpga"
  - "INVLPGA 指令"
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_invlpga
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會導致無效的地址對應項目，在電腦的轉換後備緩衝區中。  參數會指定虛擬位址，並使資料頁的地址空間識別項。  
  
## 語法  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `Va`|若要使頁面的虛擬位址。|  
|\[in\] `ASID`|地址空間 \(ASID\) 的識別項的頁面，以使其失效。|  
  
## 備註  
 `__svm_invlpga`函式相當於`INVLPGA`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋的文件中，"AMD64 架構程式設計人員手動磁碟區 2: 系統程式設計 」 在記錄號碼 24593，修訂 3.11， [AMD 公司](http://go.microsoft.com/fwlink/?LinkId=23746)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__svm_invlpga`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)