---
title: "CLS 符合性警告 CLS03603 | Microsoft Docs"
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
  - "CLS03603"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03603"
ms.assetid: 8bd74395-6b44-427d-8fe0-648dd946e6d2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS03603
全域靜態欄位不符合 CLS 標準  
  
 全域靜態欄位和方法不符合 CLS 標準。  
  
 如需公用語言子集 \(Common Language Subset, CLS\) 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS03603：  
  
```  
// CLS03603.cpp // compile with: /clr /LD // CLS03603 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; int i;   // CLS03603 public ref class MyClass { public: int i;   // OK };  
```