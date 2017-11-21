---
title: "如何： 使用規則運算式進行搜尋和取代 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- search and replace
- Replace method
- regular expressions [C++], search and replace
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 17710654b0af2e03019a1e7b888d86e42c5e35c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-regular-expressions-to-search-and-replace-ccli"></a>如何：使用規則運算式進行搜尋和取代 (C++/CLI)
下列程式碼範例示範如何規則運算式類別<xref:System.Text.RegularExpressions.Regex>可用來執行搜尋和取代。 做法是使用<xref:System.Text.RegularExpressions.Regex.Replace%2A>方法。 使用的版本會採用兩個字串做為輸入： 將修改字串和要插入的區段取代 （如果有的話） 字串的比對模式提供給<xref:System.Text.RegularExpressions.Regex>物件。  
  
 此程式碼取代字串中的所有數字與底線 (_)，然後再取代具有空字串，以便有效地移除它們。 在單一步驟中，可以完成相同的效果，但兩個步驟適用於此處示範用途。  
  
## <a name="example"></a>範例  
  
```  
// regex_replace.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System::Text::RegularExpressions;  
using namespace System;  
  
int main()  
{  
   String^ before = "The q43uick bro254wn f0ox ju4mped";  
   Console::WriteLine("original  : {0}", before);  
  
   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");  
   String^ after = digitRegex->Replace(before, "_");  
   Console::WriteLine("1st regex : {0}", after);  
  
   Regex^ underbarRegex = gcnew Regex("_");  
   String^ after2 = underbarRegex->Replace(after, "");  
   Console::WriteLine("2nd regex : {0}", after2);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 規則運算式](/dotnet/standard/base-types/regular-expressions)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)