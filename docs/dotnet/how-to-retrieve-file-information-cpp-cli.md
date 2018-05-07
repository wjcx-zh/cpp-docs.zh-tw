---
title: 如何： 擷取檔案資訊 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++], retrieving information about
- FileInfo class
ms.assetid: 8b67f7ad-a048-4437-ac5c-b41809a6018d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e3c103aaed184039267792c4df4544c382ef7aee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-file-information-ccli"></a>如何：擷取檔案資訊 (C++/CLI)
下列程式碼範例示範<xref:System.IO.FileInfo>類別。 當您擁有的檔案名稱時，您可以使用這個類別來擷取檔案如下的檔案大小、 目錄、 完整名稱，以及日期和時間相關的資訊建立和上次修改。  
  
 此程式碼會擷取為 Notepad.exe 的檔案資訊。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流 I/O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)