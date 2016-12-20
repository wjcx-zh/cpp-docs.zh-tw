---
title: "編譯器警告 (層級 3) C4635 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4635"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4635"
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4635
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文件註解目標: XML 格式錯誤: 原因  
  
 編譯器發現 XML 標記有一些問題。  請修正問題並重新編譯。  
  
 下列範例會產生 C4635：  
  
```  
// C4635.cpp // compile with: /doc /clr /W3 /c /// <summary> /// The contents of the folder have changed. /// <summary/>   // C4635 // try the following line instead // /// </summary> public ref class Test {};  
```  
  
 請注意，這個範例的輸出顯示：**結束標記 'member' 與起始標籤 'summary' 不對稱。**  
  
 這個範例的問題在於 \<摘要\> 的結束標記格式錯誤，而且編譯器無法將其辨識為 \<摘要\> 結束標記。  編譯器在每個 \/doc 編譯中，將 \<成員\> 標記內嵌於 .xdc 檔。  因此，此處的問題在於結束標記 \<\/member\> 與編譯器之前處理的起始標記 \(\<成員\>\) 不對稱。