---
title: "定義和慣例 | Microsoft Docs"
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
  - "非終端項定義"
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 定義和慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

終端是語法定義的端點。  沒有其他解決方式。  終端包括一組保留字和使用者定義的識別項。  
  
 非終端是語法中的預留位置，會在此語法摘要中的其他地方定義。  定義可以是遞迴式。  
  
 選擇性的元件會以下標的 opt 表示。  例如：  
  
```  
  
{ expression <SUB>opt</SUB> }  
```  
  
 表示放在大括號中的選擇性運算式。  
  
 語法慣例會針對語法的不同元件使用不同的字型屬性。  符號和字型如下：  
  
|屬性|說明|  
|--------|--------|  
|*nonterminal*|斜體類型表示非終端項。|  
|**const**|粗體類型的終端項為必須依下述方式輸入的常值保留字和符號。  此內容中的字元一律區分大小寫。|  
|opt|後面接著非終端頂的 opt 一律為選擇項。|  
|預設字樣|這個字樣中描述或列出的集合中的字元可用來作為 C 陳述式中的終端。|  
  
 後面接著非終端頂的冒號 \(**:**\) 會引入其定義。  除非前面加上「one of」字樣，否則替代定義另列於其他行。  
  
## 請參閱  
 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)