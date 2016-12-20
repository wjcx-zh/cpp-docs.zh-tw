---
title: "CRichEditDoc Class | Microsoft Docs"
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
  - "CRichEditDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditDoc class"
  - "document/view architecture, Rich Edit 控制項"
  - "文件, rich edit"
  - "OLE containers, rich edit"
  - "Rich Edit 控制項, OLE container"
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRichEditDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CRichEditView](../../mfc/reference/cricheditview-class.md) 和 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)， MFC 中的文件檢視架構內容中提供 Rich Edit 控制項的功能。  
  
## 語法  
  
```  
  
class CRichEditDoc : public COleServerDoc  
  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditDoc::CreateClientItem](../Topic/CRichEditDoc::CreateClientItem.md)|呼叫執行文件的清除。|  
|[CRichEditDoc::GetStreamFormat](../Topic/CRichEditDoc::GetStreamFormat.md)|指示資料流輸入和輸出是否應該包含格式資訊。|  
|[CRichEditDoc::GetView](../Topic/CRichEditDoc::GetView.md)|擷取 asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md) 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditDoc::m\_bRTF](../Topic/CRichEditDoc::m_bRTF.md)|指示資料流 I\/O 是否應該包含格式化。|  
  
## 備註  
 「Rich Edit 控制項」是使用者可以輸入和編輯文字的視窗。  文字指派字元和段落格式，並且可以包含內嵌的 OLE 物件。  Rich Edit 控制項提供格式化文字提供程式設計介面。  然而，應用程式必須實作所有必要使用者介面的元件已格式化作業給使用者使用。  
  
 `CRichEditView` 維持文字和格式一般文字。  `CRichEditDoc` 維護這個檢視的用戶端項目清單。  `CRichEditCntrItem` 提供容器的存取 OLE 用戶端項目。  
  
 這個 Windows 通用控制項 \(也 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 和相關類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需使用範例的豐富的編輯文件在 MFC 應用程式，請參閱 [WORDPAD](../../top/visual-cpp-samples.md) 範例應用程式。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## 需求  
 **Header:** afxrich.h  
  
## 請參閱  
 [MFC 範例 WORDPAD](../../top/visual-cpp-samples.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)   
 [CRichEditCntrItem Class](../../mfc/reference/cricheditcntritem-class.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [CRichEditCtrl Class](../../mfc/reference/cricheditctrl-class.md)