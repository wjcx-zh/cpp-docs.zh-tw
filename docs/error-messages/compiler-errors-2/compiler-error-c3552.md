---
title: "編譯器錯誤 C3552 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3552"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3552"
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3552
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'typename': 晚期指定的傳回類型不能包含 'auto'  
  
 如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 不過，您無法使用另一個 `auto` 關鍵字來指定晚期指定的傳回類型。 例如，下列程式碼片段會產生錯誤 C3552。  
  
 `auto myFunction->auto; // C3552`