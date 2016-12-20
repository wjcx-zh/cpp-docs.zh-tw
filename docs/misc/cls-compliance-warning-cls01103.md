---
title: "CLS 符合性警告 CLS01103 | Microsoft Docs"
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
  - "CLS01103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01103"
ms.assetid: 0d0aebaa-441a-4dc0-9745-8de3a551204b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01103
簽章中出現的所有類型都必須符合 CLS 標準  
  
 如果類型符合 CLS 標準，則除非標記為不符合 CLS 標準，否則所有欄位都必須是符合 CLS 標準的類型。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
```  
// CLS01103.cpp // compile with: /clr /LD // CLS01103 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public ref class NotCompliantType {}; // Ref class public ref class One { public: NotCompliantType^ Member1;   // CLS01103 static NotCompliantType^ Member2;   // CLS01103 };  
```