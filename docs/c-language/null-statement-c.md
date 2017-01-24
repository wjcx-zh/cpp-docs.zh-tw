---
title: "Null 陳述式 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "運算式 [C++], null"
  - "null 陳述式"
  - "null 值, 運算式"
  - "冒號, C null 陳述式"
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Null 陳述式 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「null 陳述式」是一個只包含分號的陳述式，可位於陳述式會出現的任何地方。  當執行 null 陳述式時不會發生任何事。  撰寫 null 陳述式的正確方式為：  
  
## 語法  
  
```  
  
;  
  
```  
  
## 備註  
 陳述式 \(如 **do**、**for**、**if** 和 `while`\) 要求可執行的陳述式以陳述式主體的形式顯示。  在不需要實質性陳述式主體的情況下，null 陳述式就可滿足語法需求。  
  
 如同任何其他的 C 陳述式一樣，您可以在 null 陳述式前面加上標籤。  若要對不是陳述式的項目加上標籤 \(例如複合陳述式右邊的大括號\)，您可以對 null 陳述式加上標籤，並將其插入項目的前方，可獲得相同的效果。  
  
 這個範例說明 null 陳述式：  
  
```  
for ( i = 0; i < 10; line[i++] = 0 )  
     ;  
```  
  
 在此範例中，**for** 陳述式的迴圈運算式 `line[i++] = 0` 會將 `line` 的前 10 個元素初始化為 0。  由於不需要進一步的陳述式，因此陳述式主體為 null 陳述式。  
  
## 請參閱  
 [陳述式](../c-language/statements-c.md)