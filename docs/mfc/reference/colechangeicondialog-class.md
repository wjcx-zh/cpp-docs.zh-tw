---
title: "COleChangeIconDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleChangeIconDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Change Icon dialog box"
  - "COleChangeIconDialog class"
  - "對話方塊, OLE"
  - "OLE Change Icon dialog box"
  - "OLE 對話方塊, Change Icon"
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleChangeIconDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於 OLE 變更圖示對話方塊。  
  
## 語法  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleChangeIconDialog::COleChangeIconDialog](../Topic/COleChangeIconDialog::COleChangeIconDialog.md)|建構 `COleChangeIconDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleChangeIconDialog::DoChangeIcon](../Topic/COleChangeIconDialog::DoChangeIcon.md)|執行在  對話方塊中指定的變更。|  
|[COleChangeIconDialog::DoModal](../Topic/COleChangeIconDialog::DoModal.md)|顯示 OLE 2 變更圖示對話方塊。|  
|[COleChangeIconDialog::GetIconicMetafile](../Topic/COleChangeIconDialog::GetIconicMetafile.md)|會處理這個中繼資料與此項目圖示表單。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleChangeIconDialog::m\_ci](../Topic/COleChangeIconDialog::m_ci.md)|控制項對話方塊的行為的結構。|  
  
## 備註  
 要呼叫此對話方塊時，請建立類別 `COleChangeIconDialog` 物件。  在 `COleChangeIconDialog` 在建構物件之後，您可以使用 [m\_ci](../Topic/COleChangeIconDialog::m_ci.md) 結構初始化控制項的值或狀態在對話方塊中的。  `m_ci` 結構是型別 **OLEUICHANGEICON**。  如需使用這個對話方塊類別的詳細資訊，請參閱 [DoModal](../Topic/COleChangeIconDialog::DoModal.md) 成員函式。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) 結構。  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)