---
title: "事件 &#39;&lt;事件名稱1&gt;&#39; 無法實作事件 &#39;&lt;事件名稱2&gt;&#39;，因為其委派類型與其他以 &#39;&lt;事件名稱1&gt;&#39; 實作的事件之委派類型不相符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31407"
  - "vbc31407"
helpviewer_keywords: 
  - "BC31407"
ms.assetid: 0b9ffddb-4759-438b-b569-beac7062e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件 &#39;&lt;事件名稱1&gt;&#39; 無法實作事件 &#39;&lt;事件名稱2&gt;&#39;，因為其委派類型與其他以 &#39;&lt;事件名稱1&gt;&#39; 實作的事件之委派類型不相符
[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法實作事件，因為事件的委派類型與其他事件的委派類型不相符。 如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。 只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。  
  
 **錯誤 ID︰**BC31407  
  
### 更正這個錯誤  
  
-   請分別實作這些事件。  
  
## 請參閱  
 [Events](../Topic/Events%20\(Visual%20Basic\).md)