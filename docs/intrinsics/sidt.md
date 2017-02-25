---
title: "__sidt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__sidt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sidt 指令"
  - "內建 __sidt"
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __sidt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將中斷描述元表 \(IDTR\) 登錄值儲存在指定的記憶體位置。  
  
## 語法  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `Destination`|儲存 IDTR 的記憶體位置的指標。|  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__sidt`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `__sidt`函式相當於`SIDT`機器指令。  如需詳細資訊，搜尋的文件中，"Intel 架構軟體開發人員的手冊，磁碟區 2： 指令集參考，"在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_lidt](../intrinsics/lidt.md)