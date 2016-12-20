---
title: "CLS 符合性警告 CLS01202 | Microsoft Docs"
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
  - "CLS01202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01202"
ms.assetid: ab75e9c4-9d87-4bb4-ad8f-3e6ab5559de7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01202
類型和成員應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中的類型也應該是可見和可存取的。 例如，在組件外部是可見的公用事件不得有引數，其類型只有在組件內可見。  
  
 事件處理常式類型的存取範圍必須大於或等於事件處理常式的存取範圍。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS01202：  
  
```  
/* CLS01202.cpp */ // compile with: /clr /LD // CLS01202 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyPublicDelegate(); private delegate void MyAssemblyDelegate(); public ref class One { public: event MyAssemblyDelegate^ MyEvent { public: void add(MyAssemblyDelegate^ Addparameter) {}   //  not cls compliant void remove(MyAssemblyDelegate^ Removeparameter) {}   //  not cls compliant void raise() {} } };  
```