---
title: "CMFCPropertyGridFontProperty Class | Microsoft Docs"
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
  - "CMFCPropertyGridFontProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridFontProperty class"
  - "CMFCPropertyGridFontProperty::FormatProperty method"
  - "CMFCPropertyGridFontProperty::OnClickButton method"
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertyGridFontProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertyGridFileProperty` 類別支援開啟字型選取對話方塊的屬性清單控制項項目。  
  
## 語法  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](../Topic/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty.md)|建構 `CMFCPropertyGridFontProperty` 物件。|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|格式化屬性值的文字表示。  \(覆寫 [CMFCPropertyGridProperty::FormatProperty](../Topic/CMFCPropertyGridProperty::FormatProperty.md)\)。|  
|[CMFCPropertyGridFontProperty::GetColor](../Topic/CMFCPropertyGridFontProperty::GetColor.md)|擷取使用者從 \[字型\] 對話方塊中選取的字型色彩。|  
|[CMFCPropertyGridFontProperty::GetLogFont](../Topic/CMFCPropertyGridFontProperty::GetLogFont.md)|擷取使用者從 \[字型\] 對話方塊中選取的字型。|  
|`CMFCPropertyGridFontProperty::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|`CMFCPropertyGridFontProperty::OnClickButton`|呼叫框架，當使用者按一下屬性中的按鈕。  \(覆寫 [CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md)\)。|  
  
## 備註  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## 需求  
 **標題:** afxpropertygridctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)