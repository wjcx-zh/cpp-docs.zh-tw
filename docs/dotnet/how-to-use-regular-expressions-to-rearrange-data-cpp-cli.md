---
title: "如何：使用規則運算式重新整理資料 (C++/CLI) | Microsoft Docs"
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
  - "資料 [C++], 重新排列"
  - "規則運算式 [C++], 重新排列資料"
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用規則運算式重新整理資料 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範如何使用 .NET Framework 規則運算式支援，將資料重新排列或重新格式化。  下列程式碼範例會使用 <xref:System.Text.RegularExpressions.Regex> 和 <xref:System.Text.RegularExpressions.Match> 類別，將名和姓從字串中擷取出來，並以相反順序顯示這些姓名項目。  
  
 範例會使用 <xref:System.Text.RegularExpressions.Regex> 類別建構描述資料目前格式的規則運算式。  姓和名則假設以逗號分隔，逗號的前後可以有任意數量的空白。  接著會使用 <xref:System.Text.RegularExpressions.Match> 方法來分析每個字串。  如果成功，則會從 <xref:System.Text.RegularExpressions.Match> 物件中擷取名和姓並顯示。  
  
## 範例  
  
```  
// regex_reorder.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ name =   
   {  
      "Abolrous, Sam",   
      "Berg,Matt",   
      "Berry , Jo",  
      "www.contoso.com"  
   };  
  
   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");  
  
   for ( int i=0; i < name->Length; i++ )  
   {  
      Console::Write( "{0,-20}", name[i] );  
      Match^ m = reg->Match( name[i] );  
      if ( m->Success )  
      {  
         String^ first = m->Groups["first"]->Value;  
         String^ last = m->Groups["last"]->Value;  
         Console::WriteLine("{0} {1}", first, last);  
      }  
      else  
         Console::WriteLine("(invalid)");  
   }  
   return 0;  
}  
```  
  
## 請參閱  
 [.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)