---
title: "&lt;name&gt; is not a valid solution name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALIDSOLUTIONNAME"
  - "vs.message.0x800A00D3"
ms.assetid: 79b7870d-16bd-4527-8ce6-ffb015e7e330
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid solution name.
在 \[**命令**\] 視窗或 \[**尋找\/命令**\] 方塊中以錯誤格式的值輸入 `File.NewProject` 命令的 \/sln:*solutionname* 引數時，通常就會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
1.  請重新輸入命令語法，並省略選擇性引數 \/sln:*solutionname*。  這將自動產生唯一的方案名稱。  
  
     \-或\-  
  
     檢查方案名稱沒有包含前後空格並且不是保留字。  保留字包括 NUL、CON、AUX、COM*x* 或 LPT*x*，其中 *x* 是 1\-9 的數字。  
  
## 請參閱  
 [命令視窗](../Topic/Command%20Window.md)