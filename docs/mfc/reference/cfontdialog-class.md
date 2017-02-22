---
title: "CFontDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFontDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFontDialog class"
  - "對話方塊, 字型"
  - "字型"
  - "字型, 選取"
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CFontDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可讓您結合字型選取對話方塊加入至您的應用程式。  
  
## 語法  
  
```  
class CFontDialog : public CCommonDialog  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFontDialog::CFontDialog](../Topic/CFontDialog::CFontDialog.md)|建構 `CFontDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFontDialog::DoModal](../Topic/CFontDialog::DoModal.md)|顯示對話方塊並允許使用者進行選取。|  
|[CFontDialog::GetCharFormat](../Topic/CFontDialog::GetCharFormat.md)|擷取選取字型的字元格式。|  
|[CFontDialog::GetColor](../Topic/CFontDialog::GetColor.md)|傳回選取的字型色彩。|  
|[CFontDialog::GetCurrentFont](../Topic/CFontDialog::GetCurrentFont.md)|將目前選取的字型的特性。 `LOGFONT` 結構。|  
|[CFontDialog::GetFaceName](../Topic/CFontDialog::GetFaceName.md)|傳回已選取字型的字樣名稱。|  
|[CFontDialog::GetSize](../Topic/CFontDialog::GetSize.md)|傳回選取字型的點數。|  
|[CFontDialog::GetStyleName](../Topic/CFontDialog::GetStyleName.md)|傳回已選取字型的樣式名稱。|  
|[CFontDialog::GetWeight](../Topic/CFontDialog::GetWeight.md)|傳回選取的字型粗細。|  
|[CFontDialog::IsBold](../Topic/CFontDialog::IsBold.md)|判斷字型是否為粗體。|  
|[CFontDialog::IsItalic](../Topic/CFontDialog::IsItalic.md)|判斷字型是否為斜體。|  
|[CFontDialog::IsStrikeOut](../Topic/CFontDialog::IsStrikeOut.md)|判斷字型是否顯示連結、底線。|  
|[CFontDialog::IsUnderline](../Topic/CFontDialog::IsUnderline.md)|判斷字型是否為加底線。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFontDialog::m\_cf](../Topic/CFontDialog::m_cf.md)|用於的結構 `CFontDialog` 自訂物件。|  
  
## 備註  
 `CFontDialog` 物件是在系統目前安裝的字型清單的對話方塊。  使用者可以選取特定字型，從清單中，而且這個選項就會回報給應用程式。  
  
 `CFontDialog` 建構物件，使用提供的建構函式或從衍生新的子類別並使用自訂建構函式。  
  
 一旦 `CFontDialog` 物件建構時，您可以使用 `m_cf` 結構初始化控制項的值或狀態在對話方塊中的。  [m\_cf](../Topic/CFontDialog::m_cf.md) 結構是型別 [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832)。  如需此結構的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 在初始化對話方塊物件的控制項後，請呼叫 `DoModal` 成員函式來顯示對話方塊並可讓使用者選取字型。  `DoModal` 傳回使用者是否選取了決定 \(**IDOK**\) 或取消**IDCANCEL**\(\) 按鈕。  
  
 如果 `DoModal` 傳回 **IDOK**，您可以使用其中一個 `CFontDialog` 的成員函式是由使用者輸入來擷取資訊。  
  
 您可以使用  視窗 [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) 函式以判斷是否在  對話方塊中的初始化時發生錯誤以及了解錯誤。  如需這個函式的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `CFontDialog` 仰賴隨附於 Windows 3.1 \(含\) 以後版本的 COMMDLG.DLL 檔案。  
  
 若要自訂對話方塊，請從 `CFontDialog`衍生一個類別，提供自訂對話方塊範本，並將訊息對應 \(Message Map 處理擴充的控制項傳回的通知訊息。  應將所有未處理訊息加入至基底類別。  
  
 攔截函式不需要自訂。  
  
 如需使用 `CFontDialog`的資訊，請參閱 [通用對話方塊類別。](../../mfc/common-dialog-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFontDialog`  
  
## 需求  
 **Header:** afxdlgs.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)