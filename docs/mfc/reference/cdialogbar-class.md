---
title: "CDialogBar Class | Microsoft Docs"
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
  - "CDialogBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogBar class"
  - "dialog bars, Windows modeless dialog box"
  - "對話方塊, 非強制回應"
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialogBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在其中一個控制項中列的視窗非強制回應對話方塊功能。  
  
## 語法  
  
```  
class CDialogBar : public CControlBar  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDialogBar::CDialogBar](../Topic/CDialogBar::CDialogBar.md)|建構 `CDialogBar` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDialogBar::Create](../Topic/CDialogBar::Create.md)|建立視窗對話方塊列並將其附加至 `CDialogBar` 物件。|  
  
## 備註  
 一個對話方塊列類似對話方塊因為它包含使用者可定位之間的標準 Windows 控制項。  其他相似點是您建立對話方塊樣板表示對話方塊列。  
  
 建立和使用對話方塊列類似於建立和使用 `CFormView` 物件。  首先，使用 [對話方塊編輯器](../../mfc/dialog-editor.md) 定義具有樣式 **WS\_CHILD** 並沒有其他樣式建立對話方塊樣板。  樣板不能有樣式 **WS\_VISIBLE**。  在應用程式程式碼，請呼叫建構函式 `CDialogBar` 建構物件，然後呼叫 **建立** 建立對話方塊列視窗並附加至 `CDialogBar` 物件。  
  
 如需 `CDialogBar`的詳細資訊，請參閱本文 [對話方塊列](../../mfc/dialog-bars.md) 和 [Technical Note 31](../../mfc/tn031-control-bars.md)，控制列。  
  
> [!NOTE]
>  在目前版本中， `CDialogBar` 物件無法裝載 Windows Form 控制項。  如需在 Visual C\+\+ 中的 Windows Form 控制項的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 CTRLBARS](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)