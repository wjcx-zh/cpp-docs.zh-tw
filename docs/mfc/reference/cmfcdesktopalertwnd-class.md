---
title: "CMFCDesktopAlertWnd Class | Microsoft Docs"
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
  - "CMFCDesktopAlertWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWnd class"
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDesktopAlertWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCDesktopAlertWnd` 類別實作在螢幕上顯示告知使用者事件的非強制回應對話方塊功能。  
  
## 語法  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md)|建立和初始化桌面警示視窗。|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::GetAnimationSpeed.md)|傳回動畫的速度。|  
|[CMFCDesktopAlertWnd::GetAnimationType](../Topic/CMFCDesktopAlertWnd::GetAnimationType.md)|傳回動畫型別。|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](../Topic/CMFCDesktopAlertWnd::GetAutoCloseTime.md)|傳回自動關閉時間。|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](../Topic/CMFCDesktopAlertWnd::GetCaptionHeight.md)|傳回標題的高度。|  
|[CMFCDesktopAlertWnd::GetDialogSize](../Topic/CMFCDesktopAlertWnd::GetDialogSize.md)||  
|[CMFCDesktopAlertWnd::GetLastPos](../Topic/CMFCDesktopAlertWnd::GetLastPos.md)|傳回 Desktop Alert Window 的最後一個有效的位置在螢幕上。|  
|[CMFCDesktopAlertWnd::GetTransparency](../Topic/CMFCDesktopAlertWnd::GetTransparency.md)|傳回透明度層級。|  
|[CMFCDesktopAlertWnd::HasSmallCaption](../Topic/CMFCDesktopAlertWnd::HasSmallCaption.md)|判斷桌面警示視窗是否顯示帶有小標頭。|  
|[CMFCDesktopAlertWnd::OnBeforeShow](../Topic/CMFCDesktopAlertWnd::OnBeforeShow.md)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](../Topic/CMFCDesktopAlertWnd::OnClickLinkButton.md)|呼叫框架，當使用者按一下  尋找桌面警示功能表的連結按鈕。|  
|[CMFCDesktopAlertWnd::OnCommand](../Topic/CMFCDesktopAlertWnd::OnCommand.md)|架構會呼叫此成員函式，當使用者選取項目時，從  功能表，子控制項時傳送通知訊息時，或當，快速鍵按鍵會轉譯時。  \(覆寫 [CWnd::OnCommand](../Topic/CWnd::OnCommand.md)\)。|  
|[CMFCDesktopAlertWnd::OnDraw](../Topic/CMFCDesktopAlertWnd::OnDraw.md)||  
|[CMFCDesktopAlertWnd::ProcessCommand](../Topic/CMFCDesktopAlertWnd::ProcessCommand.md)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::SetAnimationSpeed.md)|設定新的動畫速度。|  
|[CMFCDesktopAlertWnd::SetAnimationType](../Topic/CMFCDesktopAlertWnd::SetAnimationType.md)|設定動畫型別。|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](../Topic/CMFCDesktopAlertWnd::SetAutoCloseTime.md)|設定自動關閉時間。|  
|[CMFCDesktopAlertWnd::SetSmallCaption](../Topic/CMFCDesktopAlertWnd::SetSmallCaption.md)|在小型標題和一般之間切換。|  
|[CMFCDesktopAlertWnd::SetTransparency](../Topic/CMFCDesktopAlertWnd::SetTransparency.md)|設定透明度層級。|  
  
## 備註  
 桌面警示視窗可以是透明的，它可以顯示與動畫效果，因此，它可以消失 \(在指定的延遲之後，或當使用者按一下 \[關閉\] 按鈕關閉時\)。  
  
 Desktop Alert Window 也可以包含依序包含圖示、文字的預設對話方塊 \(標籤\) 和一個連結。  或者，桌面警示視窗可以包含應用程式資源的自訂對話方塊。  
  
 您使用兩個步驟來建立桌面警示視窗。  首先，請呼叫建構函式 `CMFCDesktopAlertWnd` 建構物件。  接著，請呼叫 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) 成員函式建立視窗並附加至 `CMFCDesktopAlertWnd` 物件。  
  
 `CMFCDesktopAlertWnd` 物件建立填入桌面警示視窗工作區的特殊子對話方塊。  對話方塊擁有在此表單的所有控制項。  
  
 若要顯示快顯視窗中顯示自訂對話方塊，請執行下列步驟:  
  
1.  從 `CMFCDesktopAlertDialog` 衍生類別。  
  
2.  建立子對話方塊樣板資源中。  
  
3.  呼叫 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) 使用對話方塊範本和指標的資源 ID 為衍生類別的執行階段類別資訊。  
  
4.  程式設計自訂對話方塊處理來自裝載控制項的所有通知或程式設計裝載的控制項直接處理這些告知。  
  
 使用下列函式控制桌面警示視窗的行為:  
  
-   藉由呼叫 [CMFCDesktopAlertWnd::SetAnimationType](../Topic/CMFCDesktopAlertWnd::SetAnimationType.md)設定動畫型別。  有效選項包括、、、，滑動，並淡出。  
  
-   藉由呼叫 [CMFCDesktopAlertWnd::SetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::SetAnimationSpeed.md)設定動畫的速度。  
  
-   藉由呼叫 [CMFCDesktopAlertWnd::SetTransparency](../Topic/CMFCDesktopAlertWnd::SetTransparency.md)設定透明度層級。  
  
-   變更標題的大小為小型藉由呼叫 [CMFCDesktopAlertWnd::SetSmallCaption](../Topic/CMFCDesktopAlertWnd::SetSmallCaption.md)。  子標題是高度為 7 像素。  
  
## 範例  
 下列範例會在 `CMFCDesktopAlertWnd` 類別說明了如何使用不同的方法設定 `CMFCDesktopAlertWnd` 物件。  這個範例顯示如何將動畫型別，設定快顯視窗的透明度，指定警示視窗顯示小型標題，然後設定警示視窗之前所經過的自動結束的時間。  範例也會示範如何建立和初始化桌面警示視窗。  這個程式碼片段是 [桌面警示示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwnd-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## 需求  
 **標題:** afxDesktopAlertWnd.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo Class](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)