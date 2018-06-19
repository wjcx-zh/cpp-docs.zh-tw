---
title: 如何： 使用規則運算式剖析字串 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- strings [C++], parsing
ms.assetid: 5b0c7ca3-9bba-4389-a45c-6d373cff91b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5940a59d7e9b4e68f289848523710594621e73d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131094"
---
# <a name="how-to-parse-strings-using-regular-expressions-ccli"></a>如何：使用規則運算式剖析字串 (C++/CLI)
下列程式碼範例示範簡單的字串剖析使用<xref:System.Text.RegularExpressions.Regex>類別<xref:System.Text.RegularExpressions?displayProperty=fullName>命名空間。 會建構包含多種類型的文字分隔符號的字串。 此字串會剖析使用<xref:System.Text.RegularExpressions.Regex>類別搭配<xref:System.Text.RegularExpressions.Match>類別。 然後，在句子中的每個單字會個別顯示。  
  
## <a name="example"></a>範例  
  
```  
// regex_parse.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main( )  
{  
   int words = 0;  
   String^ pattern = "[a-zA-Z]*";  
   Console::WriteLine( "pattern : '{0}'", pattern );  
   Regex^ regex = gcnew Regex( pattern );  
  
   String^ line = "one\ttwo three:four,five six  seven";     
   Console::WriteLine( "text : '{0}'", line );  
   for( Match^ match = regex->Match( line );   
        match->Success; match = match->NextMatch( ) )   
   {  
      if( match->Value->Length > 0 )  
      {  
         words++;  
         Console::WriteLine( "{0}", match->Value );  
      }  
   }  
   Console::WriteLine( "Number of Words : {0}", words );  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 規則運算式](/dotnet/standard/base-types/regular-expressions)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)