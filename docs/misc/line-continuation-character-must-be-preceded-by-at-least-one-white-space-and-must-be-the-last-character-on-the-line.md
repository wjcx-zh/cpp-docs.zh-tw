---
title: "行接續字元 &#39;_&#39; 之前必須搭配至少一個空白字元，並且必須是該行的最後一個字元 | Microsoft Docs"
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
  - "vbc30999"
  - "bc30999"
helpviewer_keywords: 
  - "BC30999"
ms.assetid: 32caf62f-52e4-4acd-b40f-5af65e42e643
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 行接續字元 &#39;_&#39; 之前必須搭配至少一個空白字元，並且必須是該行的最後一個字元
您可以使用行接續字元 \(即底線 \(\_\)\)，將檔案中很長的一行程式碼分為數行。 底線的前面必須緊接一個空格，後面則必須緊接著行結束字元 \(歸位字元\)。 例如:  
  
```  
Dim books As XDocument = _ XDocument.Load(My.Application.Info.DirectoryPath & _ "\..\..\Data\books.xml")  
```  
  
 **錯誤 ID︰**BC30999  
  
### 更正這個錯誤  
  
1.  請確定行接續字元 \(\_\) 是一行程式碼的最後一個字元。  
  
2.  確定行接續字元前面有一個空格，以與該行上的任何其他程式碼進行區隔。  
  
## 請參閱  
 [如何：在程式碼中中斷和合併陳述式](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)