---
title: "COleConvertDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleConvertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleConvertDialog class"
  - "轉換對話方塊"
  - "對話方塊, OLE"
  - "OLE Convert dialog box"
  - "OLE 對話方塊, Convert"
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleConvertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) 結構。  
  
## 語法  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleConvertDialog::COleConvertDialog](../Topic/COleConvertDialog::COleConvertDialog.md)|建構 `COleConvertDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleConvertDialog::DoConvert](../Topic/COleConvertDialog::DoConvert.md)|執行在  對話方塊中指定的型別轉換。|  
|[COleConvertDialog::DoModal](../Topic/COleConvertDialog::DoModal.md)|顯示 OLE 變更項目對話方塊。|  
|[COleConvertDialog::GetClassID](../Topic/COleConvertDialog::GetClassID.md)|取得 **CLSID** 與選取的項目。|  
|[COleConvertDialog::GetDrawAspect](../Topic/COleConvertDialog::GetDrawAspect.md)|指定是否要繪製項目顯示為圖示。|  
|[COleConvertDialog::GetIconicMetafile](../Topic/COleConvertDialog::GetIconicMetafile.md)|會處理這個中繼資料與此項目圖示表單。|  
|[COleConvertDialog::GetSelectionType](../Topic/COleConvertDialog::GetSelectionType.md)|取得選取範圍的型別被選取。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleConvertDialog::m\_cv](../Topic/COleConvertDialog::m_cv.md)|控制項對話方塊的行為的結構。|  
  
## 備註  
  
> [!NOTE]
>  應用程式精靈所產生的容器程式碼使用這個類別。  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)