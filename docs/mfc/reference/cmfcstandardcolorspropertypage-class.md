---
title: "CMFCStandardColorsPropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCStandardColorsPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCStandardColorsPropertyPage class"
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCStandardColorsPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示使用者使用選取色彩對話方塊的標準色彩的屬性頁。  
  
## 語法  
  
```  
class CMFCStandardColorsPropertyPage : public CPropertyPage  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|預設建構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCStandardColorsPropertyPage::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|`CMFCStandardColorsPropertyPage::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
  
### 備註  
 `CMFCColorDialog` 類別使用這個類別會顯示標準色彩屬性頁。  如需 `CMFCColorDialog` 的詳細資訊，請參閱 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)  
  
## 需求  
 **標題:** afxstandardcolorspropertypage.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCCustomColorsPropertyPage Class](../../mfc/reference/cmfccustomcolorspropertypage-class.md)