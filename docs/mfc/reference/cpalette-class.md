---
title: "CPalette Class | Microsoft Docs"
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
  - "CPalette"
  - "HPALETTE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "色板, MFC"
  - "CPalette class"
  - "HPALETTE"
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPalette Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 色板。  
  
## 語法  
  
```  
class CPalette : public CGdiObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPalette::CPalette](../Topic/CPalette::CPalette.md)|建構 `CPalette` 物件未附加的 Windows 調色盤。  在使用之前，您必須初始化使用其中一個 `CPalette` 物件初始化成員函式它。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPalette::AnimatePalette](../Topic/CPalette::AnimatePalette.md)|取代 `CPalette` 物件識別之邏輯調色盤的輸入。  因為 Windows 立即，將新的輸入系統調色盤應用程式不需要更新其工作區。|  
|[CPalette::CreateHalftonePalette](../Topic/CPalette::CreateHalftonePalette.md)|建立裝置內容的半色調調色盤並將其附加至 `CPalette` 物件。|  
|[CPalette::CreatePalette](../Topic/CPalette::CreatePalette.md)|建立視窗色板並將其附加至 `CPalette` 物件。|  
|[CPalette::FromHandle](../Topic/CPalette::FromHandle.md)|傳回指向 `CPalette` 物件，將控制代碼 Windows 調色盤物件。|  
|[CPalette::GetEntryCount](../Topic/CPalette::GetEntryCount.md)|擷取調色盤項目數目的邏輯調色盤。|  
|[CPalette::GetNearestPaletteIndex](../Topic/CPalette::GetNearestPaletteIndex.md)|傳回項目的索引 \(從最符合色彩值的邏輯調色盤。|  
|[CPalette::GetPaletteEntries](../Topic/CPalette::GetPaletteEntries.md)|擷取調色盤項目中某個範圍的邏輯調色盤。|  
|[CPalette::ResizePalette](../Topic/CPalette::ResizePalette.md)|將變更為指定的項目數的 `CPalette` 物件指定的邏輯調色盤的大小。|  
|[CPalette::SetPaletteEntries](../Topic/CPalette::SetPaletteEntries.md)|在輸入範圍設定 RGB 色彩值和旗標一個邏輯調色盤。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CPalette::operator HPALETTE](../Topic/CPalette::operator%20HPALETTE.md)|傳回 `HPALETTE` 附加至 `CPalette`。|  
  
## 備註  
 調色盤提供應用程式和色彩輸出裝置之間的介面 \(例如顯示裝置\)。  介面可以讓應用程式使用輸出裝置的色彩功能的嚴重的，而不會干擾其他應用程式顯示的色彩。   視窗中使用應用程式的邏輯色板 \(需要的色彩清單\) 和定義可用的色彩\) 的系統調色盤 \(判斷使用的色彩。  
  
 `CPalette` 物件提供管理物件參考的調色盤提供成員函式。  `CPalette` 建構物件並使用其成員函式建立實際調色盤，圖形裝置介面 \(GDI\) 物件並管理其型別和其他屬性。  
  
 如需使用 `CPalette`的資訊，請參閱 [圖形物件](../../mfc/graphic-objects.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 DIBLOOK](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](../Topic/CPalette::GetPaletteEntries.md)   
 [CPalette::SetPaletteEntries](../Topic/CPalette::SetPaletteEntries.md)