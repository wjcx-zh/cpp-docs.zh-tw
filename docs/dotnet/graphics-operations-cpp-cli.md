---
title: 圖形作業 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- GDI+ [C++]
- .NET Framework [C++], graphics
- images [C++], .NET Framework and
- GDI+ [C++], about graphics operations
- graphics [C++], .NET Framework and
- GDI+ [C++], displaying images
- graphics [C++], displaying images
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
- GDI+ [C++], rotating images
- graphics [C++], rotating images
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: bba27228-b9b3-4c9c-b31c-a04b76702a95
ms.openlocfilehash: c7c6d62eb4059069e6e266544ce6323c63dd15c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393736"
---
# <a name="graphics-operations-ccli"></a>圖形作業 (C++/CLI)

示範如何使用 Windows SDK 的影像操作。

下列主題示範如何使用<xref:System.Drawing.Image?displayProperty=fullName>執行影像操作的類別。

## <a name="display"></a> 使用.NET Framework 顯示影像

下列程式碼範例會修改 OnPaint 事件處理常式，來擷取變數的指標，<xref:System.Drawing.Graphics>主要表單的物件。 <xref:System.Windows.Forms.Form.OnPaint%2A>函式適用於 Windows Forms 應用程式，很可能使用精靈建立的 Visual Studio 應用程式。

表示影像<xref:System.Drawing.Image>類別。 映像載入的資料會從.jpg 檔案使用<xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>方法。 繪製至表單的影像之前，表單會調整大小以容納影像。 繪製影像利用<xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName>方法。

<xref:System.Drawing.Graphics>並<xref:System.Drawing.Image>類別都在<xref:System.Drawing?displayProperty=fullName>命名空間。

### <a name="example"></a>範例

```cpp
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

## <a name="draw"></a> 使用.NET Framework 繪製圖案

下列程式碼範例會使用<xref:System.Drawing.Graphics>類別，以修改<xref:System.Windows.Forms.Form.OnPaint%2A>事件處理常式來擷取變數的指標，<xref:System.Drawing.Graphics>主要表單的物件。 設定表單的背景色彩來繪製線條和弧形使用再使用此指標<xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>和<xref:System.Drawing.Graphics.DrawArc%2A>方法。

### <a name="example"></a>範例

```cpp
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

## <a name="rotate"></a> 使用.NET Framework 旋轉影像

下列程式碼範例示範使用<xref:System.Drawing.Image?displayProperty=fullName>從磁碟載入影像、 旋轉 90 度，並將它儲存為新的.jpg 檔案的類別。

### <a name="example"></a>範例

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );
   image->Save("SampleImage_rotated.jpg");
   return 0;
}
```

## <a name="convert"></a> 轉換影像檔案格式，使用.NET Framework

下列程式碼範例示範<xref:System.Drawing.Image?displayProperty=fullName>類別和<xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName>列舉，用來轉換和儲存影像檔。 下列程式碼會從.jpg 檔案載入影像，並再將它儲存在.gif 和.bmp 檔案格式。

### <a name="example"></a>範例

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;
using namespace System::Drawing::Imaging;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->Save("SampleImage.png", ImageFormat::Png);
   image->Save("SampleImage.bmp", ImageFormat::Bmp);

   return 0;
}
```

## <a name="related-sections"></a>相關章節

[圖形程式設計入門](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[關於 GDI+ Managed 程式碼](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
