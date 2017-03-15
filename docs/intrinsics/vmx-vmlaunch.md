---
title: "__vmx_vmlaunch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmlaunch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMLAUNCH 指令"
  - "__vmx_vmlaunch 內建"
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmlaunch
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 使用目前的虛擬機器的控制結構 \(VMCS\) 會將放在 VMX 非根作業狀態 \(輸入 VM\) 呼叫的應用程式。  
  
## 語法  
  
```  
unsigned char __vmx_vmlaunch(  
   void);  
```  
  
## 傳回值  
  
|值|意義|  
|-------|--------|  
|0|操作順利完成。|  
|1|作業失敗，並在 \[可用的延伸狀態`VM-instruction error field`的目前的 VMCS。|  
|2|作業失敗，沒有可用的狀態。|  
  
## 備註  
 應用程式可以執行 VM 輸入操作使用[\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)函式。  [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md)函數只能用於啟動狀態如下的 VMCS `Clear`，以及[\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)函式只能搭配啟動狀態如下的 VMCS `Launched`。  因此，使用[\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md)函式來設定啟動的狀態為 VMCS `Clear`，然後使用[\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md)的第一次的 VM 輸入作業的函式和[\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)函式進行後續的 VM 輸入操作。  
  
 `__vmx_vmlaunch`函式相當於`VMLAUNCH`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋文件中，"Intel 虛擬化技術規格的 ia\-32 Intel 架構，「 文件編號 C97063\-002，在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__vmx_vmlaunch`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)   
 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md)