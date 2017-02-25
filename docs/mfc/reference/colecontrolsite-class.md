---
title: "COleControlSite Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleControlSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControlSite class"
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleControlSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為自訂用戶端控制項介面的支援。  
  
## 語法  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleControlSite::COleControlSite](../Topic/COleControlSite::COleControlSite.md)|建構 `COleControlSite` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleControlSite::BindDefaultProperty](../Topic/COleControlSite::BindDefaultProperty.md)|繫結至裝載之控制項的預設屬性設定為資料來源。|  
|[COleControlSite::BindProperty](../Topic/COleControlSite::BindProperty.md)|繫結至裝載之控制項的屬性設為資料來源。|  
|[COleControlSite::CreateControl](../Topic/COleControlSite::CreateControl.md)|建立裝載 ActiveX 控制項。|  
|[COleControlSite::DestroyControl](../Topic/COleControlSite::DestroyControl.md)|終結已裝載的控制項。|  
|[COleControlSite::DoVerb](../Topic/COleControlSite::DoVerb.md)|執行已裝載之控制項的特定的動詞命令。|  
|[COleControlSite::EnableDSC](../Topic/COleControlSite::EnableDSC.md)|啟用控制項網站的資料來源。|  
|[COleControlSite::EnableWindow](../Topic/COleControlSite::EnableWindow.md)|啟用控制項的網站。|  
|[COleControlSite::FreezeEvents](../Topic/COleControlSite::FreezeEvents.md)|指定控制項的網站是否接受事件。|  
|[COleControlSite::GetDefBtnCode](../Topic/COleControlSite::GetDefBtnCode.md)|會擷取所裝載控制項的預設按鈕的程式碼。|  
|[COleControlSite::GetDlgCtrlID](../Topic/COleControlSite::GetDlgCtrlID.md)|擷取控制項的識別項。|  
|[COleControlSite::GetEventIID](../Topic/COleControlSite::GetEventIID.md)|擷取一個事件介面的 ID 所裝載控制項的。|  
|[COleControlSite::GetExStyle](../Topic/COleControlSite::GetExStyle.md)|擷取控制項站台的延伸樣式。|  
|[COleControlSite::GetProperty](../Topic/COleControlSite::GetProperty.md)|會擷取所裝載控制項的特定屬性。|  
|[COleControlSite::GetStyle](../Topic/COleControlSite::GetStyle.md)|擷取控制項站台的樣式。|  
|[COleControlSite::GetWindowText](../Topic/COleControlSite::GetWindowText.md)|會擷取所裝載控制項的文字。|  
|[COleControlSite::InvokeHelper](../Topic/COleControlSite::InvokeHelper.md)|叫用裝載控制項的特定方法。|  
|[COleControlSite::InvokeHelperV](../Topic/COleControlSite::InvokeHelperV.md)|叫用裝載控制項的特定方法的引數清單變數清單中。|  
|[COleControlSite::IsDefaultButton](../Topic/COleControlSite::IsDefaultButton.md)|判斷控制項是否在視窗的預設按鈕。|  
|[COleControlSite::IsWindowEnabled](../Topic/COleControlSite::IsWindowEnabled.md)|檢查控制網站的可見狀態。|  
|[COleControlSite::ModifyStyle](../Topic/COleControlSite::ModifyStyle.md)|修改控制網站目前的延伸樣式。|  
|[COleControlSite::ModifyStyleEx](../Topic/COleControlSite::ModifyStyleEx.md)|修改控制網站的目前樣式。|  
|[COleControlSite::MoveWindow](../Topic/COleControlSite::MoveWindow.md)|變更控制網站的位置。|  
|[COleControlSite::QuickActivate](../Topic/COleControlSite::QuickActivate.md)|快速啟動裝載的控制項。|  
|[COleControlSite::SafeSetProperty](../Topic/COleControlSite::SafeSetProperty.md)|設定控制項的屬性或方法，而不會擲回例外狀況的機率。|  
|[COleControlSite::SetDefaultButton](../Topic/COleControlSite::SetDefaultButton.md)|在  視窗中設定的預設按鈕。|  
|[COleControlSite::SetDlgCtrlID](../Topic/COleControlSite::SetDlgCtrlID.md)|擷取控制項的識別項。|  
|[COleControlSite::SetFocus](../Topic/COleControlSite::SetFocus.md)|設定焦點的控制項加入至網站。|  
|[COleControlSite::SetProperty](../Topic/COleControlSite::SetProperty.md)|設定裝載之控制項的特定屬性。|  
|[COleControlSite::SetPropertyV](../Topic/COleControlSite::SetPropertyV.md)|設定裝載之控制項的特定屬性與引數清單變數清單中。|  
|[COleControlSite::SetWindowPos](../Topic/COleControlSite::SetWindowPos.md)|設定控制網站的位置。|  
|[COleControlSite::SetWindowText](../Topic/COleControlSite::SetWindowText.md)|設定裝載之控制項的文字。|  
|[COleControlSite::ShowWindow](../Topic/COleControlSite::ShowWindow.md)|顯示或隱藏控制項的網站。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleControlSite::GetControlInfo](../Topic/COleControlSite::GetControlInfo.md)|擷取鍵盤訊息和助憶鍵裝載的控制項。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleControlSite::m\_bIsWindowless](../Topic/COleControlSite::m_bIsWindowless.md)|判斷裝載的控制項是無視窗 \(Windowless\) 控制項。|  
|[COleControlSite::m\_ctlInfo](../Topic/COleControlSite::m_ctlInfo.md)|包含有關處理控制項的鍵盤的資訊。|  
|[COleControlSite::m\_dwEventSink](../Topic/COleControlSite::m_dwEventSink.md)|控制項的連接點的 Cookie。|  
|[COleControlSite::m\_dwMiscStatus](../Topic/COleControlSite::m_dwMiscStatus.md)|裝載控制項的其他狀態。|  
|[COleControlSite::m\_dwPropNotifySink](../Topic/COleControlSite::m_dwPropNotifySink.md)|控制項的 `IPropertyNotifySink` Cookie。|  
|[COleControlSite::m\_dwStyle](../Topic/COleControlSite::m_dwStyle.md)|裝載控制項的樣式。|  
|[COleControlSite::m\_hWnd](../Topic/COleControlSite::m_hWnd.md)|控制網站的控制代碼。|  
|[COleControlSite::m\_iidEvents](../Topic/COleControlSite::m_iidEvents.md)|事件介面的 ID 所裝載控制項的。|  
|[COleControlSite::m\_nID](../Topic/COleControlSite::m_nID.md)|裝載的控制項 ID。|  
|[COleControlSite::m\_pActiveObject](../Topic/COleControlSite::m_pActiveObject.md)|已裝載之控制項的 `IOleInPlaceActiveObject` 物件的指標。|  
|[COleControlSite::m\_pCtrlCont](../Topic/COleControlSite::m_pCtrlCont.md)|裝載控制項的容器。|  
|[COleControlSite::m\_pInPlaceObject](../Topic/COleControlSite::m_pInPlaceObject.md)|已裝載之控制項的 `IOleInPlaceObject` 物件的指標。|  
|[COleControlSite::m\_pObject](../Topic/COleControlSite::m_pObject.md)|為控制項的 `IOleObjectInterface` 介面的指標。|  
|[COleControlSite::m\_pWindowlessObject](../Topic/COleControlSite::m_pWindowlessObject.md)|為控制項的 `IOleInPlaceObjectWindowless` 介面的指標。|  
|[COleControlSite::m\_pWndCtrl](../Topic/COleControlSite::m_pWndCtrl.md)|在  視窗的物件指標所裝載控制項的。|  
|[COleControlSite::m\_rect](../Topic/COleControlSite::m_rect.md)|控制網站的維度。|  
  
## 備註  
 這項支援是內嵌的 ActiveX 控制項取得有關其顯示網站的位置和範圍的相關資訊，它的 Moniker、使用者介面、其環境屬性和其容器所提供的其他資源的主要方式。  `COleControlSite` 完整實作， [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502)[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706)， [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)， **IBoundObjectSite**， **INotifyDBEvents**， [IRowSetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) 介面。  此外， IDispatch 介面 \(提供了支援環境屬性和事件接收器\) 也會實作。  
  
 使用 `COleControlSite`，若要建立 ActiveX 控制項站台，從 `COleControlSite`衍生一個類別。  在您的 `CWnd`\-容器 \(例如，您的對話方塊\) 覆寫的衍生類別 **CWnd::CreateControlSite** 函式。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## 需求  
 **Header:** afxocc.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControlContainer Class](../../mfc/reference/colecontrolcontainer-class.md)