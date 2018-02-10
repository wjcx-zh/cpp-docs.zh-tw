---
title: "如何： 顯示映像以.NET Framework |Microsoft 文件"
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
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f50659832e04c3b8938c50bedc47b3ac770a52eb
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing?displayProperty=fullName>   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)