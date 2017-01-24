---
title: "CDrawingManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDrawingManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDrawingManager class"
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
caps.latest.revision: 30
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDrawingManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDrawingManager` 類別實作複雜描繪演算法。  
  
## 語法  
  
```  
class CDrawingManager : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDrawingManager::CDrawingManager](../Topic/CDrawingManager::CDrawingManager.md)|建構 `CDrawingManager` 物件。|  
|`CDrawingManager::~CDrawingManager`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDrawingManager::CreateBitmap\_32](../Topic/CDrawingManager::CreateBitmap_32.md)|建立應用程式可以將直接寫入的 32 位元與裝置無關的點陣圖 \(DIB\)。|  
|[CDrawingManager::DrawAlpha](../Topic/CDrawingManager::DrawAlpha.md)|顯示具有透明或半透明的像素的點陣圖。|  
|[CDrawingManager::DrawRotated](../Topic/CDrawingManager::DrawRotated.md)|由\- 90 度旋轉來源 DC 內容可包含指定的矩形。|  
|[CDrawingManager::DrawEllipse](../Topic/CDrawingManager::DrawEllipse.md)|繪製所提供的填滿色彩和框線的橢圓形。|  
|[CDrawingManager::DrawGradientRing](../Topic/CDrawingManager::DrawGradientRing.md)|繪製環並以色彩漸層填滿它。|  
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](../Topic/CDrawingManager::DrawLine,%20CDrawingManager::DrawLineA.md)|繪製線條。|  
|[CDrawingManager::DrawRect](../Topic/CDrawingManager::DrawRect.md)|繪製所提供的填滿色彩和框線的矩形。|  
|[CDrawingManager::DrawShadow](../Topic/CDrawingManager::DrawShadow.md)|繪製矩形區域的陰影。|  
|[CDrawingManager::Fill4ColorsGradient](../Topic/CDrawingManager::Fill4ColorsGradient.md)|以雙色漸層填滿矩形區域。|  
|[CDrawingManager::FillGradient](../Topic/CDrawingManager::FillGradient.md)|使用指定的色彩漸層填滿矩形區域。|  
|[CDrawingManager::FillGradient2](../Topic/CDrawingManager::FillGradient2.md)|使用指定的色彩漸層填滿矩形區域。  漸層中的色彩變更方向來指定。|  
|[CDrawingManager::GrayRect](../Topic/CDrawingManager::GrayRect.md)|使用指定的灰色色彩來填滿矩形。|  
|[CDrawingManager::HighlightRect](../Topic/CDrawingManager::HighlightRect.md)|反白顯示矩形區域。|  
|[CDrawingManager::HLStoRGB\_ONE](../Topic/CDrawingManager::HLStoRGB_ONE.md)|從轉換成 HLS 表示的 RGB 色彩設成表示。|  
|[CDrawingManager::HLStoRGB\_TWO](../Topic/CDrawingManager::HLStoRGB_TWO.md)|從轉換成 HLS 表示的 RGB 色彩設成表示。|  
|[CDrawingManager::HSVtoRGB](../Topic/CDrawingManager::HSVtoRGB.md)|從轉換成 HSV 表示的 RGB 色彩設成表示。|  
|[CDrawingManager::HuetoRGB](../Topic/CDrawingManager::HuetoRGB.md)|轉換色彩值為紅色，綠色或藍色元件的 Helper 方法。|  
|[CDrawingManager::MirrorRect](../Topic/CDrawingManager::MirrorRect.md)|翻轉矩形區域。|  
|[CDrawingManager::PixelAlpha](../Topic/CDrawingManager::PixelAlpha.md)|判斷某個半透明的最後一個像素的色彩的 Helper 方法。|  
|[CDrawingManager::PrepareShadowMask](../Topic/CDrawingManager::PrepareShadowMask.md)|建立可以用來做為陰影的點陣圖。|  
|[CDrawingManager::RGBtoHSL](../Topic/CDrawingManager::RGBtoHSL.md)|轉換 RGB 表示的色彩為 HSL 表示。|  
|[CDrawingManager::RGBtoHSV](../Topic/CDrawingManager::RGBtoHSV.md)|轉換 RGB 表示的 HSV 色彩設成表示。|  
|[CDrawingManager::SetAlphaPixel](../Topic/CDrawingManager::SetAlphaPixel.md)|色彩在點陣圖建立透明的像素的 Helper 方法。|  
|[CDrawingManager::SetPixel](../Topic/CDrawingManager::SetPixel.md)|將點陣圖的單一像素為指定色彩的 Helper 方法。|  
|[CDrawingManager::SmartMixColors](../Topic/CDrawingManager::SmartMixColors.md)|群組依據的重比的兩個色彩。|  
  
## 備註  
 `CDrawingManager` 類別用於描繪陰影、色彩漸層和反白顯示矩形的函式。  它也會執行 Alpha 混色。  您可以使用這個類別直接變更應用程式的 UI。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)  
  
## 需求  
 **標題:** afxdrawmanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)