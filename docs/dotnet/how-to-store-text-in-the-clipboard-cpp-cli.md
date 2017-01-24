---
title: "如何：將文字儲存在剪貼簿中 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "剪貼簿, 儲存文字"
  - "文字, 儲存在剪貼簿"
ms.assetid: 9996023f-b700-47ad-8ad9-1ba201eaa5a6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將文字儲存在剪貼簿中 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會使用定義在 <xref:System.Windows.Forms> 命名空間中的 <xref:System.Windows.Forms.Clipboard> 物件來儲存字串。  這個物件提供兩個成員函式：<xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 和 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>。  資料會藉由將任何衍生自 <xref:System.Object> 的物件傳送至 <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>，儲存至 \[剪貼簿\] 中。  
  
## 範例  
  
```  
// store_clipboard.cpp  
// compile with: /clr  
#using <System.dll>  
#using <System.Drawing.dll>  
#using <System.Windows.Forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main()  
{  
   String^ str = "This text is copied into the Clipboard.";  
  
   // Use 'true' as the second argument if  
   // the data is to remain in the clipboard  
   // after the program terminates.  
   Clipboard::SetDataObject(str, true);  
  
   Console::WriteLine("Added text to the Clipboard.");  
  
   return 0;  
}  
```  
  
## 請參閱  
 [如何：從剪貼簿擷取文字](../dotnet/how-to-retrieve-text-from-the-clipboard-cpp-cli.md)   
 [Windows 作業](../dotnet/windows-operations-cpp-cli.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)