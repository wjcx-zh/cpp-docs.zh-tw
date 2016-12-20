---
title: "編譯器警告 (層級 1) CS1697 | Microsoft Docs"
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
  - "CS1697"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1697"
ms.assetid: 0cd931b7-f358-4ff0-b441-27668645d7d5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1697
為 'file name' 指定了不同的總和檢查碼值  
  
 您已為指定的檔案指定多個總和檢查碼。 偵錯工具會使用總和檢查碼值，來判斷專案中有多個同名的檔案時要偵錯的檔案。 大部分使用者都不會發生這個錯誤，但如果您所撰寫的應用程式會產生程式碼，則可能會發生這個錯誤。 若要解決這個錯誤，請確定您只針對任何指定的程式碼檔案產生總和檢查碼一次。