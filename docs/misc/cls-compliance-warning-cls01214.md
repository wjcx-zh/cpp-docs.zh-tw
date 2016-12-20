---
title: "CLS 符合性警告 CLS01214 | Microsoft Docs"
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
  - "CLS01214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01214"
ms.assetid: 5968af20-3d3e-4c7b-ad61-c06979cc9efd
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01214
類型和成員應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中的類型也應該是可見和可存取的。 例如，組件外部可見的委派不得有引數，其類型只有在組件內可見。  
  
 委派簽章中的類型，存取範圍必須大於或等於委派的存取範圍。  例如，組件外部可見的委派不得有引數，其類型只有在組件內可見。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS01214：  
  
```  
/* CLS01214.cpp */ // compile with: /clr /LD // CLS01214 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicType {}; private ref class AssemblyType {}; public delegate PublicType^ AssemblyDelegate(AssemblyType^ parameter);   // not cls compliant public delegate PublicType^ AssemblyDelegate2(PublicType^ parameter);   //cls compliant  
```