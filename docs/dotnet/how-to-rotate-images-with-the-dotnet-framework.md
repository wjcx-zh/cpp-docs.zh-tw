---
title: "如何： 旋轉影像以.NET Framework |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], rotating images
- graphics [C++], rotating images
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5b337186f67758d56dbc0bae06b6886f43f7435
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-rotate-images-with-the-net-framework"></a>如何：使用 .NET Framework 旋轉影像
下列程式碼範例示範如何使用<xref:System.Drawing.Image?displayProperty=fullName>類別來從磁碟載入影像、 旋轉 90 度，並將它儲存為新的.jpg 檔案。  
  
> [!NOTE]
>  GDI + 隨附於 Windows XP，並且可做為 Windows NT 4.0 SP 6、 Windows 2000、 Windows 98 和 Windows Me 的可轉散發。 若要下載最新版本可轉散發，請參閱[http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232)。 
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="see-also"></a>另請參閱  
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)