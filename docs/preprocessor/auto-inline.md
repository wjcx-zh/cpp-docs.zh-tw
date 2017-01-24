---
title: "auto_inline | Microsoft Docs"
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
  - "auto_inline_CPP"
  - "vc-pragma.auto_inline"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "auto_inline pragma"
  - "Pragma, auto_inline"
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# auto_inline
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將在指定 **off** 的範圍中定義的任何函式排除，不將其視為自動內嵌展開的候選項。  
  
## 語法  
  
```  
  
#pragma auto_inline( [{on | off}] )  
```  
  
## 備註  
 若要使用 **auto\_inline** pragma，請將其置於函式定義之前和之後 \(而非之中\)。  pragma 會在顯示該 pragma 後的第一個函式定義生效。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)