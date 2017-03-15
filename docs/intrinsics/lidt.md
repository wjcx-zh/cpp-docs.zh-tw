---
title: "__lidt | Microsoft Docs"
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
  - "__lidt"
  - "__lidt_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIDT 指令"
  - "內建 __lidt"
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __lidt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 載入中斷描述元表登錄 \(IDTR\) 與指定的記憶體位置中的值。  
  
## 語法  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `Source`|要複製到 IDTR 的值指標。|  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__lidt`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `__lidt`函式相當於`LIDT`機器指令，並僅適用於核心模式。  如需詳細資訊，搜尋的文件中，"Intel 架構軟體開發人員的手冊，磁碟區 2： 指令集參考，"在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_sidt](../intrinsics/sidt.md)