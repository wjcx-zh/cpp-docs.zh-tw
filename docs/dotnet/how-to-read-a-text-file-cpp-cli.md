---
title: 如何： 讀取文字檔 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- reading text files
- text files, reading
ms.assetid: 80551c01-d769-4b6d-8db7-fd53bde21b62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c350ea9cd8b71378d059a93ac80ca808d4f48790
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-a-text-file-ccli"></a>如何：讀取文字檔 (C++/CLI)
下列程式碼範例示範如何開啟並使用一次讀取文字檔案一行<xref:System.IO.StreamReader>中定義的類別<xref:System.IO?displayProperty=fullName>命名空間。 這個類別的執行個體用來開啟文字檔，然後<xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>方法用來擷取每一行。  
  
 這個程式碼範例會讀取具有名為 textfile.txt 且包含文字的檔案。 如需這類檔案的詳細資訊，請參閱[如何： 寫入文字檔 (C + + /CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md)。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流 I/O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)