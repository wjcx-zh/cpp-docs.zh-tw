---
title: "如何：寫入二進位檔案 (C++/CLI) | Microsoft Docs"
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
  - "二進位檔案, 以 C++ 撰寫"
  - "檔案 [C++], 二進位"
ms.assetid: 35d97ee6-fc7e-4c36-be18-8bbb3b44b3ae
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：寫入二進位檔案 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會顯示如何將二進位資料寫入至檔案中。  這裡會使用兩個來自 <xref:System.IO> 命名空間的類別：<xref:System.IO.FileStream> 和 <xref:System.IO.BinaryWriter>。  <xref:System.IO.FileStream> 表示實際的檔案，而 <xref:System.IO.BinaryWriter> 會提供介面給允許進行二進位存取的資料流。  
  
 下列程式碼範例會以二進位格式撰寫含有整數的檔案。  這個檔案可以使用 [如何：讀取二進位檔案](../dotnet/how-to-read-a-binary-file-cpp-cli.md)中的程式碼讀取。  
  
## 範例  
  
```  
// binary_write.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<Int32>^ data = {1, 2, 3, 10000};  
  
   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);  
   BinaryWriter^ w = gcnew BinaryWriter(fs);  
  
   try   
   {  
      Console::WriteLine("writing data to file:");  
      for (int i=0; i<data->Length; i++)  
      {  
         Console::WriteLine(data[i]);  
         w->Write(data[i]);  
      }  
   }  
   catch (Exception^)   
   {  
     Console::WriteLine("data could not be written");  
     fs->Close();  
     return -1;  
   }  
  
   fs->Close();  
   return 0;  
}  
```  
  
## 請參閱  
 [檔案和資料流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)