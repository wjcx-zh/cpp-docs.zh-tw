---
title: "__svm_vmsave | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_vmsave"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMSAVE 指令"
  - "__svm_vmsave 內建"
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# __svm_vmsave
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 指定的虛擬機器的控制區 \(VMCB\) 中儲存處理器狀態的子集合。  
  
## 語法  
  
```  
void __svm_vmsave(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `VmcbPhysicalAddress`|VMCB 實體位址。|  
  
## 備註  
 `__svm_vmsave`函式相當於`VMSAVE`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋的文件中，"AMD64 架構程式設計人員手動磁碟區 2: 系統的程式設計中，「 文件編號 24593、 修訂 3.11 \(含\) 以後，在[AMD 公司](http://go.microsoft.com/fwlink/?LinkId=23746)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__svm_vmsave`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmrun](../intrinsics/svm-vmrun.md)   
 [\_\_svm\_vmload](../intrinsics/svm-vmload.md)