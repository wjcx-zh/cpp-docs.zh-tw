---
title: "編譯器警告 (層級 1) CS1695 | Microsoft Docs"
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
  - "CS1695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1695"
ms.assetid: cc4e4d00-0618-400d-985b-90968e98772c
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1695
\#pragma checksum 語法無效; 應該是 \#pragma checksum "filename" "{XXXXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXXXXX}" "XXXX..."  
  
 如果您是透過 Code Dom API 產生程式碼，則因為總和檢查碼一般是在執行階段插入，所以應該很少會發生這個錯誤。  
  
 不過，如果您是在這個 `#pragma` 陳述式中輸入，並且打錯 GUID 或總和檢查碼，就會收到這個錯誤。 編譯器的語法檢查不會驗證您輸入的 GUID 是否正確，但會檢查數字位數和分隔符號數目是否正確，以及數字是否為十六進位。 同樣地，它也會驗證總和檢查碼是否包含偶數位數的數字，以及數字是否為十六進位。  
  
## 範例  
 下列範例會產生 CS1695。  
  
```  
// CS1695.cs #pragma checksum "12345"  // CS1695 public class Test { static void Main() { } }  
```