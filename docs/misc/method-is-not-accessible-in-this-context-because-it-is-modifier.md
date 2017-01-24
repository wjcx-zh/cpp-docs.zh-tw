---
title: "無法在此內容中存取 &#39;&lt;方法&gt;&#39;，因為它是 &#39;&lt;修飾詞&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30389"
  - "bc30389"
helpviewer_keywords: 
  - "BC30389"
ms.assetid: fae58a68-df91-4741-a8c9-f1bb10e166e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法在此內容中存取 &#39;&lt;方法&gt;&#39;，因為它是 &#39;&lt;修飾詞&gt;&#39;
您嘗試存取因宣告為 `Private` 而無法在這個內容中存取的方法。 這個錯誤的可能原因是 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器匯入類別的所有成員且未區分大小寫，因此只由大小寫區分的名稱可能會發生衝突。  
  
 **錯誤 ID︰**BC30389  
  
### 更正這個錯誤  
  
-   考慮宣告方法 `Public`。  
  
-   如果錯誤是由名稱衝突所造成，請用大小寫以外的方式區分衝突的名稱。  
  
## 請參閱  
 [Private](../Topic/Private%20\(Visual%20Basic\).md)