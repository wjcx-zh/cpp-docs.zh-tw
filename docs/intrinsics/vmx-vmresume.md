---
title: "__vmx_vmresume | Microsoft Docs"
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
  - "__vmx_vmresume"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmresume 內建"
  - "VMRESUME 指令"
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmresume
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 使用目前的虛擬機器控制結構 \(VMCS\) 繼續 VMX 非根作業。  
  
## 語法  
  
```  
unsigned char __vmx_vmresume(  
   void);  
```  
  
## 傳回值  
  
|值|意義|  
|-------|--------|  
|0|作業成功。|  
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|  
|2|作業失敗，無可用的狀態。|  
  
## 備註  
 應用程式可以使用 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 或 `__vmx_vmresume` 函式執行 VM 輸入作業。`__vmx_vmlaunch` 函式只能搭配啟動狀態為 `Clear` 的 VMCS，而 `__vmx_vmresume` 函式只能搭配啟動狀態為 `Launched` 的 VMCS。 因此，使用 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md) 函式可將 VMCS 的啟動狀態設為 `Clear`，然後第一個 VM 輸入作業使用 `__vmx_vmlaunch` 函式，後續的 VM 輸入作業使用 `__vmx_vmresume` 函式。  
  
 `__vmx_vmresume` 函式相當於 `VMRESUME` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，請搜尋 PDF 文件＜IA\-32 Intel 架構的 Intel 虛擬化技術規格＞，文件編號 C97063\-002，位於 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) 站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__vmx_vmresume`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md)