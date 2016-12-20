---
title: "CFont Class | Microsoft Docs"
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
  - "CFont"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFont class"
  - "字型, MFC 類別"
  - "GDI, font classes"
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFont Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 圖形裝置介面 \(GDI\) 字型並提供管理字型的成員函式。  
  
## 語法  
  
```  
class CFont : public CGdiObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFont::CFont](../Topic/CFont::CFont.md)|建構 `CFont` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFont::CreateFont](../Topic/CFont::CreateFont.md)|使用指定的特性 `CFont` 。|  
|[CFont::CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md)|初始化與 `LOGFONT` 結構指定的 `CFont` 特性來建立物件。|  
|[CFont::CreatePointFont](../Topic/CFont::CreatePointFont.md)|使用指定的 `CFont` 高度的度量單位，以點的十分位數和字樣。|  
|[CFont::CreatePointFontIndirect](../Topic/CFont::CreatePointFontIndirect.md)|和 `CreateFontIndirect` ，除了字型高度相同點的秒為單位 \(而不是邏輯單位。|  
|[CFont::FromHandle](../Topic/CFont::FromHandle.md)|傳回指向 `CFont` 物件，當指定視窗 **HFONT**。|  
|[CFont::GetLogFont](../Topic/CFont::GetLogFont.md)|如需以邏輯字型的資訊填入 `LOGFONT` 附加至 `CFont` 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CFont::operator HFONT](../Topic/CFont::operator%20HFONT.md)|傳回 Windows GDI 字型控制代碼 `CFont` 附加至物件。|  
  
## 備註  
 若要使用 `CFont` 物件，建構一個 `CFont` 物件和其他 Windows 字型給它與 [CreateFont](../Topic/CFont::CreateFont.md)、 [CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md)、 [CreatePointFont](../Topic/CFont::CreatePointFont.md)或 [CreatePointFontIndirect](../Topic/CFont::CreatePointFontIndirect.md)，然後使用該物件的成員函式來管理字型。  
  
 因為它們會自動進行，字型高度的轉換點數大小的至邏輯單位 `CreatePointFont` 和 `CreatePointFontIndirect` 函式的 `CreateFont` 或 `CreateFontIndirect` 通常很容易使用。  
  
 如需 `CFont`的資訊，請參閱 [圖形物件](../../mfc/graphic-objects.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)