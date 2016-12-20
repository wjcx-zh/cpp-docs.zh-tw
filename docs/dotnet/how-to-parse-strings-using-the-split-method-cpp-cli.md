---
title: "如何：使用 Split 方法剖析字串 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "範例 [C++], 字串"
  - "剖析字串 [C++]"
  - "規則運算式 [C++], 剖析字串"
  - "Split 方法, 剖析字串"
  - "字串 [C++], 剖析"
ms.assetid: d52d2539-5ebb-4716-86b3-07314dd7e4bd
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 Split 方法剖析字串 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範使用 <xref:System.String.Split%2A?displayProperty=fullName> 方法，從字串中抽取每一個單字。  範例會建構包含各種文字分隔符號的字串，然後使用分隔符號清單做為參數，呼叫 <xref:System.String.Split%2A> 來剖析字串。  接著會個別顯示句子中的每一個單字。  
  
## 範例  
  
```  
// regex_split.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String^ delimStr = " ,.:\t";  
   Console::WriteLine( "delimiter : '{0}'", delimStr );  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ words;  
   String^ line = "one\ttwo three:four,five six seven";  
  
   Console::WriteLine( "text : '{0}'", line );  
   words = line->Split( delimiter );  
   Console::WriteLine( "Number of Words : {0}", words->Length );  
   for (int word=0; word<words->Length; word++)  
      Console::WriteLine( "{0}", words[word] );  
  
   return 0;  
}  
```  
  
## 請參閱  
 [.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)