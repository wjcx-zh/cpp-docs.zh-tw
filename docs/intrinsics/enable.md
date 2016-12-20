---
title: "_ 啟用 | Microsoft Docs"
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
  - "_enable"
  - "_enable_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ 啟用內建"
  - "啟用內建"
  - "ssm 指令"
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ 啟用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 啟用中斷。  
  
## 語法  
  
```  
void _enable(void);  
```  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_enable`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `_enable` 指示處理器設定中斷旗標。  在 x86 系統中，這個函式會產生設定中斷旗標 \(`sti`\) 指令。  
  
 這個函式只適用於核心模式。  如果在使用者模式中使用，會擲回有權限指令例外狀況。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)