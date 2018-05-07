---
title: 如何： 寫入文字檔 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++], text
- text files, writing in C++
ms.assetid: 39ecdba6-84e0-485c-a202-84cf6d7b8d4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e0ce3839a5d0a0668d921a2d64cb0cf7bd1c775
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-text-file-ccli"></a>如何：寫入文字檔 (C++/CLI)
下列程式碼範例示範如何建立文字檔案，並將文字寫入至使用<xref:System.IO.StreamWriter>類別，定義於<xref:System.IO>命名空間。 <xref:System.IO.StreamWriter>建構函式會採用要建立檔案的名稱。 如果檔案存在，則會覆寫 (除非您將為 true，則當做第二個<xref:System.IO.StringWriter>建構函式引數)。  
  
 檔案然後歸檔使用<xref:System.IO.StreamWriter.Write%2A>和<xref:System.IO.TextWriter.WriteLine%2A>函式。  
  
## <a name="example"></a>範例  
  
```  
// text_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "textfile.txt";  
  
   StreamWriter^ sw = gcnew StreamWriter(fileName);  
   sw->WriteLine("A text file is born!");  
   sw->Write("You can use WriteLine");  
   sw->WriteLine("...or just Write");  
   sw->WriteLine("and do {0} output too.", "formatted");  
   sw->WriteLine("You can also send non-text objects:");  
   sw->WriteLine(DateTime::Now);  
   sw->Close();  
   Console::WriteLine("a new file ('{0}') has been written", fileName);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流 I/O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)