---
title: "如何： 轉換使用.NET Framework 的影像檔案格式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: 5d5384b0-b9b7-4262-b9ad-c4cb95f75ee4
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dc2b84063c509cd870b5d02fa0a209b511d8a0f3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-convert-image-file-formats-with-the-net-framework"></a>如何：使用 .NET Framework 轉換影像檔格式
下列程式碼範例示範<xref:System.Drawing.Image?displayProperty=fullName>類別和<xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName>列舉用來轉換並儲存映像檔案。 下列程式碼載入.jpg 檔案的映像，然後將它儲存在.gif 和.bmp 檔案格式。  
  
> [!NOTE]
>  GDI + 隨附於 Windows XP、 Windows Server 2003 和 Windows Vista，並且可做為 Windows 2000 的可轉散發。 若要下載最新版本可轉散發，請參閱[http://go.microsoft.com/fwlink/p/?linkid=11232](http://go.microsoft.com/fwlink/p/?linkid=11232)。   
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing>   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)