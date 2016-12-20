---
title: "CLS 符合性警告 CLS03202 | Microsoft Docs"
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
  - "CLS03202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03202"
ms.assetid: 2219c86c-9276-4244-a2ff-bce578c4d65f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS03202
事件的加入和移除方法應各自採用一個其類型會定義事件類型的參數，而且必須是衍生自 System.Delegate  
  
 事件的加入和移除方法應各自採用一個其類型會定義事件類型的參數，而且必須是衍生自 System.Delegate。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列函式宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS03202：  
  
```  
// bad .method public specialname instance void add_MyEvent(class MyDelegate __unnamed000, int32 __extra) cil managed {}  
```  
  
 如果事件存取子只接受一個參數，您就可以解決這個警告：  
  
```  
.method public specialname instance void add_MyEvent(class MyDelegate __unnamed000) cil managed {}  
```