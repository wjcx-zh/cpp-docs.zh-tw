---
title: "CBrush Class | Microsoft Docs"
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
  - "CBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "筆刷, CBrush class"
  - "CBrush class"
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBrush Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 圖形裝置介面 \(GDI\) 筆刷。  
  
## 語法  
  
```  
class CBrush : public CGdiObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CBrush::CBrush](../Topic/CBrush::CBrush.md)|建構 `CBrush` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CBrush::CreateBrushIndirect](../Topic/CBrush::CreateBrushIndirect.md)|初始化與 [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) 結構指定的樣式、色彩和圖樣筆刷。|  
|[CBrush::CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md)|初始化一個與裝置無關的點陣圖指定樣式的筆刷 \(DIB\)。|  
|[CBrush::CreateHatchBrush](../Topic/CBrush::CreateHatchBrush.md)|使用指定的已規劃的樣式和色彩的筆刷。|  
|[CBrush::CreatePatternBrush](../Topic/CBrush::CreatePatternBrush.md)|初始化具有指定點陣圖中的樣式的筆刷。|  
|[CBrush::CreateSolidBrush](../Topic/CBrush::CreateSolidBrush.md)|使用指定的純色的筆刷。|  
|[CBrush::CreateSysColorBrush](../Topic/CBrush::CreateSysColorBrush.md)|建立為預設系統色彩的筆刷。|  
|[CBrush::FromHandle](../Topic/CBrush::FromHandle.md)|傳回指向 `CBrush` 物件，當指定處理視窗 `HBRUSH` 物件。|  
|[CBrush::GetLogBrush](../Topic/CBrush::GetLogBrush.md)|取得 [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) 結構。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CBrush::operator HBRUSH](../Topic/CBrush::operator%20HBRUSH.md)|傳回視窗控制代碼 `CBrush` 附加至物件。|  
  
## 備註  
 使用 `CBrush` 物件， `CBrush` 建構物件並將它傳遞給需要一個筆刷的任何 `CDC` 成員函式。  
  
 筆刷可以是實線，孵化或模式。  
  
 如需 `CBrush`的資訊，請參閱 [圖形物件](../../mfc/graphic-objects.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC PROPDLG 範例](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CBitmap Class](../../mfc/reference/cbitmap-class.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)