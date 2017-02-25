---
title: "CRichEditCntrItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditCntrItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCntrItem class"
  - "OLE items, in rich edit views"
  - "Rich Edit 控制項, OLE items"
  - "Rich Edit 控制項, 使用"
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CRichEditCntrItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CRichEditView](../../mfc/reference/cricheditview-class.md) 和 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)， MFC 中的文件檢視架構內容中提供 Rich Edit 控制項的功能。  
  
## 語法  
  
```  
class CRichEditCntrItem : public COleClientItem  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditCntrItem::CRichEditCntrItem](../Topic/CRichEditCntrItem::CRichEditCntrItem.md)|建構 `CRichEditCntrItem` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditCntrItem::SyncToRichEditObject](../Topic/CRichEditCntrItem::SyncToRichEditObject.md)|啟動項目做為另一個型別。|  
  
## 備註  
 「Rich Edit 控制項」是使用者可以輸入和編輯文字的視窗。  文字指派字元和段落格式，並且可以包含內嵌的 OLE 物件。  Rich Edit 控制項提供格式化文字提供程式設計介面。  然而，應用程式必須實作所有必要使用者介面的元件已格式化作業給使用者使用。  
  
 `CRichEditView` 維持文字和格式一般文字。  `CRichEditDoc` 維護這個檢視 OLE 用戶端項目的清單。  `CRichEditCntrItem` 提供容器的存取 OLE 用戶端項目。  
  
 這個 Windows 通用控制項 \(也 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 和相關類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需使用範例豐富只要在 MFC 應用程式的容器項目，請 [WORDPAD](../../top/visual-cpp-samples.md) 範例應用程式。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## 需求  
 **Header:** afxrich.h  
  
## 請參閱  
 [MFC 範例 WORDPAD](../../top/visual-cpp-samples.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc Class](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)