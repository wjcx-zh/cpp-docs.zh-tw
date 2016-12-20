---
title: "CGdiObject Class | Microsoft Docs"
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
  - "CGdiObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "筆刷, base class for"
  - "CGdiObject class"
  - "字型, base class for"
  - "GDI 物件, base class for"
  - "調色盤, base class for"
  - "畫筆, base class for"
  - "區域, base class for"
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CGdiObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供各種視窗圖形裝置介面 \(GDI\) 物件提供基底類別 \(例如點陣圖、區域、筆刷、畫筆、調色盤和字型。  
  
## 語法  
  
```  
class CGdiObject : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CGdiObject::CGdiObject](../Topic/CGdiObject::CGdiObject.md)|建構 `CGdiObject` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CGdiObject::Attach](../Topic/CGdiObject::Attach.md)|附加至 `CGdiObject` 物件的 Windows GDI 物件。|  
|[CGdiObject::CreateStockObject](../Topic/CGdiObject::CreateStockObject.md)|擷取控制代碼為其中一個視窗預先定義的內建 \(Stock\) 字型、筆刷、畫筆。|  
|[CGdiObject::DeleteObject](../Topic/CGdiObject::DeleteObject.md)|刪除釋放附加到從記憶體中的物件 `CGdiObject` Windows GDI 物件所有系統儲存區相關聯的物件。|  
|[CGdiObject::DeleteTempMap](../Topic/CGdiObject::DeleteTempMap.md)|刪除 `FromHandle`建立的所有 `CGdiObject` 暫存物件。|  
|[CGdiObject::Detach](../Topic/CGdiObject::Detach.md)|中斷連結 `CGdiObject` 物件的 Windows GDI 物件並將控制代碼傳回給 Windows GDI 物件。|  
|[CGdiObject::FromHandle](../Topic/CGdiObject::FromHandle.md)|傳回指向 `CGdiObject` 物件會以處理 Windows GDI 物件。|  
|[CGdiObject::GetObject](../Topic/CGdiObject::GetObject.md)|以描述附加的 Windows GDI 物件 `CGdiObject` 物件的資料填入緩衝區。|  
|[CGdiObject::GetObjectType](../Topic/CGdiObject::GetObjectType.md)|擷取 GDI 物件的型別。|  
|[CGdiObject::GetSafeHandle](../Topic/CGdiObject::GetSafeHandle.md)|傳回 `m_hObject` ，除非 `this` 是 `NULL`，在這種情況下， `NULL` 傳回情況下。|  
|[CGdiObject::UnrealizeObject](../Topic/CGdiObject::UnrealizeObject.md)|將筆刷的原點或重設了邏輯色板。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CGdiObject::operator \!\=](../Topic/CGdiObject::operator%20!=.md)|判斷兩個物件是否未 GDI 邏輯相等。|  
|[CGdiObject::operator \=\=](../Topic/CGdiObject::operator%20==.md)|判斷兩個物件是否為 GDI 邏輯相等。|  
|[CGdiObject::operator HGDIOBJ](../Topic/CGdiObject::operator%20HGDIOBJ.md)|擷取 `HANDLE` 附加的 Windows GDI 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CGdiObject::m\_hObject](../Topic/CGdiObject::m_hObject.md)|包含 `HBITMAP`、 `HPALETTE`、 `HRGN`、 `HBRUSH`、 `HPEN`或 `HFONT` 的 `HANDLE` 附加至這個物件。|  
  
## 備註  
 您絕對不會直接建立 `CGdiObject` 。  相反地，可從其中一個衍生類別的物件，例如 `CPen` 或 `CBrush`。  
  
 如需 `CGdiObject` 的詳細資訊，請參閱 [圖形物件](../../mfc/graphic-objects.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CBitmap Class](../../mfc/reference/cbitmap-class.md)   
 [CBrush Class](../../mfc/reference/cbrush-class.md)   
 [CFont Class](../../mfc/reference/cfont-class.md)   
 [CPalette Class](../../mfc/reference/cpalette-class.md)   
 [CPen Class](../../mfc/reference/cpen-class.md)   
 [CRgn 類別](../../mfc/reference/crgn-class.md)