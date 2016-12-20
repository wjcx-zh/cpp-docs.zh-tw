---
title: "CLS 符合性警告 CLS02409 | Microsoft Docs"
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
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS02409
實作屬性之 getter 和 setter 方法的方法在中繼資料中應標記為 SpecialName  
  
 實作屬性之 getter 和 setter 方法的方法在中繼資料中未標記為 **specialname**。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列函式宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS02409：  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 加入 **specialname** 關鍵字，即可解決這個警告：  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```