---
title: "CLS 符合性警告 CLS00500 | Microsoft Docs"
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
  - "CLS00500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00500"
ms.assetid: faaf377e-3738-4c0d-9a51-09db4073564e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS00500
符合 CLS 標準之範圍中的所有名稱都必須是不同的獨立類型  
  
 在符合 CLS 標準的範圍中引入的所有名稱，除了名稱完全相同且透過多載解析的情況之外，都必須是不同的獨立類型。 基於 CLS 目的，如果兩個名稱的小寫對應是相同的，則這兩個名稱是視為相等。 只有屬性和函式可以多載。 多載時，屬性和函式只可以根據其參數數目和類型多載，但不包括轉換運算子，該運算子也可以根據其傳回類型多載；如需詳細資訊，請參閱[使用者定義轉換](../dotnet/user-defined-conversions-cpp-cli.md)。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列範例會產生 CLS00500：  
  
```  
// CLS00500.cpp // compile with: /clr /LD // CLS00500 expected using namespace System; using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; [assembly:System::CLSCompliant(true)]; public ref class a {}; public ref class A {};   // CLS00500  
```