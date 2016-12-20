---
title: "如何：讀取二進位檔案 (C++/CLI) | Microsoft Docs"
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
  - "二進位檔案, 在 C++ 中讀取"
  - "檔案 [C++], 二進位"
ms.assetid: 41ad9ad1-5cac-489c-874e-4bb3a649073a
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：讀取二進位檔案 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例示範如何從檔案讀取二進位資料，作法是使用 <xref:System.IO?displayProperty=fullName> 命名空間中的兩個類別：<xref:System.IO.FileStream> 或 <xref:System.IO.BinaryReader>。  <xref:System.IO.FileStream> 表示實際的檔案。  <xref:System.IO.BinaryReader> 則提供可進行二進位存取的資料流介面。  
  
 程式碼範例會讀取名為 data.bin 且包含二進位格式整數的檔案。  如需這個檔案類型的詳細資訊，請參閱 [如何：寫入二進位檔案](../dotnet/how-to-write-a-binary-file-cpp-cli.md)。  
  
## 範例  
  
```  
// binary_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "data.bin";  
   try  
   {  
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);  
      BinaryReader^ br = gcnew BinaryReader(fs);  
  
      Console::WriteLine("contents of {0}:", fileName);  
      while (br->BaseStream->Position < br->BaseStream->Length)  
         Console::WriteLine(br->ReadInt32().ToString());  
  
      fs->Close( );  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("File '{0}' not found", fileName);  
      else  
         Console::WriteLine("Exception: ({0})", e);  
      return -1;  
   }  
   return 0;  
}  
```  
  
## 請參閱  
 [檔案和資料流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)