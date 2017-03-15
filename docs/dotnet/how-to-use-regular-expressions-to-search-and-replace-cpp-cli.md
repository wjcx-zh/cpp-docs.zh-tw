---
title: "如何：使用規則運算式進行搜尋和取代 (C++/CLI) | Microsoft Docs"
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
  - "規則運算式 [C++], 搜尋和取代"
  - "Replace 方法"
  - "搜尋和取代"
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用規則運算式進行搜尋和取代 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會顯示如何使用規則運算式類別 <xref:System.Text.RegularExpressions.Regex> 執行搜尋和取代。  這是使用 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法來完成。  所使用的版本會使用兩個字串做為輸入：一是要修改的字串，另一個字串則是要插入以取代符合給予 <xref:System.Text.RegularExpressions.Regex> 物件之模式的區段 \(如果有的話\)。  
  
 這個程式碼會以底線 \(\_\) 取代字串中的所有數字，再以空白字串取代底線，以便有效地移除這些數字。  這些動作也能以單一步驟達成，但此處為了示範之用，還是採用兩個步驟。  
  
## 範例  
  
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
  
## 請參閱  
 [.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)