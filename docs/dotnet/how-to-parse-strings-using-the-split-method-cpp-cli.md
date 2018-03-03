---
title: "如何： 使用 Split 方法剖析字串 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
ms.assetid: d52d2539-5ebb-4716-86b3-07314dd7e4bd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7494a615d1a253c6617601f38e5d01755c718b80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-parse-strings-using-the-split-method-ccli"></a>如何：使用 Split 方法剖析字串 (C++/CLI)
下列程式碼範例示範如何使用<xref:System.String.Split%2A?displayProperty=fullName>方法，以從字串擷取的每個字。 建構及藉由呼叫會剖析字串，包含多種類型的文字分隔符號<xref:System.String.Split%2A>分隔符號的清單。 然後，在句子中的每個單字會個別顯示。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>請參閱  
 [.NET Framework 規則運算式](/dotnet/standard/base-types/regular-expressions)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)