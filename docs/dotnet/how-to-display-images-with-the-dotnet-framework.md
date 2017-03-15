---
title: "如何：使用 .NET Framework 顯示影像 | Microsoft Docs"
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
  - "GDI+ [C++], 顯示影像"
  - "圖形 [C++], 顯示影像"
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 .NET Framework 顯示影像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會修改 OnPaint 事件處理常式，以擷取指向主要表單 <xref:System.Drawing.Graphics> 物件的指標。  <xref:System.Windows.Forms.Form.OnPaint%2A> 函式主要用於 Windows Form 應用程式 \(通常是使用 Visual Studio 應用程式精靈所建立\)。  
  
 影像由 <xref:System.Drawing.Image> 類別所表示。  範例會使用 <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> 方法從 .jpg 檔載入影像資料。  在影像描繪至表單之前，會調整表單大小以容納影像。  影像的描繪是使用 <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> 方法來進行。  
  
 <xref:System.Drawing.Graphics> 和 <xref:System.Drawing.Image> 類別都位於 <xref:System.Drawing?displayProperty=fullName> 命名空間中。  
  
> [!NOTE]
>  GDI\+ 內含在 Windows XP 中，而在 Windows NT 4.0 SP 6、Windows 2000、Windows 98 和 Windows Me 上則是以可轉散發檔案的方式提供。  若要下載最新的可轉散發套件，請 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232)參閱。  如需詳細資訊，請參閱 [GDI\+](_gdiplus_GDI_start_cpp) 的 GDI\+ SDK 說明文件。  
  
## 範例  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
  
protected:  
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override  
{  
    Graphics^ g = pe->Graphics;  
    Image^ image = Image::FromFile("SampleImage.jpg");  
    Form::ClientSize = image->Size;  
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );  
}  
```  
  
## 請參閱  
 <xref:System.Drawing?displayProperty=fullName>   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)