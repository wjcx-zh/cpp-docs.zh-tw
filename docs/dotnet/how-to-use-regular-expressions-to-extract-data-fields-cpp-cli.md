---
title: "如何：使用規則運算式擷取資料欄位 (C++/CLI) | Microsoft Docs"
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
  - "資料 [C++], 從字串中擷取"
  - "格式化的字串 [C++]"
  - "規則運算式 [C++], 擷取資料欄位"
  - "字串 [C++], 擷取資料自"
ms.assetid: b581d9b6-630e-48fa-94fe-20b0f7b89b06
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用規則運算式擷取資料欄位 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範使用規則運算式 \(Regular Expression\) 從已格式化的字串中擷取資料。  並會使用 <xref:System.Text.RegularExpressions.Regex> 類別，指定對應至電子郵件地址的模式。  這個模式包含欄位識別項，可以用來擷取每個電子郵件地址的使用者和主機名稱部分。  <xref:System.Text.RegularExpressions.Match> 類別會用來執行實際的模式比對。  如果指定的電子郵件地址是有效的，則會擷取使用者名稱和主機名稱並顯示出來。  
  
## 範例  
  
```  
// Regex_extract.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main()  
{  
    array<String^>^ address=  
    {  
        "jay@southridgevideo.com",  
        "barry@adatum.com",  
        "treyresearch.net",  
        "karen@proseware.com"  
    };  
  
    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");  
  
    for (int i=0; i<address->Length; i++)  
    {  
        Match^ m = emailregex->Match( address[i] );  
        Console::Write("\n{0,25}", address[i]);  
  
        if ( m->Success )   
        {  
            Console::Write("   User='{0}'",   
            m->Groups["user"]->Value);  
            Console::Write("   Host='{0}'",   
            m->Groups["host"]->Value);  
        }  
        else   
            Console::Write("   (invalid email address)");  
        }  
  
    Console::WriteLine("");  
    return 0;  
}  
```  
  
## 請參閱  
 [.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)