---
title: "CComControlBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComControlBase"
  - "ATL.CComControlBase"
  - "ATL::CComControlBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComControlBase class"
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComControlBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會建立和管理 ATL 控制項的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class ATL_NO_VTABLE CComControlBase  
  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CComControlBase::AppearanceType](../Topic/CComControlBase::AppearanceType.md)|覆寫，如果您的 `m_nAppearance` 共用屬性的型別不是 `short`。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComControlBase::CComControlBase](../Topic/CComControlBase::CComControlBase.md)|建構函式。|  
|[CComControlBase::~CComControlBase](../Topic/CComControlBase::~CComControlBase.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComControlBase::ControlQueryInterface](../Topic/CComControlBase::ControlQueryInterface.md)|擷取指標所要求的介面。|  
|[CComControlBase::DoesVerbActivate](../Topic/CComControlBase::DoesVerbActivate.md)|檢查或來啟動控制項之使用者介面的 `iVerb` 參數所使用的 `IOleObjectImpl::DoVerb` \(`iVerb` 等於 `OLEIVERB_UIACTIVATE`\)，定義所採取的動作，當使用者按兩下控制項 \(`iVerb` 等於 `OLEIVERB_PRIMARY`\)，顯示控制項 \(`iVerb` 等於 `OLEIVERB_SHOW`\)，或啟動控制項 \(`iVerb` 等於 **OLEIVERB\_INPLACEACTIVATE**\)。|  
|[CComControlBase::DoesVerbUIActivate](../Topic/CComControlBase::DoesVerbUIActivate.md)|檢查 `IOleObjectImpl::DoVerb` 使用的 `iVerb` 由動態控制項的使用者介面 \(UI\) 啟動並傳回 **是**。|  
|[CComControlBase::DoVerbProperties](../Topic/CComControlBase::DoVerbProperties.md)|顯示控制項的屬性頁。|  
|[CComControlBase::FireViewChange](../Topic/CComControlBase::FireViewChange.md)|呼叫這個方法會告知容器重繪控制項或通知已登錄的通知接收控制項檢視已變更。|  
|[CComControlBase::GetAmbientAppearance](../Topic/CComControlBase::GetAmbientAppearance.md)|擷取 **DISPID\_AMBIENT\_APPEARANCE**，控制項目前的外觀設定:一般的 0 和 1 的 3D。|  
|[CComControlBase::GetAmbientAutoClip](../Topic/CComControlBase::GetAmbientAutoClip.md)|擷取 **DISPID\_AMBIENT\_AUTOCLIP**，指出容器是否旗標支援控制項顯示區域的自動裁剪。|  
|[CComControlBase::GetAmbientBackColor](../Topic/CComControlBase::GetAmbientBackColor.md)|擷取 **DISPID\_AMBIENT\_BACKCOLOR**，所有控制項的環境背景色彩，定義由容器。|  
|[CComControlBase::GetAmbientCharSet](../Topic/CComControlBase::GetAmbientCharSet.md)|擷取 **DISPID\_AMBIENT\_CHARSET**，所有控制項的環境字元集，定義由容器。|  
|[CComControlBase::GetAmbientCodePage](../Topic/CComControlBase::GetAmbientCodePage.md)|擷取 **DISPID\_AMBIENT\_CODEPAGE**，所有控制項的環境字元集，定義由容器。|  
|[CComControlBase::GetAmbientDisplayAsDefault](../Topic/CComControlBase::GetAmbientDisplayAsDefault.md)|擷取 **DISPID\_AMBIENT\_DISPLAYASDEFAULT**，是 **是** 的旗標，如果容器中網站指示控制項為預設按鈕，以及按鈕控制項應該繪製其本身具有較粗的框架。|  
|[CComControlBase::GetAmbientDisplayName](../Topic/CComControlBase::GetAmbientDisplayName.md)|擷取 **DISPID\_AMBIENT\_DISPLAYNAME**容器，提供給控制項的名稱。|  
|[CComControlBase::GetAmbientFont](../Topic/CComControlBase::GetAmbientFont.md)|擷取指標容器的環境 `IFont` 介面。|  
|[CComControlBase::GetAmbientFontDisp](../Topic/CComControlBase::GetAmbientFontDisp.md)|擷取指標容器的環境 **IFontDisp** 分派介面。|  
|[CComControlBase::GetAmbientForeColor](../Topic/CComControlBase::GetAmbientForeColor.md)|擷取 **DISPID\_AMBIENT\_FORECOLOR**，所有控制項的前景色彩，定義由容器。|  
|[CComControlBase::GetAmbientLocaleID](../Topic/CComControlBase::GetAmbientLocaleID.md)|擷取 **DISPID\_AMBIENT\_LOCALEID**，容器所使用之語言的識別項。|  
|[CComControlBase::GetAmbientMessageReflect](../Topic/CComControlBase::GetAmbientMessageReflect.md)|擷取 **DISPID\_AMBIENT\_MESSAGEREFLECT**，指出容器是否旗標要接收 Windows 訊息 \(例如 `WM_DRAWITEM`\) 做為事件。|  
|[CComControlBase::GetAmbientPalette](../Topic/CComControlBase::GetAmbientPalette.md)|擷取 **DISPID\_AMBIENT\_PALETTE**，用來存取容器的 `HPALETTE`。|  
|[CComControlBase::GetAmbientProperty](../Topic/CComControlBase::GetAmbientProperty.md)|擷取 `id`指定容器的屬性。|  
|[CComControlBase::GetAmbientRightToLeft](../Topic/CComControlBase::GetAmbientRightToLeft.md)|擷取 **DISPID\_AMBIENT\_RIGHTTOLEFT**，重新導向的內容是由容器顯示。|  
|[CComControlBase::GetAmbientScaleUnits](../Topic/CComControlBase::GetAmbientScaleUnits.md)|擷取 **DISPID\_AMBIENT\_SCALEUNITS**，容器的單位 \(例如英吋或公分\) 標記的顯示。|  
|[CComControlBase::GetAmbientShowGrabHandles](../Topic/CComControlBase::GetAmbientShowGrabHandles.md)|擷取 **DISPID\_AMBIENT\_SHOWGRABHANDLES**，指出容器是否旗標可讓控制項顯示其本身的抓取控點，在作用中時。|  
|[CComControlBase::GetAmbientShowHatching](../Topic/CComControlBase::GetAmbientShowHatching.md)|擷取 **DISPID\_AMBIENT\_SHOWHATCHING**，指出容器是否旗標可讓控制項顯示使用已規劃的樣式，該 UI 為作用中時。|  
|[CComControlBase::GetAmbientSupportsMnemonics](../Topic/CComControlBase::GetAmbientSupportsMnemonics.md)|擷取 **DISPID\_AMBIENT\_SUPPORTSMNEMONICS**，指出容器是否旗標支援鍵盤助憶鍵。|  
|[CComControlBase::GetAmbientTextAlign](../Topic/CComControlBase::GetAmbientTextAlign.md)|擷取 **DISPID\_AMBIENT\_TEXTALIGN**容器，慣用的文字對齊方式:0 一般對齊 \(數字、置中，文字\)， 1 靠左對齊的中央對齊， 2 和 3 的正確對齊的。|  
|[CComControlBase::GetAmbientTopToBottom](../Topic/CComControlBase::GetAmbientTopToBottom.md)|擷取 **DISPID\_AMBIENT\_TOPTOBOTTOM**，重新導向的內容是由容器顯示。|  
|[CComControlBase::GetAmbientUIDead](../Topic/CComControlBase::GetAmbientUIDead.md)|擷取 **DISPID\_AMBIENT\_UIDEAD**，指出容器是否旗標想要控制項來回應使用者介面動作。|  
|[CComControlBase::GetAmbientUserMode](../Topic/CComControlBase::GetAmbientUserMode.md)|擷取 **DISPID\_AMBIENT\_USERMODE**，指出容器是否旗標在執行模式 \(**是**\) 或設計模式 \(**否**\)。|  
|[CComControlBase::GetDirty](../Topic/CComControlBase::GetDirty.md)|傳回資料成員 `m_bRequiresSave`的值。|  
|[CComControlBase::GetZoomInfo](../Topic/CComControlBase::GetZoomInfo.md)|擷取縮放因數的分子和分母的 X 和 Y 值進行就地編輯啟動的控制項。|  
|[CComControlBase::InPlaceActivate](../Topic/CComControlBase::InPlaceActivate.md)|使控制項與非作用中狀態的轉換到任何狀態在 `iVerb` 動詞命令的值。|  
|[CComControlBase::InternalGetSite](../Topic/CComControlBase::InternalGetSite.md)|呼叫這個方法會查詢指標的控制網站加入至識別的介面。|  
|[CComControlBase::OnDraw](../Topic/CComControlBase::OnDraw.md)|覆寫這個方法會繪製自己的控制項。|  
|[CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)|預設 **OnDrawAdvanced** 正規化的裝置內容進行繪圖的準備工作，然後呼叫您的控制項類別的 `OnDraw` 方法。|  
|[CComControlBase::OnKillFocus](../Topic/CComControlBase::OnKillFocus.md)|檢查控制項是就地啟動且有一個 ActiveX 控制項站台，然後通知容器控制項失去焦點。|  
|[CComControlBase::OnMouseActivate](../Topic/CComControlBase::OnMouseActivate.md)|檢查 UI 在使用者模式中，然後啟動控制項。|  
|[CComControlBase::OnPaint](../Topic/CComControlBase::OnPaint.md)|容器準備用於繪製，取得控制項的工作區，然後呼叫控制項類別的 `OnDraw` 方法。|  
|[CComControlBase::OnSetFocus](../Topic/CComControlBase::OnSetFocus.md)|檢查控制項是就地啟動且有一個 ActiveX 控制項站台，然後通知控制項取得焦點的容器。|  
|[CComControlBase::PreTranslateAccelerator](../Topic/CComControlBase::PreTranslateAccelerator.md)|覆寫這個方法以提供您自己的鍵盤快速鍵處理常式的。|  
|[CComControlBase::SendOnClose](../Topic/CComControlBase::SendOnClose.md)|告知諮詢接收向通知持有人註冊關閉控制項。|  
|[CComControlBase::SendOnDataChange](../Topic/CComControlBase::SendOnDataChange.md)|告知諮詢接收向通知預留位置控制項註冊資料已經變更。|  
|[CComControlBase::SendOnRename](../Topic/CComControlBase::SendOnRename.md)|告知諮詢接收向通知持有人登錄控制項具有新 Moniker。|  
|[CComControlBase::SendOnSave](../Topic/CComControlBase::SendOnSave.md)|告知諮詢接收向通知持有人登錄控制項已儲存。|  
|[CComControlBase::SendOnViewChange](../Topic/CComControlBase::SendOnViewChange.md)|告知所有已登錄的諮詢接收控制項檢視已變更。|  
|[CComControlBase::SetControlFocus](../Topic/CComControlBase::SetControlFocus.md)|設定或移除鍵盤焦點從控制項。|  
|[CComControlBase::SetDirty](../Topic/CComControlBase::SetDirty.md)|將資料成員 `m_bRequiresSave` 至 `bDirty`的值。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComControlBase::m\_bAutoSize](../Topic/CComControlBase::m_bAutoSize.md)|表示控制項的旗標不可以是其他大小。|  
|[CComControlBase::m\_bDrawFromNatural](../Topic/CComControlBase::m_bDrawFromNatural.md)|旗標表示 `IDataObjectImpl::GetData` 和 `CComControlBase::GetZoomInfo` 應該將從 `m_sizeNatural` 的控制項大小而不是從 `m_sizeExtent`。|  
|[CComControlBase::m\_bDrawGetDataInHimetric](../Topic/CComControlBase::m_bDrawGetDataInHimetric.md)|旗標表示 `IDataObjectImpl::GetData` 應該用來取代 HIMETRIC 單位為像素\)，在繪製時。|  
|[CComControlBase::m\_bInPlaceActive](../Topic/CComControlBase::m_bInPlaceActive.md)|表示控制項的旗標是就地啟動。|  
|[CComControlBase::m\_bInPlaceSiteEx](../Topic/CComControlBase::m_bInPlaceSiteEx.md)|指示容器的旗標支援 **IOleInPlaceSiteEx** 介面和 O CX96 控制的功能，例如無視窗和重繪閃動可用的控制項。|  
|[CComControlBase::m\_bNegotiatedWnd](../Topic/CComControlBase::m_bNegotiatedWnd.md)|旗標表示控制項是否具有相關支援的容器交涉了 O CX96 控制功能 \(例如重繪閃動可用與無視窗 \(Windowless\) 控制項\)，因此，控制項是視窗型或無視窗 \(Windowless\) 控制項。|  
|[CComControlBase::m\_bRecomposeOnResize](../Topic/CComControlBase::m_bRecomposeOnResize.md)|在容器的控制項變更顯示的大小時，表示控制項的旗標才能重新撰寫自己的簡介。|  
|[CComControlBase::m\_bRequiresSave](../Topic/CComControlBase::m_bRequiresSave.md)|自上次儲存，表示控制項的旗標已變更。|  
|[CComControlBase::m\_bResizeNatural](../Topic/CComControlBase::m_bResizeNatural.md)|表示控制項的旗標若要調整其自然單位 \(其未縮放的實體大小\)，在容器的控制項變更顯示的大小時。|  
|[CComControlBase::m\_bUIActive](../Topic/CComControlBase::m_bUIActive.md)|旗標表示控制項的使用者介面 \(UI\)，例如功能表，而工具列，為作用中。|  
|[CComControlBase::m\_bUsingWindowRgn](../Topic/CComControlBase::m_bUsingWindowRgn.md)|表示控制項的旗標使用由容器提供的視窗區域。|  
|[CComControlBase::m\_bWasOnceWindowless](../Topic/CComControlBase::m_bWasOnceWindowless.md)|表示控制項的旗標是無視窗 \(Windowless\)，，但不一定現在是無視窗 \(Windowless\) 控制項。|  
|[CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md)|表示控制項的旗標應該視窗型，，即使容器支援無視窗 \(Windowless\) 控制項。|  
|[CComControlBase::m\_bWndLess](../Topic/CComControlBase::m_bWndLess.md)|表示控制項的旗標是無視窗 \(Windowless\) 控制項。|  
|[CComControlBase::m\_hWndCD](../Topic/CComControlBase::m_hWndCD.md)|包含視窗控制代碼的參考與控制項。|  
|[CComControlBase::m\_nFreezeEvents](../Topic/CComControlBase::m_nFreezeEvents.md)|次數計數容器凍結事件 \(拒絕\) 接受事件，而不用事件 \(事件接受度干擾解除凍結\)。|  
|[CComControlBase::m\_rcPos](../Topic/CComControlBase::m_rcPos.md)|在控制項的像素的位置，以容器的座標。|  
|[CComControlBase::m\_sizeExtent](../Topic/CComControlBase::m_sizeExtent.md)|控制項的範圍。HIMETRIC 單位 \(每單位為 0.01 公釐\) 特定顯示的。|  
|[CComControlBase::m\_sizeNatural](../Topic/CComControlBase::m_sizeNatural.md)|控制項的實體大小 \(以 HIMETRIC 單位 \(每單位為 0.01 公釐\)。|  
|[CComControlBase::m\_spAdviseSink](../Topic/CComControlBase::m_spAdviseSink.md)|對諮詢連接的直接指標在容器 \(容器的 [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)\)。|  
|[CComControlBase::m\_spAmbientDispatch](../Topic/CComControlBase::m_spAmbientDispatch.md)|可讓您透過 `IDispatch` 指標擷取和設定容器的屬性 `CComDispatchDriver` 物件。|  
|[CComControlBase::m\_spClientSite](../Topic/CComControlBase::m_spClientSite.md)|為控制項的用戶端站台上的指標在容器內。|  
|[CComControlBase::m\_spDataAdviseHolder](../Topic/CComControlBase::m_spDataAdviseHolder.md)|提供標準的方式存放資料物件之間建立諮詢連接的通知接收。|  
|[CComControlBase::m\_spInPlaceSite](../Topic/CComControlBase::m_spInPlaceSite.md)|在容器的 [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)、 [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)或 [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) 介面指標的指標。|  
|[CComControlBase::m\_spOleAdviseHolder](../Topic/CComControlBase::m_spOleAdviseHolder.md)|提供的標準實作保留諮詢連接。|  
  
## 備註  
 這個類別會建立和管理 ATL 控制項的方法。  [CComControl 類別](../../atl/reference/ccomcontrol-class.md)`CComControlBase`從衍生。  使用 ATL 控制項精靈，當您建立標準控制項或 DHTML 控制項，從  `CComControlBase`會自動衍生您的類別。  
  
 如需建立控制項的詳細資訊，請參閱 [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。  如需 ATL 專案精靈的詳細資訊，請參閱本文 [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)