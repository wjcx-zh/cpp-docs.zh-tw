---
title: "&#39;&lt;修飾詞&gt;&#39; 在 Interface 宣告中無效 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30397"
  - "vbc30397"
helpviewer_keywords: 
  - "BC30397"
ms.assetid: 9143dc87-c396-4ff9-9987-0b460ee32b38
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;修飾詞&gt;&#39; 在 Interface 宣告中無效
您使用了對 `Interface` 宣告無效的修飾詞。 對 `Interface` 宣告中所宣告之 `Sub`、`Function` 或 `Property` 陳述式唯一有效的修飾詞為 `Overloads` 和 `Default` 關鍵字。 其他修飾詞 \(例如 `Public`、`Private`、`Friend`、`Protected`、`Shared`、`Static`、`Overrides`、`MustOverride` 和 `Overridable`\) 則無效。  
  
 **錯誤 ID：**BC30397  
  
### 更正這個錯誤  
  
-   請移除修飾詞。  
  
## 請參閱  
 [不在組建中：介面定義](http://msdn.microsoft.com/zh-tw/7840a52c-9c38-42c4-adbc-e2c02e9dc204)