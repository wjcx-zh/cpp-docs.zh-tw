---
title: "CLS 符合性警告 CLS02902 | Microsoft Docs"
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
  - "CLS02902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02902"
ms.assetid: 028c91fc-d3bb-4c97-92e6-159b5d663fc2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS02902
在中繼資料中，實作事件的方法必須標示為 SpecialName。  
  
 在中繼資料中，實作事件的方法未標上 **specialname**。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列函式宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS02902：  
  
```  
.method public instance void raise_MyEvent(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent  
```  
  
 加入 **specialname** 關鍵字，即可解決這個警告：  
  
```  
.method public specialname instance void raise_MyEvent(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent  
```