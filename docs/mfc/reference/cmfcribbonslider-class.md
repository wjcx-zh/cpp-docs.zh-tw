---
title: "CMFCRibbonSlider Class | Microsoft Docs"
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
  - "CMFCRibbonSlider"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonSlider class"
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
caps.latest.revision: 43
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonSlider Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonSlider` 類別實作可以加入至功能區列或功能區狀態列的滑桿控制項。  功能區滑桿控制項類似出現在 Office 2007 應用程式中的縮放滑桿。  
  
## 語法  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](../Topic/CMFCRibbonSlider::CMFCRibbonSlider.md)|建構和初始化功能區滑桿控制項。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonSlider::GetPos](../Topic/CMFCRibbonSlider::GetPos.md)|傳回滑桿控制項的目前位置。|  
|[CMFCRibbonSlider::GetRangeMax](../Topic/CMFCRibbonSlider::GetRangeMax.md)|傳回滑桿的最大值。|  
|[CMFCRibbonSlider::GetRangeMin](../Topic/CMFCRibbonSlider::GetRangeMin.md)|傳回滑桿的最小值。|  
|[CMFCRibbonSlider::GetRegularSize](../Topic/CMFCRibbonSlider::GetRegularSize.md)|傳回功能區項目的一般大小。  \(覆寫 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)\)。|  
|[CMFCRibbonSlider::GetZoomIncrement](../Topic/CMFCRibbonSlider::GetZoomIncrement.md)|傳回縮放增量的滑桿控制項的大小。|  
|[CMFCRibbonSlider::HasZoomButtons](../Topic/CMFCRibbonSlider::HasZoomButtons.md)|指定滑桿是否具有縮放的按鈕。|  
|[CMFCRibbonSlider::OnDraw](../Topic/CMFCRibbonSlider::OnDraw.md)|呼叫框架繪製功能區項目。  \(覆寫 [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)\)。|  
|[CMFCRibbonSlider::SetPos](../Topic/CMFCRibbonSlider::SetPos.md)|設定滑桿控制項的目前位置。|  
|[CMFCRibbonSlider::SetRange](../Topic/CMFCRibbonSlider::SetRange.md)|藉由設定最小和最大值指定滑桿控制項的範圍。|  
|[CMFCRibbonSlider::SetZoomButtons](../Topic/CMFCRibbonSlider::SetZoomButtons.md)|顯示或隱藏縮放的按鈕。|  
|[CMFCRibbonSlider::SetZoomIncrement](../Topic/CMFCRibbonSlider::SetZoomIncrement.md)|設定縮放增量的滑桿控制項的大小。|  
  
## 備註  
 您可以使用 `SetRange` 方法設定縮放增量的滑桿的範圍。  您可以使用 `SetPos` 方法，您可以設定滑桿的目前位置。  
  
 您可以使用 `SetZoomButtons` 方法，您可以顯示滑桿控制項的左右兩邊的循環縮放的按鈕。  根據預設，滑桿是水平的，左縮放\] 按鈕會顯示負號，並正確縮放按鈕顯示加號。  
  
 當使用者按一下 \[縮放\] 按鈕時， `SetZoomIncrement` 方法定義將會從目前位置減。  
  
## 範例  
 下列範例會在 `CMFCRibbonSlider` 類別會示範如何使用各種方法會設定滑桿的屬性。  這個範例顯示如何建構 `CMFCRibbonSlider` 物件，顯示縮放\] 按鈕，將滑桿控制項的目前位置，並設定其值的範圍滑桿控制項的。  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/CPP/cmfcribbonslider-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## 需求  
 **標題:** afxribbonslider.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)