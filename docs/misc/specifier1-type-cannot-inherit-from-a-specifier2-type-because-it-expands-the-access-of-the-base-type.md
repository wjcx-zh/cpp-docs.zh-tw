---
title: "&lt;規範1&gt; &lt;類型&gt; 無法繼承自 &lt;規範2&gt; &lt;類型&gt;，因為它會展開基底 &lt;類型&gt; 的存取權 | Microsoft Docs"
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
  - "bc30509"
  - "vbc30509"
helpviewer_keywords: 
  - "BC30509"
ms.assetid: 53594d6e-5e6d-463d-aa68-e2d41e152da7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;規範1&gt; &lt;類型&gt; 無法繼承自 &lt;規範2&gt; &lt;類型&gt;，因為它會展開基底 &lt;類型&gt; 的存取權
您嘗試讓公用類別繼承自標記為 `Private` 或 `Friend` 的基底類別。  
  
 **錯誤 ID︰**BC30509  
  
### 更正這個錯誤  
  
-   請宣告基底類別 `Public` 或宣告繼承類別 `Private` 或 `Friend`。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)