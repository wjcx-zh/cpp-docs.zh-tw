---
title: 如何： 顯示映像以.NET Framework |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a7f3ed2d8fe90501b5ef3d0ae5028890fe5290e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-images-with-the-net-framework"></a>如何：使用 .NET Framework 顯示影像
下列程式碼範例會修改 OnPaint 事件處理常式，以擷取指標<xref:System.Drawing.Graphics>主要表單的物件。 <xref:System.Windows.Forms.Form.OnPaint%2A>函式適用於 Windows Forms 應用程式，很可能是使用 Visual Studio 應用程式精靈建立。  
  
 影像由<xref:System.Drawing.Image>類別。 影像資料從使用.jpg 檔案載入<xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>方法。 影像繪製至表單之前，表單會調整大小以容納影像。 繪製影像利用<xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName>方法。  
  
 <xref:System.Drawing.Graphics>和<xref:System.Drawing.Image>類別都會在<xref:System.Drawing?displayProperty=fullName>命名空間。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing?displayProperty=fullName>   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)