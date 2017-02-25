---
title: "如何：將標準字串轉換為 System::String | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Standard C++ 程式庫, 轉換字串為 System::String"
  - "字串轉換 [C++], Standard C++ 程式庫字串"
  - "字串 [C++], 轉換"
ms.assetid: 1fde79a0-9d0b-44e5-981b-e8f2676c199d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何：將標準字串轉換為 System::String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個主題將介紹如何將 Standard C\+\+ 程式庫字串 \([\<string\>](../standard-library/string.md)\) 轉換為 <xref:System.String>。  
  
## 範例  
  
```  
// convert_standard_string_to_system_string.cpp  
// compile with: /clr  
#include <string>  
#include <iostream>  
using namespace System;  
using namespace std;  
  
int main() {  
   string str = "test";  
   cout << str << endl;  
   String^ str2 = gcnew String(str.c_str());  
   Console::WriteLine(str2);  
  
   // alternatively  
   String^ str3 = gcnew String(str.c_str());  
   Console::WriteLine(str3);  
}  
```  
  
  **測試**  
**測試**  
**測試**   
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)