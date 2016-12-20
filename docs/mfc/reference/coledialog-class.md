---
title: "COleDialog Class | Microsoft Docs"
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
  - "COleDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDialog class"
  - "對話方塊, OLE"
  - "OLE 對話方塊, 基底類別"
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 OLE 提供通用的功能加入至  對話方塊。  
  
## 語法  
  
```  
class COleDialog : public CCommonDialog  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDialog::GetLastError](../Topic/COleDialog::GetLastError.md)|取得錯誤碼傳回由對話方塊。|  
  
## 備註  
 MFC 程式庫提供從 `COleDialog`衍生的幾種類別:  
  
-   [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
-   [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
-   [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
-   [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
-   [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
-   [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
-   [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
-   [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
-   [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)