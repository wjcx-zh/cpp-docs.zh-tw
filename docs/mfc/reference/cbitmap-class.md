---
title: "CBitmap Class | Microsoft Docs"
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
  - "CBitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBitmap class"
  - "繪製, 工具"
  - "GDI bitmap"
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBitmap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 圖形裝置介面 \(GDI\) 點陣圖並提供成員函式來管理點陣圖。  
  
## 語法  
  
```  
class CBitmap : public CGdiObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CBitmap::CBitmap](../Topic/CBitmap::CBitmap.md)|建構 `CBitmap` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CBitmap::CreateBitmap](../Topic/CBitmap::CreateBitmap.md)|初始化具有指定的寬度、高度和位元模式的與裝置相關的記憶體點陣圖的物件。|  
|[CBitmap::CreateBitmapIndirect](../Topic/CBitmap::CreateBitmapIndirect.md)|初始化一個點陣圖的物件在 **點陣圖** 結構 \(如果已指定\) 指定的寬度、高度和位元組合。|  
|[CBitmap::CreateCompatibleBitmap](../Topic/CBitmap::CreateCompatibleBitmap.md)|使用點陣圖的物件，使其與指定的裝置相容。|  
|[CBitmap::CreateDiscardableBitmap](../Topic/CBitmap::CreateDiscardableBitmap.md)|初始化與指定的裝置相容的可捨棄點陣圖的物件。|  
|[CBitmap::FromHandle](../Topic/CBitmap::FromHandle.md)|傳回指向 `CBitmap` 物件，當指定處理視窗 `HBITMAP` 點陣圖。|  
|[CBitmap::GetBitmap](../Topic/CBitmap::GetBitmap.md)|如需以點陣圖的資訊填入一 **點陣圖** 結構。|  
|[CBitmap::GetBitmapBits](../Topic/CBitmap::GetBitmapBits.md)|複製指定的點陣圖位元讀入指定的緩衝區。|  
|[CBitmap::GetBitmapDimension](../Topic/CBitmap::GetBitmapDimension.md)|傳回點陣圖的寬度和高度。  這個高度和寬度所提供 [SetBitmapDimension](../Topic/CBitmap::SetBitmapDimension.md) 成員函式之前設定。|  
|[CBitmap::LoadBitmap](../Topic/CBitmap::LoadBitmap.md)|透過載入具名點陣圖資源從應用程式的可執行檔和附加點陣圖初始化物件至物件。|  
|[CBitmap::LoadMappedBitmap](../Topic/CBitmap::LoadMappedBitmap.md)|載入點陣圖並將色彩對應至目前的系統色彩。|  
|[CBitmap::LoadOEMBitmap](../Topic/CBitmap::LoadOEMBitmap.md)|透過載入預先定義的 Windows 點陣圖和附加點陣圖初始化物件至物件。|  
|[CBitmap::SetBitmapBits](../Topic/CBitmap::SetBitmapBits.md)|將點陣圖的  欄位設定為指定的欄位值。|  
|[CBitmap::SetBitmapDimension](../Topic/CBitmap::SetBitmapDimension.md)|指定寬度和高度為 0.1 公釐為單位的點陣圖。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CBitmap::operator HBITMAP](../Topic/CBitmap::operator%20HBITMAP.md)|傳回視窗控制代碼 `CBitmap` 附加至物件。|  
  
## 備註  
 若要使用 `CBitmap` 物件，請建構物件，將點陣圖控制代碼來初始化其中一個成員函式，然後呼叫物件的成員函式。  
  
 如需使用圖形物件的詳細資訊 `CBitmap`，請參閱 [圖形物件](../../mfc/graphic-objects.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)