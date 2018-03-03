---
title: "如何： 讀取二進位檔案 (C + + /CLI) |Microsoft 文件"
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
- files [C++], binary
- binary files, reading in C++
ms.assetid: 41ad9ad1-5cac-489c-874e-4bb3a649073a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3714ba3df6d44559db66b56ea1a0f8a3ff7f3f44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-a-binary-file-ccli"></a>如何：讀取二進位檔案 (C++/CLI)
下列程式碼範例示範如何從檔案讀取二進位資料，使用兩個類別從<xref:System.IO?displayProperty=fullName>命名空間：<xref:System.IO.FileStream>和<xref:System.IO.BinaryReader>。 <xref:System.IO.FileStream>代表實際檔案。 <xref:System.IO.BinaryReader>提供可讓您存取二進位資料流介面。  
  
 程式碼範例讀取的檔案具有名為 data.bin 且包含二進位格式的整數。 如需這類檔案的詳細資訊，請參閱[如何： 寫入二進位檔案 (C + + /CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md)。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>請參閱  
 [檔案和資料流 I/O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)