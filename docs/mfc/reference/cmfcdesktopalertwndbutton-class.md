---
title: "CMFCDesktopAlertWndButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDesktopAlertWndButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWndButton class"
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMFCDesktopAlertWndButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允許按鈕加入至桌面警示對話方塊。  
  
## 語法  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|預設建構函式。|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](../Topic/CMFCDesktopAlertWndButton::IsCaptionButton.md)|判斷  按鈕是否在警示對話方塊的頁首區域的顯示。|  
|[CMFCDesktopAlertWndButton::IsCloseButton](../Topic/CMFCDesktopAlertWndButton::IsCloseButton.md)|判斷  按鈕是否關閉警示對話方塊。|  
  
### 資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|將指定的布林值按鈕是否在警示對話方塊的頁首區域的顯示。|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|將指定的布林值按鈕是否關閉警示對話方塊。|  
  
### 備註  
 根據預設，建構函式會設定 `m_bIsCaptionButton` 和 `m_bIsCloseButton` 資料成員至 `FALSE`。  如果按鈕在警示對話方塊的標題區域，會放置 `CMFCDesktopAlertDialog` 父物件設定為 `m_bIsCaptionButton``TRUE` 。  `CMFCDesktopAlertDialog` 類別會建立做為按鈕來關閉警示對話方塊並設定 `m_bIsCloseButton` 至 `TRUE`的 `CMFCDesktopAlertWndButton` 物件。  
  
 因為您將所有按鈕，將 `CMFCDesktopAlertDialog` 物件的 `CMFCDesktopAlertWndButton` 物件。  如需 `CMFCDesktopAlertDialog` 的詳細資訊，請參閱 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## 範例  
 下列範例會在 `CMFCDesktopAlertWndButton` 類別會示範如何使用 `SetImage` 方法。  這個程式碼片段是 [桌面警示示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## 需求  
 **標題:** afxdesktopalertwnd.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)