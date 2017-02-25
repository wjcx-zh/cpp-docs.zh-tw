---
title: "COlePasteSpecialDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COlePasteSpecialDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePasteSpecialDialog class"
  - "對話方塊, Paste Special"
  - "OLE Paste Special dialog box"
  - "Paste Special dialog box"
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COlePasteSpecialDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於 OLE 貼上資料編輯對話方塊。  
  
## 語法  
  
```  
  
class COlePasteSpecialDialog : public COleDialog  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](../Topic/COlePasteSpecialDialog::COlePasteSpecialDialog.md)|建構 `COlePasteSpecialDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COlePasteSpecialDialog::AddFormat](../Topic/COlePasteSpecialDialog::AddFormat.md)|將自訂格式加入至您的應用程式可貼上格式的清單。|  
|[COlePasteSpecialDialog::AddLinkEntry](../Topic/COlePasteSpecialDialog::AddLinkEntry.md)|將新項目加入至支援的剪貼簿格式清單。|  
|[COlePasteSpecialDialog::AddStandardFormats](../Topic/COlePasteSpecialDialog::AddStandardFormats.md)|將 **CF\_BITMAP**， **CF\_DIB**， `CF_METAFILEPICT`，，並選擇性地將您的應用程式可貼上格式清單的 `CF_LINKSOURCE` 。|  
|[COlePasteSpecialDialog::CreateItem](../Topic/COlePasteSpecialDialog::CreateItem.md)|使用指定的格式，建立在 \[Bin\] 資料夾中的項目。|  
|[COlePasteSpecialDialog::DoModal](../Topic/COlePasteSpecialDialog::DoModal.md)|顯示 OLE 貼上資料編輯對話方塊。|  
|[COlePasteSpecialDialog::GetDrawAspect](../Topic/COlePasteSpecialDialog::GetDrawAspect.md)|告知是否繪製項目顯示為圖示。|  
|[COlePasteSpecialDialog::GetIconicMetafile](../Topic/COlePasteSpecialDialog::GetIconicMetafile.md)|會處理這個中繼資料與此項目圖示表單。|  
|[COlePasteSpecialDialog::GetPasteIndex](../Topic/COlePasteSpecialDialog::GetPasteIndex.md)|取得使用者選取可用的貼上選取之的索引。|  
|[COlePasteSpecialDialog::GetSelectionType](../Topic/COlePasteSpecialDialog::GetSelectionType.md)|取得選取範圍的型別被選取。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COlePasteSpecialDialog::m\_ps](../Topic/COlePasteSpecialDialog::m_ps.md)|控制項對話方塊的函式型別 **OLEUIPASTESPECIAL** 的結構。|  
  
## 備註  
 要呼叫此對話方塊時，請建立類別 `COlePasteSpecialDialog` 物件。  在 `COlePasteSpecialDialog` 在建構物件之後，您可以使用 [AddFormat](../Topic/COlePasteSpecialDialog::AddFormat.md) 和 [AddStandardFormats](../Topic/COlePasteSpecialDialog::AddStandardFormats.md) 成員函式加入剪貼簿格式加入至對話方塊。  您也可以使用 [m\_ps](../Topic/COlePasteSpecialDialog::m_ps.md) 結構初始化控制項的值或狀態在對話方塊中的。  `m_ps` 結構是型別 **OLEUIPASTESPECIAL**。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) 結構。  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)