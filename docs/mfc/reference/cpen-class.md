---
title: "CPen Class | Microsoft Docs"
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
  - "HPEN"
  - "CPen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPen class"
  - "HPEN"
  - "畫筆, MFC"
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPen Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 圖形裝置介面 \(GDI\) 畫筆。  
  
## 語法  
  
```  
class CPen : public CGdiObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPen::CPen](../Topic/CPen::CPen.md)|建構 `CPen` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPen::CreatePen](../Topic/CPen::CreatePen.md)|建立一個邏輯化妝產品或幾何畫筆與指定的樣式、寬度和筆刷屬性，並將其附加至 `CPen` 物件。|  
|[CPen::CreatePenIndirect](../Topic/CPen::CreatePenIndirect.md)|建立與 [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) 結構指定的樣式、寬度和色彩的畫筆，並將其附加至 `CPen` 物件。|  
|[CPen::FromHandle](../Topic/CPen::FromHandle.md)|傳回指向 `CPen` 物件，當指定視窗 `HPEN`。|  
|[CPen::GetExtLogPen](../Topic/CPen::GetExtLogPen.md)|取得 [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) 基礎結構。|  
|[CPen::GetLogPen](../Topic/CPen::GetLogPen.md)|取得 [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) 基礎結構。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CPen::operator HPEN](../Topic/CPen::operator%20HPEN.md)|傳回視窗控制代碼 `CPen` 附加至物件。|  
  
## 備註  
 如需使用 `CPen`的資訊，請參閱 [圖形物件](../../mfc/graphic-objects.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CBrush Class](../../mfc/reference/cbrush-class.md)