---
title: "如何：使用 .NET Framework 旋轉影像 | Microsoft Docs"
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
  - "GDI+ [C++], 旋轉影像"
  - "圖形 [C++], 旋轉影像"
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 .NET Framework 旋轉影像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範使用 <xref:System.Drawing.Image?displayProperty=fullName> 類別 \(Class\) 從磁碟載入影像、旋轉影像 90 度，然後儲存為新的 .jpg 檔。  
  
> [!NOTE]
>  GDI\+ 內含在 Windows XP 中，而在 Windows NT 4.0 SP 6、Windows 2000、Windows 98 和 Windows Millennium Edition 上則是以可轉散發檔案的方式提供。  若要下載最新的可轉散發套件，請 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232)參閱。  如需詳細資訊，請參閱 [GDI\+](_gdiplus_GDI_start_cpp)。  
  
## 範例  
  
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
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)