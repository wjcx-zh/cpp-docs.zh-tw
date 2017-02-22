---
title: "CMFCPropertyGridColorProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridColorProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridColorProperty class"
  - "CMFCPropertyGridColorProperty::FormatProperty method"
  - "CMFCPropertyGridColorProperty::OnClickButton method"
  - "CMFCPropertyGridColorProperty::OnDrawValue method"
  - "CMFCPropertyGridColorProperty::OnEdit method"
  - "CMFCPropertyGridColorProperty::OnUpdateValue method"
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCPropertyGridColorProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertyGridColorProperty` 類別支援開啟色彩選取對話方塊的屬性清單控制項項目。  
  
## 語法  
  
```  
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](../Topic/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty.md)|建構 `CMFCPropertyGridColorProperty` 物件。|  
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](../Topic/CMFCPropertyGridColorProperty::EnableAutomaticButton.md)|啟用色彩選取對話方塊上的 \[*自動*\] 按鈕。  \(標準自動按鈕的標籤為**自動**。\)|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](../Topic/CMFCPropertyGridColorProperty::EnableOtherButton.md)|啟用色彩選取對話方塊上的 \[*其他*\] 按鈕。  \(標準其他按鈕的標籤為**更多色彩**。\)|  
|`CMFCPropertyGridColorProperty::FormatProperty`|格式化屬性值的文字表示法。  \(覆寫 [CMFCPropertyGridProperty::FormatProperty](../Topic/CMFCPropertyGridProperty::FormatProperty.md)。\)|  
|[CMFCPropertyGridColorProperty::GetColor](../Topic/CMFCPropertyGridColorProperty::GetColor.md)|取得屬性的目前色彩。|  
|`CMFCPropertyGridColorProperty::GetThisClass`|由取得與此類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件標的架構使用。|  
|`CMFCPropertyGridColorProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。  \(覆寫 [CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md)。\)|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|由架構呼叫以顯示屬性值。  \(覆寫 [CMFCPropertyGridProperty::OnDrawValue](../Topic/CMFCPropertyGridProperty::OnDrawValue.md)。\)|  
|`CMFCPropertyGridColorProperty::OnEdit`|使用者即將修改屬性值時由架構呼叫。  \(覆寫 [CMFCPropertyGridProperty::OnEdit](../Topic/CMFCPropertyGridProperty::OnEdit.md)。\)|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|當可編輯屬性的值變更時由架構呼叫。  \(覆寫 [CMFCPropertyGridProperty::OnUpdateValue](../Topic/CMFCPropertyGridProperty::OnUpdateValue.md)。\)|  
|[CMFCPropertyGridColorProperty::SetColor](../Topic/CMFCPropertyGridColorProperty::SetColor.md)|設定屬性的新色彩。|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](../Topic/CMFCPropertyGridColorProperty::SetColumnsNumber.md)|指定目前色彩屬性格線中的資料行數目。|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](../Topic/CMFCPropertyGridColorProperty::SetOriginalValue.md)|設定可編輯屬性的原始值。|  
  
## 備註  
 `CMFCPropertyGridColorProperty` 類別支援的色彩屬性可以加入至屬性清單控制項。  如需詳細資訊，請參閱 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)。  
  
## 範例  
 下列範例示範如何建構 `CMFCPropertyGridColorProperty` 類別的物件，以及使用 `CMFCPropertyGridColorProperty` 類別的各種方法來設定此物件。  程式碼說明如何啟用自動和其他按鈕，以及如何設定色彩和資料行數目。  這個範例是[新控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#13](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#13)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)  
  
## 需求  
 **標頭：**afxpropertygridctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)