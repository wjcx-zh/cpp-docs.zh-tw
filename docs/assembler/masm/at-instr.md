---
title: "@InStr | Microsoft Docs"
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
  - "@InStr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "@InStr symbol"
ms.assetid: 980d5b9f-2b88-4306-8955-df6cd2133e68
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# @InStr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找第一個出現位置的巨集函式 *string2* 在 *string1*、 開始在 *位置* 內  *string1*。  如果*位置* 沒有出現，在開始處開始搜尋  *string1*。  傳回一個位置的整數，則為 0，如果 *string2* 找不到。  
  
## 語法  
  
```  
  
@InStr( [[position]], string1, string2 )  
```  
  
## 請參閱  
 [Symbols Reference](../../assembler/masm/symbols-reference.md)