---
title: "COleLinksDialog Class | Microsoft Docs"
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
  - "COleLinksDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleLinksDialog class"
  - "對話方塊, OLE"
  - "Edit Links dialog box"
  - "OLE Edit Links dialog box"
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleLinksDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於 OLE 編輯連接對話方塊。  
  
## 語法  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleLinksDialog::COleLinksDialog](../Topic/COleLinksDialog::COleLinksDialog.md)|建構 `COleLinksDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleLinksDialog::DoModal](../Topic/COleLinksDialog::DoModal.md)|顯示 OLE 編輯連結對話方塊。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleLinksDialog::m\_el](../Topic/COleLinksDialog::m_el.md)|控制項對話方塊的行為類型 **OLEUIEDITLINKS** 的結構。|  
  
## 備註  
 要呼叫此對話方塊時，請建立類別 `COleLinksDialog` 物件。  在 `COleLinksDialog` 在建構物件之後，您可以使用 [m\_el](../Topic/COleLinksDialog::m_el.md) 結構初始化控制項的值或狀態在對話方塊中的。  `m_el` 結構是型別 **OLEUIEDITLINKS**。  如需使用這個對話方塊類別的詳細資訊，請參閱 [DoModal](../Topic/COleLinksDialog::DoModal.md) 成員函式。  
  
> [!NOTE]
>  應用程式精靈所產生的容器程式碼使用這個類別。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) 結構。  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)