---
title: "__nop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nop 指令"
  - "內建 __nop"
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __nop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 產生會執行任何作業平台特定電腦程式碼。  
  
## 語法  
  
```  
void __nop();  
```  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__nop`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 備註  
 `__nop`函式相當於`NOP`機器指令。  如需詳細資訊，搜尋的文件中，"Intel 架構軟體開發人員的手冊，磁碟區 2： 指令集參考，"在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_noop](../intrinsics/noop.md)