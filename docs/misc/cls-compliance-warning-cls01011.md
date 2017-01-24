---
title: "CLS 符合性警告 CLS01011 | Microsoft Docs"
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
  - "CLS01011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01011"
ms.assetid: e4141e15-14fd-491c-9639-f3f3a47d7865
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01011
在覆寫繼承的方法時，不得變更其存取範圍  
  
 請確定覆寫方法的可視性與它覆寫的方法相同。  在覆寫繼承的方法時，不得變更其存取範圍；但覆寫繼承自具有 Family\-or\-Assembly 存取範圍之不同組件的方法除外。 在這種情況下，覆寫應具有 Family 存取範圍。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS01011：  
  
```  
// CLS01011.cpp // compile with: /clr /LD // CLS01011 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class BaseType { public protected: virtual void BaseTypeMethod() {} }; public ref class One : public BaseType { public: void BaseTypeMethod() {}   // CLS01011 // OK // public protected: //    void BaseTypeMethod() {} };  
```