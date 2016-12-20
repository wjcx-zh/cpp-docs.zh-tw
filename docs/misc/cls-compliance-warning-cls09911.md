---
title: "CLS 符合性警告 CLS09911 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS09911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS09911"
ms.assetid: 8cc0b0c0-a823-4392-9bf9-4d12242ef451
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS09911
泛型類型不符合 CLS 標準  
  
 符合 CLS 標準的類型不能也是泛型類型。  如需 Visual C\+\+ 中泛型的詳細資訊，請參閱 [C\+\+ 中的泛型支援](../windows/generics-cpp-component-extensions.md)。  
  
 如需公用語言子集 \(Common Language Subset, CLS\) 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS09911：  
  
```  
// CLS09911.cpp // compile with: /clr /LD using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; generic <class T> public ref class Five {   // CLS09911 };  
  
```