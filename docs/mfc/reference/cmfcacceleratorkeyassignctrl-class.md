---
title: "CMFCAcceleratorKeyAssignCtrl Class | Microsoft Docs"
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
  - "CMFCAcceleratorKeyAssignCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAcceleratorKeyAssignCtrl class"
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCAcceleratorKeyAssignCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCAcceleratorKeyAssignCtrl` 類別會擴充 [CEdit Class](../../mfc/reference/cedit-class.md)，以支援額外的系統按鈕，例如 ALT、CONTROL 和 SHIFT。  
  
## 語法  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](../Topic/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl.md)|建構 `CMFCAcceleratorKeyAssignCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](../Topic/CMFCAcceleratorKeyAssignCtrl::GetAccel.md)|針對在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下的快速鍵，擷取 `ACCEL` 結構。|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](../Topic/CMFCAcceleratorKeyAssignCtrl::IsFocused.md)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](../Topic/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined.md)|判斷是否已定義快速鍵。|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](../Topic/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage.md)|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前的視窗訊息。  \(覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。\)|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](../Topic/CMFCAcceleratorKeyAssignCtrl::ResetKey.md)|重設快速鍵。|  
  
## 備註  
 此類別可藉由支援快速鍵來擴充 `CEdit` 類別的功能。   `CMFCAcceleratorKeyAssignCtrl` 類別可當作 [CEdit Class](../../mfc/reference/cedit-class.md)，而且也可以辨認系統按鈕。  
  
 這個類別會將實體快速鍵組合對應至字串值。  例如，假設按鍵組合 ALT \+ B 會對應至字串 "Alt \+ B"。  當使用者在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下此按鍵組合時，會對使用者顯示 "Alt \+ B"。  如需快捷鍵和字串格式之間對應的詳細資訊，請參閱 [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md)。  
  
## 範例  
 下列範例示範如何建構 `CMFCAcceleratorKeyAssignCtrl` 物件，並使用其 `ResetKey` 方法來重設快速鍵。  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/CPP/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)  
  
## 需求  
 **標頭：**afxacceleratorkeyassignctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md)