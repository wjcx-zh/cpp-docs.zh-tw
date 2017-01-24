---
title: "__vmx_off | Microsoft Docs"
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
  - "__vmx_off"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMXOFF 指令"
  - "內建 __vmx_off"
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_off
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 虛擬機器在處理器的擴充功能 \(VMX\) 作業則會停用。  
  
## 語法  
  
```  
void __vmx_off();  
```  
  
## 備註  
 `__vmx_off`函式相當於`VMXOFF`機器指令。  這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋文件中，"Intel 虛擬化技術規格的 ia\-32 Intel 架構，「 文件編號 C97063\-002，在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__vmx_off`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)