---
title: "如何：讀取文字檔 (C++/CLI) | Microsoft Docs"
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
  - "讀取文字檔"
  - "文字檔, 讀取"
ms.assetid: 80551c01-d769-4b6d-8db7-fd53bde21b62
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：讀取文字檔 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範如何使用 <xref:System.IO?displayProperty=fullName> 命名空間中定義的 <xref:System.IO.StreamReader> 類別開啟文字檔，一次讀取一行文字。  範例會使用這個類別的執行個體來開啟文字檔案，然後使用 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> 方法來擷取每一行。  
  
 這個程式碼範例會讀取名為 textfile.txt 且包含文字的檔案。  如需這個檔案類型的詳細資訊，請參閱 [如何：寫入文字檔](../dotnet/how-to-write-a-text-file-cpp-cli.md)。  
  
## 範例  
  
```  
// text_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ fileName = "textfile.txt";  
   try   
   {  
      Console::WriteLine("trying to open file {0}...", fileName);  
      StreamReader^ din = File::OpenText(fileName);  
  
      String^ str;  
      int count = 0;  
      while ((str = din->ReadLine()) != nullptr)   
      {  
         count++;  
         Console::WriteLine("line {0}: {1}", count, str );  
      }  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("file '{0}' not found", fileName);  
      else  
         Console::WriteLine("problem reading file '{0}'", fileName);  
   }  
  
   return 0;  
}  
```  
  
## 請參閱  
 [檔案和資料流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)