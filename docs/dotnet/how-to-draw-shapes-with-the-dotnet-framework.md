---
title: "如何：使用 .NET Framework 繪製圖案 | Microsoft Docs"
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
  - "繪製, 圖案"
  - "GDI+, 繪製圖案"
  - "圖案"
  - "圖案, 繪製"
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 .NET Framework 繪製圖案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會使用 <xref:System.Drawing.Graphics> 類別 \(Class\)，修改 <xref:System.Windows.Forms.Form.OnPaint%2A> 事件處理常式，為主要表單擷取指向 <xref:System.Drawing.Graphics> 物件的指標。  接著會使用這個指標設定表單的背景色彩，並使用 <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> 和 <xref:System.Drawing.Graphics.DrawArc%2A> 方法繪製線條和弧形。  
  
> [!NOTE]
>  GDI\+ 內含在 Windows XP 中，而在 Windows NT 4.0 SP 6、Windows 2000、Windows 98 和 Windows Me 上則是以可轉散發檔案的方式提供。  若要下載最新的可轉散發套件，請 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232)參閱。  如需詳細資訊，請參閱 [GDI\+](_gdiplus_GDI_start_cpp)。  
  
## 範例  
  
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
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [System::Drawing 命名空間](https://msdn.microsoft.com/en-us/library/system.drawing.aspx)