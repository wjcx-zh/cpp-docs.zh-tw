---
title: "__svm_stgi | Microsoft Docs"
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
  - "__svm_stgi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_stgi 內建"
  - "STGI 指令"
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_stgi
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 設定通用的插斷旗標。  
  
## 語法  
  
```  
void __svm_stgi(void);  
```  
  
## 備註  
 `__svm_stgi`函式相當於`STGI`機器指令。  通用的插斷旗標決定微處理器會略過、 方面會延，或處理事件，例如 I\/O 完成、 硬體溫度警示或偵錯例外受限於插斷。  
  
 這個函式會以來賓作業系統與它的應用程式支援主應用程式的虛擬機器監視器的互動。  如需詳細資訊，搜尋的文件中，"AMD64 架構程式設計人員手動磁碟區 2: 系統程式設計 」 在記錄號碼 24593，修訂 3.11， [AMD 公司](http://go.microsoft.com/fwlink/?LinkId=23746)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__svm_stgi`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_clgi](../intrinsics/svm-clgi.md)