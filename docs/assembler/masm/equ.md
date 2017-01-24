---
title: "EQU | Microsoft Docs"
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
  - "EQU"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EQU directive"
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EQU
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

第一個指示詞會指定數值的*運算式* 到 *名稱*。  
  
## 語法  
  
```  
  
      name EQU expression  
name EQU <text>  
```  
  
## 備註  
 *名稱*不能在稍後重新定義。  
  
 指定第二個指示詞評定*文字* 到 *名稱*。  *名稱* 可以指派不同的 *文字*更新。  請參閱 [TEXTEQU](../../assembler/masm/textequ.md)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)