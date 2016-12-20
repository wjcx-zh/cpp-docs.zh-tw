---
title: "CLS 符合性警告 CLS03002 | Microsoft Docs"
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
  - "CLS03002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03002"
ms.assetid: b3254410-e21c-430b-a2fd-d110d6f5f38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS03002
事件及其存取子的存取範圍必須是相同的  
  
 事件及其存取子方法的存取範圍必須是相同的。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS03002：  
  
```  
// CLS03002.cpp // compile with: /clr /LD // CLS03002 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyDelegate(int parameter); public ref class One { public: event MyDelegate^ MyEvent {   // CLS03002 public: void add(MyDelegate^ paramter) {} void remove(MyDelegate^ parameter) {} protected: void raise(int parameter)   {} } event MyDelegate^ MyEvent2 {   // OK public: void add(MyDelegate^ paramter) {} void remove(MyDelegate^ parameter) {} void raise(int parameter)   {} } };  
```