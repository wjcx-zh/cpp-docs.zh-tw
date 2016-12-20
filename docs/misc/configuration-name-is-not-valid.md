---
title: "Configuration name is not valid. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Configuration name is not valid.
在為組建組態所輸入的名稱中包含不合法的字元 \(例如 \<、\>、&#124; 和 \*\) 時，通常就會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
1.  請檢查組態名稱並沒有包含下列字元：\<、\>、\*、&#124;、:、\\、\/、&、%、"、.、\#、? 或前後空格。  此外，組態名稱不能使用保留給 Windows 或 DOS 的名稱，例如 "nul"、"aux"、"con"、"com\#"、"com\#" 等等。  
  
2.  請重新輸入名稱。  
  
## 請參閱  
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)