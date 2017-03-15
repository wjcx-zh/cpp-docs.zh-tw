---
title: "ALIAS (MASM) | Microsoft Docs"
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
  - "Alias"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALIAS directive"
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ALIAS (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**別名**指示詞會建立一個函式的替代名稱。  這可讓您建立多個函式的名稱，或建立文件庫，可讓連結器 \(LINK.exe\) 將舊的函式對應到新的函式。  
  
## 語法  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### 參數  
 `actual-name`  
 函式或程序的實際名稱。  角括弧是必要的。  
  
 `alias`  
 其他名稱或別名名稱。  角括弧是必要的。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)