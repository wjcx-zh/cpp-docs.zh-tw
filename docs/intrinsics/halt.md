---
title: "__halt | Microsoft Docs"
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
  - "__halt"
  - "__halt_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __halt"
  - "HLT 指令"
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __halt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 之前已啟用插斷、 非遮罩式插斷 \(NMI\) 或重設，會暫止微處理器。  
  
## 語法  
  
```  
void __halt( void );  
```  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__halt`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `__halt`函式相當於`HLT`機器指令，並僅適用於核心模式。  如需詳細資訊，搜尋的文件中，"Intel 架構軟體開發人員的手冊，磁碟區 2： 指令集參考，"在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)