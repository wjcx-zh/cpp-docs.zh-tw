---
title: "__readeflags | Microsoft Docs"
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
  - "__readeflags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readeflags 內建"
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __readeflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

讀取程式狀態和控制項 \(EFLAGS\) 註冊。  
  
## 語法  
  
```  
unsigned     int __readeflags(void);  
unsigned __int64 __readeflags(void);  
```  
  
## 傳回值  
 EFLAGS 暫存器值。  傳回值是 32 位元長在 32 位元平台與 64 位元長度在 64 位元平台。  
  
## 備註  
 這些常式會僅當作內建函式。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__readeflags`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_writeeflags](../intrinsics/writeeflags.md)