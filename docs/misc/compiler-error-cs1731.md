---
title: "編譯器錯誤 CS1731 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1731"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1731"
ms.assetid: 267b32aa-a692-4a54-8654-0540ee36c0a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1731
無法將 'expression' 轉換成委派，因為區塊中部分傳回類型無法隱含轉換成委派傳回類型。  
  
 Lambda 運算式或匿名方法的傳回類型與委派的傳回類型不相容時，會產生這個錯誤。  
  
### 更正這個錯誤  
  
1.  請變更委派或運算式的傳回類型。  
  
## 範例  
 下列程式碼會產生 CS1731：  
  
```  
class CS1731 { delegate double D(); D d = () => { return "Who knows the real sword of Gryffindor?"; }; }  
```