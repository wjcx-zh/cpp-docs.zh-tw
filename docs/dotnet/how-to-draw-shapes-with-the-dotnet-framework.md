---
title: 如何： 使用.NET Framework 繪製圖案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 877e78b1ce4f81af76aa20961ea05d18e64f58f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130031"
---
# <a name="how-to-draw-shapes-with-the-net-framework"></a>如何：使用 .NET Framework 繪製圖案
下列程式碼範例使用<xref:System.Drawing.Graphics>類別以修改<xref:System.Windows.Forms.Form.OnPaint%2A>事件處理常式來擷取指標<xref:System.Drawing.Graphics>主要表單的物件。 此指標然後用來設定表單的背景色彩和繪製一條線與弧線使用<xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>和<xref:System.Drawing.Graphics.DrawArc%2A>方法。  
  
## <a name="example"></a>範例  
  
```  
#using <system.drawing.dll>  
using namespace System;  
using namespace System::Drawing;  
// ...  
protected:   
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override  
{  
   Graphics^ g = pe->Graphics;  
   g->Clear(Color::AntiqueWhite);  
  
   Rectangle rect = Form::ClientRectangle;  
   Rectangle smallRect;  
   smallRect.X = rect.X + rect.Width / 4;  
   smallRect.Y = rect.Y + rect.Height / 4;  
   smallRect.Width = rect.Width / 2;  
   smallRect.Height = rect.Height / 2;  
  
   Pen^ redPen = gcnew Pen(Color::Red);  
   redPen->Width = 4;  
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);  
  
   Pen^ bluePen = gcnew Pen(Color::Blue);  
   bluePen->Width = 10;  
   g->DrawArc( bluePen, smallRect, 90, 270 );  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [.NET 程式設計使用 C + + /CLI （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [System::Drawing 命名空間](https://msdn.microsoft.com/en-us/library/system.drawing.aspx)