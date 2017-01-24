---
title: "COleChangeSourceDialog Class | Microsoft Docs"
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
  - "COleChangeSourceDialog"
  - "OLEUICHANGESOURCE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleChangeSourceDialog class"
  - "對話方塊, OLE"
  - "OLE Change Source dialog box"
  - "OLE 對話方塊, Change Source"
  - "OleUIChangeSource structure"
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleChangeSourceDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於 OLE 變更來源對話方塊。  
  
## 語法  
  
```  
class COleChangeSourceDialog : public COleDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleChangeSourceDialog::COleChangeSourceDialog](../Topic/COleChangeSourceDialog::COleChangeSourceDialog.md)|建構 `COleChangeSourceDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleChangeSourceDialog::DoModal](../Topic/COleChangeSourceDialog::DoModal.md)|顯示 OLE 變更來源對話方塊。|  
|[COleChangeSourceDialog::GetDisplayName](../Topic/COleChangeSourceDialog::GetDisplayName.md)|取得完整的來源顯示名稱。|  
|[COleChangeSourceDialog::GetFileName](../Topic/COleChangeSourceDialog::GetFileName.md)|從來源名稱取得該檔案的名稱。|  
|[COleChangeSourceDialog::GetFromPrefix](../Topic/COleChangeSourceDialog::GetFromPrefix.md)|取得上一個來源的前置詞。|  
|[COleChangeSourceDialog::GetItemName](../Topic/COleChangeSourceDialog::GetItemName.md)|從來源名稱取得項目名稱。|  
|[COleChangeSourceDialog::GetToPrefix](../Topic/COleChangeSourceDialog::GetToPrefix.md)|取得新來源的前置字元。|  
|[COleChangeSourceDialog::IsValidSource](../Topic/COleChangeSourceDialog::IsValidSource.md)|表示來源是否有效。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleChangeSourceDialog::m\_cs](../Topic/COleChangeSourceDialog::m_cs.md)|控制項對話方塊的行為的結構。|  
  
## 備註  
 要呼叫此對話方塊時，請建立類別 `COleChangeSourceDialog` 物件。  在 `COleChangeSourceDialog` 在建構物件之後，您可以使用 [m\_cs](../Topic/COleChangeSourceDialog::m_cs.md) 結構初始化控制項的值或狀態在對話方塊中的。  `m_cs` 結構是型別 [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)。  如需使用這個對話方塊類別的詳細資訊，請參閱 [DoModal](../Topic/COleChangeSourceDialog::DoModal.md) 成員函式。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) 結構。  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeSourceDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)