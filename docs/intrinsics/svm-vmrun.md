---
title: "__svm_vmrun | Microsoft Docs"
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
  - "__svm_vmrun"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __svm_vmrun"
  - "VMRUN 指令"
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_vmrun
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 執行虛擬機器的來賓程式碼相對於指定的虛擬機器的控制區 \(VMCB\) 就會啟動。  
  
## 語法  
  
```  
void __svm_vmrun(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `VmcbPhysicalAddress`|VMCB 實體位址。|  
  
## 備註  
 `__svm_vmrun`函式使用 VMCB 中極少量的資訊，能開始執行的虛擬機器來賓程式碼。  使用[\_\_svm\_vmsave](../intrinsics/svm-vmsave.md)或[\_\_svm\_vmload](../intrinsics/svm-vmload.md)函式，如果您需要更多的資訊，來處理複雜的插斷，或切換至另一台來賓。  
  
 `__svm_vmrun`函式相當於`VMRUN`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋的文件中，"AMD64 架構程式設計人員手動磁碟區 2: 系統的程式設計中，「 文件編號 24593、 修訂 3.11 \(含\) 以後，在[AMD 公司](http://go.microsoft.com/fwlink/?LinkId=23746)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__svm_vmrun`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md)   
 [\_\_svm\_vmload](../intrinsics/svm-vmload.md)