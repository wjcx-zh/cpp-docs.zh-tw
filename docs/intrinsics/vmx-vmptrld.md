---
title: "__vmx_vmptrld | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmptrld"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmptrld 內建"
  - "VMPTRLD 指令"
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmptrld
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 載入目前的虛擬機器的控制結構 \(VMCS\) 的指標，從指定的位址。  
  
## 語法  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### 參數  
 \[in 1`VmcsPhysicalAddress`  
 VMCS 指標的儲存位置的位址。  
  
## 傳回值  
 0  
 操作順利完成。  
  
 1  
 作業失敗，並在 \[可用的延伸狀態`VM-instruction error field`的目前的 VMCS。  
  
 2  
 作業失敗，沒有可用的狀態。  
  
## 備註  
 VMCS 指標是 64 位元實體位址。  
  
 `__vmx_vmptrld`函式相當於`VMPTRLD`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋文件中，"Intel 虛擬化技術規格的 ia\-32 Intel 架構，「 文件編號 C97063\-002，在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__vmx_vmptrld`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmptrst](../intrinsics/vmx-vmptrst.md)