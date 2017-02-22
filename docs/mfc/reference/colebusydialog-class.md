---
title: "COleBusyDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleBusyDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleBusyDialog class"
  - "Server Busy dialog box"
  - "Server Not Responding dialog box"
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleBusyDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於 OLE 伺服器沒有回應或伺服器忙碌對話方塊。  
  
## 語法  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleBusyDialog::COleBusyDialog](../Topic/COleBusyDialog::COleBusyDialog.md)|建構 `COleBusyDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleBusyDialog::DoModal](../Topic/COleBusyDialog::DoModal.md)|顯示 OLE 伺服器忙碌對話方塊。|  
|[COleBusyDialog::GetSelectionType](../Topic/COleBusyDialog::GetSelectionType.md)|判斷在對話方塊中進行的選項。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleBusyDialog::m\_bz](../Topic/COleBusyDialog::m_bz.md)|控制項對話方塊的行為類型 **OLEUIBUSY** 的結構。|  
  
## 備註  
 例如，當您想要呼叫這些對話方塊時，請建立類別 `COleBusyDialog` 物件。  在 `COleBusyDialog` 在建構物件之後，您可以使用 [m\_bz](../Topic/COleBusyDialog::m_bz.md) 結構初始化控制項的值或狀態在對話方塊中的。  `m_bz` 結構是型別 **OLEUIBUSY**。  如需使用這個對話方塊類別的詳細資訊，請參閱 [DoModal](../Topic/COleBusyDialog::DoModal.md) 成員函式。  
  
> [!NOTE]
>  應用程式精靈所產生的容器程式碼使用這個類別。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) 結構。  
  
 如需 OLE 應用程式特定對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)