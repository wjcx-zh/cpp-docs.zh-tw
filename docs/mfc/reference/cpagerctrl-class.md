---
title: "CPagerCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPagerCtrl class"
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPagerCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPagerCtrl` 類別包裝 Windows 頁面巡覽區控制項，可以捲動到檢視所包含的視窗不符合所包含的視窗。  
  
## 語法  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPagerCtrl::CPagerCtrl](../Topic/CPagerCtrl::CPagerCtrl.md)|建構 `CPagerCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPagerCtrl::Create](../Topic/CPagerCtrl::Create.md)|建立具有指定樣式的頁面巡覽區控制項並將其附加至目前 `CPagerCtrl` 物件。|  
|[CPagerCtrl::CreateEx](../Topic/CPagerCtrl::CreateEx.md)|建立具有指定的延伸樣式的頁面巡覽區控制項並將其附加至目前 `CPagerCtrl` 物件。|  
|[CPagerCtrl::ForwardMouse](../Topic/CPagerCtrl::ForwardMouse.md)|啟用或停用轉送 [WM\_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) 訊息至目前頁面巡覽區控制項所包含的視窗。|  
|[CPagerCtrl::GetBkColor](../Topic/CPagerCtrl::GetBkColor.md)|擷取目前頁面巡覽區控制項的背景色彩。|  
|[CPagerCtrl::GetBorder](../Topic/CPagerCtrl::GetBorder.md)|擷取目前頁面巡覽區控制項的框線大小。|  
|[CPagerCtrl::GetButtonSize](../Topic/CPagerCtrl::GetButtonSize.md)|擷取目前頁面巡覽區控制項的按鈕大小。|  
|[CPagerCtrl::GetButtonState](../Topic/CPagerCtrl::GetButtonState.md)|擷取指定之按鈕的狀態在目前頁面巡覽區控制項的。|  
|[CPagerCtrl::GetDropTarget](../Topic/CPagerCtrl::GetDropTarget.md)|擷取目前頁面巡覽區控制項的 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) 介面。|  
|[CPagerCtrl::GetScrollPos](../Topic/CPagerCtrl::GetScrollPos.md)|擷取目前頁面巡覽區控制項的捲動位置。|  
|[CPagerCtrl::IsButtonDepressed](../Topic/CPagerCtrl::IsButtonDepressed.md)|表示目前頁面巡覽區控制項的指定按鈕是否在 `pressed` 狀態。|  
|[CPagerCtrl::IsButtonGrayed](../Topic/CPagerCtrl::IsButtonGrayed.md)|表示目前頁面巡覽區控制項的指定按鈕是否在 `grayed` 狀態。|  
|[CPagerCtrl::IsButtonHot](../Topic/CPagerCtrl::IsButtonHot.md)|表示目前頁面巡覽區控制項的指定按鈕是否在 `hot` 狀態。|  
|[CPagerCtrl::IsButtonInvisible](../Topic/CPagerCtrl::IsButtonInvisible.md)|表示目前頁面巡覽區控制項的指定按鈕是否在 `invisible` 狀態。|  
|[CPagerCtrl::IsButtonNormal](../Topic/CPagerCtrl::IsButtonNormal.md)|表示目前頁面巡覽區控制項的指定按鈕是否在 `normal` 狀態。|  
|[CPagerCtrl::RecalcSize](../Topic/CPagerCtrl::RecalcSize.md)|導致目前的頁面巡覽區控制項重新計算所包含之視窗的大小。|  
|[CPagerCtrl::SetBkColor](../Topic/CPagerCtrl::SetBkColor.md)|設定目前頁面巡覽區控制項的背景色彩。|  
|[CPagerCtrl::SetBorder](../Topic/CPagerCtrl::SetBorder.md)|設定目前頁面巡覽區控制項的框線大小。|  
|[CPagerCtrl::SetButtonSize](../Topic/CPagerCtrl::SetButtonSize.md)|設定目前頁面巡覽區控制項的按鈕大小。|  
|[CPagerCtrl::SetChild](../Topic/CPagerCtrl::SetChild.md)|設定目前頁面巡覽區控制項所包含的視窗。|  
|[CPagerCtrl::SetScrollPos](../Topic/CPagerCtrl::SetScrollPos.md)|設定目前頁面巡覽區控制項的捲動位置。|  
  
## 備註  
 頁面巡覽區控制項是包含另一個視窗大於包含視窗線性和，並且讓您移動所包含的視窗中檢視的視窗。  頁面巡覽區控制項顯示自動消失的兩個捲軸按鈕，當包含的視窗移至其上最遠的範圍內時，則會再次出現。  您可以建立水平或垂直捲動的頁面巡覽區控制項。  
  
 例如，在中，如果您的應用程式具有寬度不足以顯示它的所有項目的工具列，您可以將工具列加入至頁面巡覽區控制項，而且使用者可以捲動工具列左側或右側存取任何項目。  Microsoft Internet Explorer 會在 Microsoft Internet Explorer 4.0 版 \(4.71 版\) commctrl.dll 引入頁面巡覽區控制項。  
  
 `CPagerCtrl` 類別 [CWnd](../../mfc/reference/cwnd-class.md) 從類別衍生。  如需詳細資訊和頁面巡覽區控制項的說明，請參閱 [頁面巡覽區控制項](http://msdn.microsoft.com/library/windows/desktop/bb760855)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## 需求  
 **標題:** afxcmn.h  
  
## 請參閱  
 [CPagerCtrl Class](../../mfc/reference/cpagerctrl-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [頁面巡覽區控制項](http://msdn.microsoft.com/library/windows/desktop/bb760855)