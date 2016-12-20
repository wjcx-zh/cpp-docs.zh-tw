---
title: "CLS 符合性警告 CLS01706 | Microsoft Docs"
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
  - "CLS01706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01706"
ms.assetid: b89ccbf1-7256-4842-a0af-44a803f28340
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01706
Unmanaged 指標類型不符合 CLS 標準  
  
 符合 CLS 標準的函式簽章不能包含 Unmanaged 指標類型。  
  
 如需公用語言子集 \(Common Language Subset, CLS\) 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS01706：  
  
```  
// CLS01706.cpp // compile with: /clr /LD // CLS01706 expected [assembly:System::CLSCompliant (true)]; [assembly:System::Reflection::AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: void Method1(int* parameter) {}   // CLS01706 void Method1(One ^ parameter) {}   // OK };  
```