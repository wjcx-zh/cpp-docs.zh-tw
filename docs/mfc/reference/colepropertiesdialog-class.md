---
title: "COlePropertiesDialog Class | Microsoft Docs"
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
  - "COlePropertiesDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePropertiesDialog class"
  - "對話方塊, OLE"
  - "Object Properties dialog box"
  - "OLE 文件, 修改屬性"
  - "OLE Object Properties dialog box"
  - "屬性頁, OLE"
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COlePropertiesDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 通用 OLE 物件屬性對話方塊。  
  
## 語法  
  
```  
  
class COlePropertiesDialog : public COleDialog  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COlePropertiesDialog::COlePropertiesDialog](../Topic/COlePropertiesDialog::COlePropertiesDialog.md)|建構 `COlePropertiesDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COlePropertiesDialog::DoModal](../Topic/COlePropertiesDialog::DoModal.md)|顯示  對話方塊可讓使用者進行選取。|  
|[COlePropertiesDialog::OnApplyScale](../Topic/COlePropertiesDialog::OnApplyScale.md)|呼叫由架構，在文件項目的縮放比例變更。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COlePropertiesDialog::m\_gp](../Topic/COlePropertiesDialog::m_gp.md)|用來初始化結構 `COlePropertiesDialog` 物件的「一般」網頁。|  
|[COlePropertiesDialog::m\_lp](../Topic/COlePropertiesDialog::m_lp.md)|用來初始化結構 `COlePropertiesDialog` 物件的「連結」網頁。|  
|[COlePropertiesDialog::m\_op](../Topic/COlePropertiesDialog::m_op.md)|用來初始化結構 `COlePropertiesDialog` 物件。|  
|[COlePropertiesDialog::m\_psh](../Topic/COlePropertiesDialog::m_psh.md)|用於將結構加入額外的自訂屬性頁。|  
|[COlePropertiesDialog::m\_vp](../Topic/COlePropertiesDialog::m_vp.md)|用於的結構自訂 `COlePropertiesDialog` 物件「檢視」網頁。|  
  
## 備註  
 通用 OLE 物件屬性對話方塊可讓您輕鬆顯示和修改的 OLE 文件項目的某些屬性符合 Windows 標準。  \(如果項目連結\)，這些屬性，包括、等等，關於文件項目所表示的檔案之顯示圖示和影像調整的資訊，如需項目的連結的選項和資訊。  
  
 使用 `COlePropertiesDialog` 建構函式，才能使用 `COlePropertiesDialog` 物件，請先建立物件。  在  對話方塊中建構之後，呼叫 `DoModal` 成員函式來顯示對話方塊並允許使用者修改項目的所有屬性。  `DoModal` 傳回使用者是否選取了決定 \(**IDOK**\) 或取消**IDCANCEL**\(\) 按鈕。  除了確定和取消按鈕之外，還會套用  按鈕。  當使用者選取時套用，來變更文件項目的屬性 \(Attribute\) 會套用至項目，並在它的影像時自動更新，，但仍在作用中。  
  
 [m\_psh](../Topic/COlePropertiesDialog::m_psh.md) 資料成員是指向 **PROPSHEETHEADER** 結構，因此，在大部分情況下都不需要明確地加以存取。  唯一例外是您需要在預設一般、檢視和連結網頁以外的其他屬性頁。  在這種情況下，您可以修改 `m_psh` 資料成員在 `DoModal` 呼叫成員函式之前包含自訂的選項頁。  
  
 如需 OLE 對話方塊的詳細資訊，請參閱本文 [在 OLE 的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## 需求  
 **Header:** afxodlgs.h  
  
## 請參閱  
 [MFC CIRC 範例](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage Class](../../mfc/reference/cpropertypage-class.md)