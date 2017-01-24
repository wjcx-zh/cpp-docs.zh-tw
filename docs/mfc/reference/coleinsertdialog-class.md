---
title: "COleInsertDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleInsertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleInsertDialog class"
  - "對話方塊, OLE"
  - "Insert Object dialog box"
  - "OLE Insert Object dialog box"
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleInsertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於 OLE 物件插入對話方塊。  
  
## 語法  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleInsertDialog::COleInsertDialog](../Topic/COleInsertDialog::COleInsertDialog.md)|建構 `COleInsertDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleInsertDialog::CreateItem](../Topic/COleInsertDialog::CreateItem.md)|建立對話方塊中選取的項目。|  
|[COleInsertDialog::DoModal](../Topic/COleInsertDialog::DoModal.md)|顯示 OLE 物件插入對話方塊。|  
|[COleInsertDialog::GetClassID](../Topic/COleInsertDialog::GetClassID.md)|取得 **CLSID** 與選取的項目。|  
|[COleInsertDialog::GetDrawAspect](../Topic/COleInsertDialog::GetDrawAspect.md)|是否會繪製項目顯示為圖示。|  
|[COleInsertDialog::GetIconicMetafile](../Topic/COleInsertDialog::GetIconicMetafile.md)|會處理這個中繼資料與此項目圖示表單。|  
|[COleInsertDialog::GetPathName](../Topic/COleInsertDialog::GetPathName.md)|具有完整路徑在對話方塊中選取的檔案。|  
|[COleInsertDialog::GetSelectionType](../Topic/COleInsertDialog::GetSelectionType.md)|取得物件的型別被選取。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleInsertDialog::m\_io](../Topic/COleInsertDialog::m_io.md)|控制項對話方塊的行為類型 **OLEUIINSERTOBJECT** 的結構。|  
  
## 備註  
 要呼叫此對話方塊時，請建立類別 `COleInsertDialog` 物件。  在 `COleInsertDialog` 在建構物件之後，您可以使用 [m\_io](../Topic/COleInsertDialog::m_io.md) 結構初始化控制項的值或狀態在對話方塊中的。  `m_io` 結構是型別 **OLEUIINSERTOBJECT**。  如需使用這個對話方塊類別的詳細資訊，請參閱 [DoModal](../Topic/COleInsertDialog::DoModal.md) 成員函式。  
  
> [!NOTE]
>  應用程式精靈所產生的容器程式碼使用這個類別。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) 結構。  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)