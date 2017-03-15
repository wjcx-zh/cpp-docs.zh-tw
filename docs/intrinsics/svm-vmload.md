---
title: "__svm_vmload | Microsoft Docs"
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
  - "__svm_vmload"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __svm_vmload"
  - "VMLOAD 指令"
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_vmload
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 從指定的虛擬機器的控制區 \(VMCB\) 載入處理器狀態的子集合。  
  
## 語法  
  
```  
void __svm_vmload(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `VmcbPhysicalAddress`|VMCB 實體位址。|  
  
## 備註  
 `__svm_vmload`函式相當於`VMLOAD`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋的文件中，"AMD64 架構程式設計人員手動磁碟區 2: 系統程式設計 」 在記錄號碼 24593，修訂 3.11， [AMD 公司](http://go.microsoft.com/fwlink/?LinkId=23746)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__svm_vmload`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmrun](../intrinsics/svm-vmrun.md)   
 [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md)