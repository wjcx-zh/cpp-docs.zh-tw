---
title: "編譯器錯誤 CS0268 | Microsoft Docs"
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
  - "CS0268"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0268"
ms.assetid: a4faca71-8b4a-4f22-a89e-59d92ced48cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0268
匯入的類型 'type' 無效。 它包含循環基底類別相依性。  
  
 如果從另一種語言匯入的類型具有循環基底類別相依性，則會發生這個錯誤。 此類型不能用於 C\# 程式中。 若要解決這個錯誤，請檢查任何參考之組件或模組中從其他語言匯入的類型。