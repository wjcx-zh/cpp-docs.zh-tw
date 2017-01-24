---
title: "CLS 符合性警告 CLS01606 | Microsoft Docs"
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
  - "CLS01606"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01606"
ms.assetid: 24291af4-d2b1-4a91-b50f-fb61d8ff1687
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01606
陣列必須有符合 CLS 標準之類型的項目，而且陣列所有維度的下限必須為零  
  
 陣列必須有符合 CLS 標準之類型的項目，而且陣列所有維度的下限必須為零。 只有項目是陣列以及陣列的項目類型是需要在多載之間區別的事實。 當多載根據兩個或多個陣列類型時，項目類型應該是具名類型。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS01606：  
  
```  
// CLS01606.cpp // compile with: /clr /LD // CLS01606 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One { public: // CLS01606 array<NotCompliantType^>^ Method1() { return gcnew array<NotCompliantType^>(10); } // OK array<CompliantType^>^ Method2() { return gcnew array<CompliantType^>(10); } };  
```