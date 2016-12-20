---
title: "引數不能為 Nothing | Microsoft Docs"
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
  - "vbrGeneral_ArgumentNullException"
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引數不能為 Nothing
Null 值已提供給必須有值的引數。  
  
### 更正這個錯誤  
  
-   您可能嘗試使用物件，卻未提供該物件的執行個體。 這種情況請使用 `New` 關鍵字建立執行個體。  
  
-   檢查值是否計算正確。  
  
## 請參閱  
 [疑難排解例外狀況：System.NullReferenceException](../misc/troubleshooting-exceptions-system-nullreferenceexception.md)