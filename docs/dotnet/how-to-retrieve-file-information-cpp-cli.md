---
title: "如何：擷取檔案資訊 (C++/CLI) | Microsoft Docs"
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
  - "FileInfo 類別"
  - "檔案 [C++], 擷取相關資訊"
ms.assetid: 8b67f7ad-a048-4437-ac5c-b41809a6018d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：擷取檔案資訊 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範使用 <xref:System.IO.FileInfo> 類別。  當您知道檔案名稱時，您可以使用這個類別擷取檔案的資訊，例如檔案大小、目錄、完整名稱以及建立和上次修改的日期和時間。  
  
 這個程式碼會擷取 Notepad.exe 的檔案資訊。  
  
## 範例  
  
```  
// file_info.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<String^>^ args = Environment::GetCommandLineArgs();  
   if (args->Length < 2)  
   {  
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");  
      return -1;  
   }  
  
   FileInfo^ fi = gcnew FileInfo( args[1] );  
  
   Console::WriteLine("file size: {0}", fi->Length );  
  
   Console::Write("File creation date:  ");  
   Console::Write(fi->CreationTime.Month.ToString());  
   Console::Write(".{0}", fi->CreationTime.Day.ToString());  
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());  
  
   Console::Write("Last access date:  ");  
   Console::Write(fi->LastAccessTime.Month.ToString());  
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());  
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());  
  
   return 0;  
}  
```  
  
## 請參閱  
 [檔案和資料流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)