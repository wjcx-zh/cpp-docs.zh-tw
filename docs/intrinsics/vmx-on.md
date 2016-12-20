---
title: "__vmx_on | Microsoft Docs"
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
  - "__vmx_on"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMXON 指令"
  - "內建 __vmx_on"
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_on
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 啟動虛擬機器在處理器的擴充功能 \(VMX\) 作業。  
  
## 語法  
  
```  
unsigned char __vmx_on(  
   unsigned __int64 *VmsSupportPhysicalAddress  
);  
```  
  
#### 參數  
 \[in\] `VmsSupportPhysicalAddress`  
 變數的指標，指向 \[虛擬機器的控制結構 \(VMCS\) 的 64 位元實體位址。  
  
## 傳回值  
  
|值|意義|  
|-------|--------|  
|0|操作順利完成。|  
|1|作業失敗，並在 \[可用的延伸狀態`VM-instruction error field`的目前的 VMCS。|  
|2|作業失敗，沒有可用的狀態。|  
  
## 備註  
 `__vmx_on`函數都對應至`VMXON`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋文件中，"Intel 虛擬化技術規格的 ia\-32 Intel 架構，「 文件編號 C97063\-002，在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__vmx_on`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)