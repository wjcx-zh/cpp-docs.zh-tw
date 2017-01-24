---
title: "常數 &#39;&lt;常數名稱&gt;&#39; 無法相依在本身的值上 | Microsoft Docs"
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
  - "bc30500"
  - "vbc30500"
helpviewer_keywords: 
  - "BC30500"
ms.assetid: 0dad89bc-9196-492f-acd9-7777757362f7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 常數 &#39;&lt;常數名稱&gt;&#39; 無法相依在本身的值上
您已在程式碼中建立循環相依性，其中常數取決於它自己的值。 例如，`Const a = Const b; Const b = Const a`。  
  
 **錯誤 ID︰**BC30500  
  
### 更正這個錯誤  
  
1.  請檢查您的程式碼，以查看評估常數的位置，並相應地進行修改。  
  
## 請參閱  
 [NOTINBUILD 常數概觀](http://msdn.microsoft.com/zh-tw/5c7f57fb-48b2-4a2f-afee-79d8e3adf15b)