---
title: "此內容中不允許 &#39;Global&#39;; 必須是識別項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36001"
  - "bc36001"
helpviewer_keywords: 
  - "BC36001"
ms.assetid: d515daa2-f53d-424c-81fd-e9c4b12f331b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此內容中不允許 &#39;Global&#39;; 必須是識別項
`Global` 關鍵字使用在不允許的陳述式。  
  
 `Global` 關鍵字可讓您存取在您的程式碼要編譯所在命名空間階層架構之外定義的命名空間。`Global` 的限定性條件路徑從 .NET Framework 類別庫的最外層命名空間層級開始。 如需圖例，請參閱 [Global \- delete](http://msdn.microsoft.com/zh-tw/18c8ba14-40f6-4978-8096-6a5852324635)。  
  
 某些陳述式，例如 `Imports` 和 `Namespace`，與您的程式碼要編譯所在的命名空間無關。 它們需要完整限定性條件路徑，並且從根層級的命名空間開始，例如 <xref:System> 或 <xref:Microsoft.VisualBasic>。 在這類陳述式，`Global` 是多餘且不允許的關鍵字。  
  
 **錯誤 ID︰**BC36001  
  
### 更正這個錯誤  
  
-   請從陳述式中移除 `Global` 關鍵字。 不需要它。  
  
## 請參閱  
 [Global \- delete](http://msdn.microsoft.com/zh-tw/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)   
 [Namespace Statement](../Topic/Namespace%20Statement.md)   
 [References and the Imports Statement](../Topic/References%20and%20the%20Imports%20Statement%20\(Visual%20Basic\).md)