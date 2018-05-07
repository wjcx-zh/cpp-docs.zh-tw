---
title: 如何： 使用規則運算式重新整理資料 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular expressions [C++], rearranging data
- data [C++], rearranging
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72c72721aa68417ff13905fdf96f8d2a48b310cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-regular-expressions-to-rearrange-data-ccli"></a>如何：使用規則運算式重新整理資料 (C++/CLI)
下列程式碼範例示範如何使用.NET Framework 規則運算式支援，以重新排列或重新格式化資料。 下列程式碼範例使用<xref:System.Text.RegularExpressions.Regex>和<xref:System.Text.RegularExpressions.Match>類別以從字串中擷取姓氏和名字，並以反向順序顯示這些名稱項目。  
  
 <xref:System.Text.RegularExpressions.Regex>類別用來建構描述目前的資料格式的規則運算式。 兩個名稱會假設為以逗號分隔，而且可以使用任何數量的逗點周圍的空白。 <xref:System.Text.RegularExpressions.Match>方法可用來分析每個字串。 如果成功，第一個和最後一個名稱從擷取<xref:System.Text.RegularExpressions.Match>物件，並顯示。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 規則運算式](/dotnet/standard/base-types/regular-expressions)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)