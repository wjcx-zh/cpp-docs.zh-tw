---
title: CComControlBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
dev_langs:
- C++
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18666cc619796bc7ee0216eb9cdf020bd8d8a6f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035743"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 類別

這個類別提供方法來建立及管理 ATL 的控制項。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|如果覆寫您`m_nAppearance`內建屬性不是型別的**簡短**。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|建構函式。|
|[CComControlBase:: ~ CComControlBase](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|擷取所要求介面的指標。|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|確認兩個*iVerb*所使用的參數`IOleObjectImpl::DoVerb`可能會啟用控制項的使用者介面 (*iVerb*等於 OLEIVERB_UIACTIVATE)，定義當使用者按兩下時採取的動作控制項 (*iVerb*等於 OLEIVERB_PRIMARY)，顯示控制項 (*iVerb*等於 OLEIVERB_SHOW)，或啟動的控制項 (*iVerb*等於 OLEIVERB_INPLACEACTIVATE)。|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|確認兩個*iVerb*所使用的參數`IOleObjectImpl::DoVerb`會啟用控制項的使用者介面，並傳回 TRUE。|
|[CComControlBase::DoVerbProperties](#doverbproperties)|顯示控制項的屬性頁。|
|[CComControlBase::FireViewChange](#fireviewchange)|呼叫此方法來指示來進行重繪控制項的容器，或通知控制項的檢視已變更的已註冊的通知接收。|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|擷取目前設定控制項的外觀，DISPID_AMBIENT_APPEARANCE： 一般和 3d 1 的 0。|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|擷取 DISPID_AMBIENT_AUTOCLIP，旗標，指出容器是否支援自動裁剪的控制項顯示區域。|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|擷取 DISPID_AMBIENT_BACKCOLOR，容器所定義的所有控制項的環境背景色彩。|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|擷取 DISPID_AMBIENT_CHARSET，環境設定的容器所定義的所有控制項的字元集。|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|擷取 DISPID_AMBIENT_CODEPAGE，環境設定的容器所定義的所有控制項的字元集。|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|擷取 DISPID_AMBIENT_DISPLAYASDEFAULT，為 TRUE，如果容器已標示為預設按鈕，這個網站中的控制項，並因此按鈕控制項應該繪製本身有較粗框架的旗標。|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|擷取 DISPID_AMBIENT_DISPLAYNAME，容器已提供給控制項的名稱。|
|[CComControlBase::GetAmbientFont](#getambientfont)|擷取容器的指標的環境`IFont`介面。|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|擷取容器的指標的環境`IFontDisp`分派介面。|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|擷取 DISPID_AMBIENT_FORECOLOR，容器所定義的所有控制項的前景色彩。|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|擷取 DISPID_AMBIENT_LOCALEID，容器所使用的語言識別項。|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|擷取 DISPID_AMBIENT_MESSAGEREFLECT，旗標，指出容器是否要接收事件 （例如 WM_DRAWITEM) 的視窗訊息。|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|擷取 DISPID_AMBIENT_PALETTE，用來存取容器的 HPALETTE。|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|擷取所指定的容器屬性*識別碼*。|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|擷取 DISPID_AMBIENT_RIGHTTOLEFT，容器所顯示內容的方向。|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|擷取 DISPID_AMBIENT_SCALEUNITS，容器的環境 （例如英吋或公分為單位） 的單位標籤會顯示。|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|擷取 DISPID_AMBIENT_SHOWGRABHANDLES，旗標，指出容器是否允許控制項來顯示為其本身時使用的抓取控點。|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|擷取 DISPID_AMBIENT_SHOWHATCHING，旗標，指出容器是否允許控制項本身顯示影線圖樣，啟用 UI 時。|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|擷取 DISPID_AMBIENT_SUPPORTSMNEMONICS，旗標，指出容器是否支援鍵盤助憶鍵。|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|擷取 DISPID_AMBIENT_TEXTALIGN，容器所慣用的文字對齊方式： 一般對齊 （數字，文字靠左對齊） 為 0，1 表示靠左對齊、 置中對齊，2，靠右對齊的 3。|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|擷取 DISPID_AMBIENT_TOPTOBOTTOM，容器所顯示內容的方向。|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|擷取 DISPID_AMBIENT_UIDEAD，旗標，指出容器是否想要回應使用者介面動作的控制項。|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|擷取 DISPID_AMBIENT_USERMODE，旗標，指出容器是否在執行模式 (TRUE) 或設計模式 (FALSE)。|
|[CComControlBase::GetDirty](#getdirty)|傳回的資料成員值`m_bRequiresSave`。|
|[CComControlBase::GetZoomInfo](#getzoominfo)|擷取的 x 和 y 值的分子和分母的縮放因數為控制項啟用就地編輯。|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|讓控制項從任何狀態中的動詞命令的非作用中狀態轉換*iVerb*表示。|
|[CComControlBase::InternalGetSite](#internalgetsite)|呼叫這個方法來查詢已識別的介面指標的控制項網站。|
|[CComControlBase::OnDraw](#ondraw)|覆寫這個方法，以繪製您的控制項。|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|預設值`OnDrawAdvanced`標準化的裝置內容準備繪圖，然後呼叫您的控制項類別`OnDraw`方法。|
|[CComControlBase::OnKillFocus](#onkillfocus)|檢查控制項是就地啟用作用中且具有有效的控制站台就會通知容器控制項已遺失焦點。|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|檢查 UI 是在使用者模式中，然後啟動控制項。|
|[CComControlBase::OnPaint](#onpaint)|準備容器來繪製，取得控制項的工作區，然後會呼叫控制項類別的`OnDraw`方法。|
|[CComControlBase::OnSetFocus](#onsetfocus)|檢查控制項是就地啟用作用中且具有有效的控制站台就會通知容器控制項已取得焦點。|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|覆寫這個方法，以提供您自己的鍵盤對應鍵處理常式。|
|[CComControlBase::SendOnClose](#sendonclose)|告知控制項已關閉的通知持有者註冊的所有諮詢接收。|
|[CComControlBase::SendOnDataChange](#sendondatachange)|通知控制項資料已變更的通知持有者註冊的所有諮詢接收。|
|[CComControlBase::SendOnRename](#sendonrename)|通知控制項有新的 moniker 的 advise 持有者註冊的所有諮詢接收。|
|[CComControlBase::SendOnSave](#sendonsave)|告知控制項已儲存的通知持有者註冊的所有諮詢接收。|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|告知所有已登錄諮詢接收，控制項的檢視已變更。|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|設定或移除或從控制項的鍵盤焦點。|
|[CComControlBase::SetDirty](#setdirty)|設定資料成員`m_bRequiresSave`中的值*bDirty*。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|表示控制項不能任何其他大小的旗標。|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|旗標，表示`IDataObjectImpl::GetData`並`CComControlBase::GetZoomInfo`應該設定的控制項大小`m_sizeNatural`而不是從`m_sizeExtent`。|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|旗標，表示`IDataObjectImpl::GetData`應該 HIMETRIC 單位並不像素繪製時使用。|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|表示控制項就地啟用作用中的旗標。|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|旗標，指出容器支援`IOleInPlaceSiteEx`介面和 OCX96 控制功能，例如無視窗和無重繪閃動的控制項。|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|表示與 OCX96 控制功能 （例如閃爍 」 和 「 無視窗控制項），支援的相關容器的控制項已經交涉和視窗化或是無視窗控制項的是否旗標。|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|表示的控制項重新撰寫其簡報，容器會變更控制項的顯示大小時所要的旗標。|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|表示控制項在自上次儲存後已變更的旗標。|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|旗標，指出控制項要調整其自然的範圍 （其未縮放的實體大小） 的容器控制項的顯示大小的變更時。|
|[CComControlBase::m_bUIActive](#m_buiactive)|旗標，指出控制項的使用者介面，例如功能表和工具列，才有作用。|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|旗標，指出控制項使用的容器提供的視窗區域。|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|表示控制項已無視窗，但可能會或可能不是無視窗現在旗標。|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|表示控制項應該 「 視窗，即使容器支援無視窗控制項旗標。|
|[CComControlBase::m_bWndLess](#m_bwndless)|表示控制項無視窗的旗標。|
|[CComControlBase::m_hWndCD](#m_hwndcd)|包含與控制項關聯的視窗控制代碼的參考。|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|次數的計數容器已凍結 （拒絕接受事件） 的事件而不需要介入的解除凍結的事件 （事件接受）。|
|[CComControlBase::m_rcPos](#m_rcpos)|控制項，以表示容器的座標單位為像素位置。|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|以 himetric 為單位 （每個單位為 0.01 公釐為單位） 的特定顯示控制項的範圍。|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|控制項以 himetric 為單位 （每個單位為 0.01 公釐為單位） 的實體大小。|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|在容器上的諮詢連接的直接指標 (容器[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink))。|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A`CComDispatchDriver`物件，可讓您擷取及設定容器的屬性，透過`IDispatch`指標。|
|[CComControlBase::m_spClientSite](#m_spclientsite)|在容器內控制項的用戶端站台指標。|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|提供一種標準方式來保存資料物件之間的諮詢連接，並告知接收。|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|容器的指標[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面指標。|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|提供一個方式來保存諮詢連接的標準實作。|

## <a name="remarks"></a>備註

這個類別提供方法來建立及管理 ATL 的控制項。 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)衍生自`CComControlBase`。 當您建立的標準控制項或 DHTML 控制項使用 ATL 控制項精靈時，精靈會自動衍生您的類別，從`CComControlBase`。

如需建立控制項的詳細資訊，請參閱[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。 如需 ATL 專案精靈 的詳細資訊，請參閱文章[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

如果覆寫您`m_nAppearance`內建屬性不是型別的**簡短**。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>備註

ATL 控制項精靈新增`m_nAppearance`內建屬性的簡短的型別。 覆寫`AppearanceType`如果您使用不同的資料類型。

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

建構函式。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>參數

*h*<br/>
與控制項關聯的視窗控制代碼。

### <a name="remarks"></a>備註

初始化控制項大小至 5080 X 5080 HIMETRIC 單位 (2x"2")，並初始化`CComControlBase`資料成員的值為 NULL 或 FALSE。

##  <a name="dtor"></a>  CComControlBase:: ~ CComControlBase

解構函式。

```
~CComControlBase();
```

### <a name="remarks"></a>備註

視窗型，控制是否`~CComControlBase`終結藉由呼叫[DestroyWindow](/windows/desktop/api/winuser/nf-winuser-destroywindow)。

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

擷取所要求介面的指標。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>參數

*iid*<br/>
所要求介面的 GUID。

*ppv*<br/>
所識別之介面指標的指標*iid*，或如果找不到介面則為 NULL。

### <a name="remarks"></a>備註

只會處理 COM 對應表格中的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

確認兩個*iVerb*所使用的參數`IOleObjectImpl::DoVerb`可能會啟用控制項的使用者介面 (*iVerb*等於 OLEIVERB_UIACTIVATE)，定義當使用者按兩下時採取的動作控制項 (*iVerb*等於 OLEIVERB_PRIMARY)，顯示控制項 (*iVerb*等於 OLEIVERB_SHOW)，或啟動的控制項 (*iVerb*等於 OLEIVERB_INPLACEACTIVATE)。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
值，指出所要執行的動作`DoVerb`。

### <a name="return-value"></a>傳回值

如果為 true *iVerb*等於 OLEIVERB_UIACTIVATE、 OLEIVERB_PRIMARY、 OLEIVERB_SHOW，還是 OLEIVERB_INPLACEACTIVATE; 否則傳回 FALSE。

### <a name="remarks"></a>備註

您可以覆寫這個方法，以定義您自己的啟動指令動詞。

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

確認兩個*iVerb*所使用的參數`IOleObjectImpl::DoVerb`會啟用控制項的使用者介面，並傳回 TRUE。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
值，指出所要執行的動作`DoVerb`。

### <a name="return-value"></a>傳回值

如果為 true *iVerb*等於 OLEIVERB_UIACTIVATE、 OLEIVERB_PRIMARY、 OLEIVERB_SHOW，還是 OLEIVERB_INPLACEACTIVATE。 否則，這個方法會傳回 FALSE。

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

顯示控制項的屬性頁。

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
保留的。

*hwndParent*<br/>
包含控制項的視窗控制代碼。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

呼叫此方法來指示來進行重繪控制項的容器，或通知控制項的檢視已變更的已註冊的通知接收。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果控制項是 active (控制項的類別資料成員[CComControlBase::m_bInPlaceActive](#m_binplaceactive)為 TRUE)，通知您想要重新繪製整個控制項的容器。 如果控制項處於非使用中，會通知控制項的已註冊通知接收 (透過控制項的類別資料成員[CComControlBase::m_spAdviseSink](#m_spadvisesink)) 控制項的檢視已變更。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

擷取目前設定控制項的外觀，DISPID_AMBIENT_APPEARANCE： 一般和 3d 1 的 0。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>參數

*nAppearance*<br/>
DISPID_AMBIENT_APPEARANCE 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

擷取 DISPID_AMBIENT_AUTOCLIP，旗標，指出容器是否支援自動裁剪的控制項顯示區域。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>參數

*bAutoClip*<br/>
DISPID_AMBIENT_AUTOCLIP 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

擷取 DISPID_AMBIENT_BACKCOLOR，容器所定義的所有控制項的環境背景色彩。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>參數

*背景色彩*<br/>
DISPID_AMBIENT_BACKCOLOR 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

擷取 DISPID_AMBIENT_CHARSET，環境設定的容器所定義的所有控制項的字元集。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>參數

*bstrCharSet*<br/>
DISPID_AMBIENT_CHARSET 屬性。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

擷取 DISPID_AMBIENT_CODEPAGE，容器所定義的所有控制項的環境的字碼頁。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>參數

*ulCodePage*<br/>
DISPID_AMBIENT_CODEPAGE 屬性。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

擷取 DISPID_AMBIENT_DISPLAYASDEFAULT，為 TRUE，如果容器已標示為預設按鈕，這個網站中的控制項，並因此按鈕控制項應該繪製本身有較粗框架的旗標。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>參數

*bDisplayAsDefault*<br/>
DISPID_AMBIENT_DISPLAYASDEFAULT 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

擷取 DISPID_AMBIENT_DISPLAYNAME，容器已提供給控制項的名稱。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>參數

*bstrDisplayName*<br/>
DISPID_AMBIENT_DISPLAYNAME 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

擷取容器的指標的環境`IFont`介面。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
指標，容器的環境[IFont](/windows/desktop/api/ocidl/nn-ocidl-ifont)介面。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果屬性為 NULL，則指標為 NULL。 如果指標不是 NULL，則呼叫端必須釋放指標。

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

擷取容器的指標的環境`IFontDisp`分派介面。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
指標，容器的環境[IFontDisp](https://msdn.microsoft.com/library/windows/desktop/ms692695)分派介面。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

如果屬性為 NULL，則指標為 NULL。 如果指標不是 NULL，則呼叫端必須釋放指標。

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

擷取 DISPID_AMBIENT_FORECOLOR，容器所定義的所有控制項的前景色彩。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>參數

*前景色彩*<br/>
DISPID_AMBIENT_FORECOLOR 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

擷取 DISPID_AMBIENT_LOCALEID，容器所使用的語言識別項。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>參數

*lcid*<br/>
DISPID_AMBIENT_LOCALEID 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

控制項可以使用這個識別項，來調整它的使用者介面，以不同的語言。

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

擷取 DISPID_AMBIENT_MESSAGEREFLECT，旗標，指出容器是否要接收視窗訊息 (例如`WM_DRAWITEM`) 做為事件。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>參數

*bMessageReflect*<br/>
DISPID_AMBIENT_MESSAGEREFLECT 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

擷取 DISPID_AMBIENT_PALETTE，用來存取容器的 HPALETTE。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>參數

*hPalette*<br/>
DISPID_AMBIENT_PALETTE 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

擷取所指定的容器屬性*dispid*。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>參數

*dispid*<br/>
要擷取之容器屬性識別項。

*var*<br/>
接收屬性的變數。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 提供了一組協助程式函式來擷取特定屬性，例如[CComControlBase::GetAmbientBackColor](#getambientbackcolor)。 如果不沒有可用的任何合適的方法，使用`GetAmbientProperty`。

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

擷取 DISPID_AMBIENT_RIGHTTOLEFT，容器所顯示內容的方向。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>參數

*bRightToLeft*<br/>
DISPID_AMBIENT_RIGHTTOLEFT 屬性。 如果內容由右至左顯示，請設為 TRUE，為 FALSE 可以顯示左到右。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

擷取 DISPID_AMBIENT_SCALEUNITS，容器的環境 （例如英吋或公分為單位） 的單位標籤會顯示。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>參數

*bstrScaleUnits*<br/>
DISPID_AMBIENT_SCALEUNITS 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

擷取 DISPID_AMBIENT_SHOWGRABHANDLES，旗標，指出容器是否允許控制項來顯示為其本身時使用的抓取控點。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>參數

*bShowGrabHandles*<br/>
DISPID_AMBIENT_SHOWGRABHANDLES 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

擷取 DISPID_AMBIENT_SHOWHATCHING，旗標，指出容器是否允許控制項本身顯示影線圖樣，作用中控制項的使用者介面時。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>參數

*bShowHatching*<br/>
DISPID_AMBIENT_SHOWHATCHING 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

擷取 DISPID_AMBIENT_SUPPORTSMNEMONICS，旗標，指出容器是否支援鍵盤助憶鍵。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>參數

*bSupportsMnemonics*<br/>
DISPID_AMBIENT_SUPPORTSMNEMONICS 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

擷取 DISPID_AMBIENT_TEXTALIGN，容器所慣用的文字對齊方式： 一般對齊 （數字，文字靠左對齊） 為 0，1 表示靠左對齊、 置中對齊，2，靠右對齊的 3。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>參數

*nTextAlign*<br/>
DISPID_AMBIENT_TEXTALIGN 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

擷取 DISPID_AMBIENT_TOPTOBOTTOM，容器所顯示內容的方向。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>參數

*bTopToBottom*<br/>
DISPID_AMBIENT_TOPTOBOTTOM 屬性。 設定為 TRUE，如果文字會顯示從上到下，為 FALSE 顯示底部到頂端。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

擷取 DISPID_AMBIENT_UIDEAD，旗標，指出容器是否想要回應使用者介面動作的控制項。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>參數

*bUIDead*<br/>
DISPID_AMBIENT_UIDEAD 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果為 TRUE，控制項應該不會回應。 此旗標適用於無論 DISPID_AMBIENT_USERMODE 旗標。 請參閱[CComControlBase::GetAmbientUserMode](#getambientusermode)。

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

擷取 DISPID_AMBIENT_USERMODE，旗標，指出容器是否在執行模式 (TRUE) 或設計模式 (FALSE)。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>參數

*bUserMode*<br/>
DISPID_AMBIENT_USERMODE 屬性。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="getdirty"></a>  CComControlBase::GetDirty

傳回的資料成員值`m_bRequiresSave`。

```
BOOL GetDirty();
```

### <a name="return-value"></a>傳回值

傳回的值資料成員[m_bRequiresSave](#m_brequiressave)。

### <a name="remarks"></a>備註

此值會設定使用[CComControlBase::SetDirty](#setdirty)。

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

擷取的 x 和 y 值的分子和分母的縮放因數為控制項啟用就地編輯。

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*di*<br/>
結構，用以保存縮放因數的分子和分母。 如需詳細資訊，請參閱 < [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。

### <a name="remarks"></a>備註

縮放因數是其目前的範圍內的控制項的原始大小的比例。

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

讓控制項從任何狀態中的動詞命令的非作用中狀態轉換*iVerb*表示。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
值，指出所要執行的動作[IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)。

*prcPosRect*<br/>
就地控制項的位置指標。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

之前啟動過程中，這個方法會檢查控制項具有用戶端站台、 檢查多少控制項為可見，並取得父視窗中的控制項的位置。 啟動控制項之後，這個方法會啟用控制項的使用者介面，並告知要顯示控制項的容器。

這個方法也會擷取`IOleInPlaceSite`， `IOleInPlaceSiteEx`，或`IOleInPlaceSiteWindowless`控制項的介面指標並將它儲存在控制項類別的資料成員[CComControlBase::m_spInPlaceSite](#m_spinplacesite)。 控制項類別資料成員[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)， [CComControlBase::m_bWndLess](#m_bwndless)， [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)，和[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)設為 true，則視情況。

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

呼叫這個方法來查詢已識別的介面指標的控制項網站。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>參數

*riid*<br/>
應該傳回介面指標 IID *ppUnkSite*。

*ppUnkSite*<br/>
接收要求中的介面指標的指標變數的地址*riid*。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

如果站台支援所要求的介面*riid*，藉由傳回的指標*ppUnkSite*。 否則，請*ppUnkSite*設為 NULL。

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

表示控制項不能任何其他大小的旗標。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>備註

這個旗標會檢查`IOleObjectImpl::SetExtent`而且，如果為 TRUE，會導致此函數傳回 E_FAIL。

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

如果您加入**自動調整大小**選項[內建屬性](../../atl/reference/stock-properties-atl-control-wizard.md) 索引標籤的 ATL 控制項精靈，精靈會自動建立這個資料成員控制項類別中，建立 put 並取得屬性的方法並支援[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)屬性變更時自動通知容器。

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

旗標，表示`IDataObjectImpl::GetData`並`CComControlBase::GetZoomInfo`應該設定的控制項大小`m_sizeNatural`而不是從`m_sizeExtent`。

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

旗標，表示`IDataObjectImpl::GetData`應該 HIMETRIC 單位並不像素繪製時使用。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>備註

每個邏輯 HIMETRIC 單位為 0.01 公釐。

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

表示控制項就地啟用作用中的旗標。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>備註

這表示控制項為可見和其視窗中，如果有的話，會顯示，但其功能表與工具列可能無法使用。 `m_bUIActive`旗標指出控制項的使用者介面，例如功能表，也是作用中。

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

旗標，指出容器支援`IOleInPlaceSiteEx`介面和 OCX96 控制功能，例如無視窗和無重繪閃動的控制項。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

資料成員`m_spInPlaceSite`指向[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面，根據的值`m_bWndLess`和`m_bInPlaceSiteEx`旗標。 (資料成員`m_bNegotiatedWnd`必須是 TRUE 為`m_spInPlaceSite`為有效的指標。)

如果`m_bWndLess`為 FALSE 時，`m_bInPlaceSiteEx`為 TRUE 時，`m_spInPlaceSite`是`IOleInPlaceSiteEx`介面指標。 請參閱[m_spInPlaceSite](#m_spinplacesite)顯示這些三個資料成員之間的關聯性的資料表。

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

表示與 OCX96 控制功能 （例如閃爍 」 和 「 無視窗控制項），支援的相關容器的控制項已經交涉和視窗化或是無視窗控制項的是否旗標。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

`m_bNegotiatedWnd`旗標必須是 TRUE 為`m_spInPlaceSite`為有效的指標。

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

表示的控制項重新撰寫其簡報，容器會變更控制項的顯示大小時所要的旗標。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

這個旗標會檢查[IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent)而且，如果為 TRUE，`SetExtent`通知檢視變更的容器。 如果設定此旗標，OLEMISC_RECOMPOSEONRESIZE 位元[OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc)也應該設定列舉型別。

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

表示控制項在自上次儲存後已變更的旗標。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>備註

值`m_bRequiresSave`可以使用設定[CComControlBase::SetDirty](#setdirty)並使用擷取[CComControlBase::GetDirty](#getdirty)。

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

旗標，指出控制項要調整其自然的範圍 （其未縮放的實體大小） 的容器控制項的顯示大小的變更時。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>備註

這個旗標會檢查`IOleObjectImpl::SetExtent`和大小，則為 TRUE，如果已傳入`SetExtent`指派給`m_sizeNatural`。

大小傳入`SetExtent`一定會指派給`m_sizeExtent`無關的值、 `m_bResizeNatural`。

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

旗標，指出控制項的使用者介面，例如功能表和工具列，才有作用。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>備註

`m_bInPlaceActive`旗標，表示控制項作用中，但不是其使用者介面正在使用中。

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

旗標，指出控制項使用的容器提供的視窗區域。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

表示控制項已無視窗，但可能會或可能不是無視窗現在旗標。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

表示控制項應該 「 視窗，即使容器支援無視窗控制項旗標。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess

表示控制項無視窗的旗標。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

資料成員`m_spInPlaceSite`指向[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面，根據的值`m_bWndLess`並[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)旗標。 (資料成員[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)必須是 TRUE for [CComControlBase::m_spInPlaceSite](#m_spinplacesite)為有效的指標。)

如果`m_bWndLess`為 TRUE 時，`m_spInPlaceSite`是`IOleInPlaceSiteWindowless`介面指標。 請參閱[CComControlBase::m_spInPlaceSite](#m_spinplacesite)顯示這些資料成員之間完成的關聯性的資料表。

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

包含與控制項關聯的視窗控制代碼的參考。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

次數的計數容器已凍結 （拒絕接受事件） 的事件而不需要介入的解除凍結的事件 （事件接受）。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

控制項，以表示容器的座標單位為像素位置。

```
RECT m_rcPos;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent

以 himetric 為單位 （每個單位為 0.01 公釐為單位） 的特定顯示控制項的範圍。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

此大小會調整所顯示。 控制項的實體大小以指定`m_sizeNatural`資料成員和已修正。

您可以將大小轉換為全域函式與像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

控制項以 himetric 為單位 （每個單位為 0.01 公釐為單位） 的實體大小。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

此大小固定的同時在大小`m_sizeExtent`調整所顯示。

您可以將大小轉換為全域函式與像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

在容器上的諮詢連接的直接指標 (容器[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink))。

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

A`CComDispatchDriver`物件，可讓您擷取和設定物件的屬性，透過`IDispatch`指標。

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

在容器內控制項的用戶端站台指標。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

提供一種標準方式來保存資料物件之間的諮詢連接，並告知接收。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

資料物件是的控制項，可以傳送資料，並實作[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)，其方法指定的資料格式和傳輸媒介。

介面`m_spDataAdviseHolder`會實作[IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise)並[IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise)方法來建立和刪除容器的諮詢連接。 控制項的容器必須實作所支援的通知接收[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)介面。

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

容器的指標[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面指標。

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

`m_spInPlaceSite`指標無效才[m_bNegotiatedWnd](#m_bnegotiatedwnd)旗標為 TRUE。

下表顯示如何`m_spInPlaceSite`指標類型而定[m_bWndLess](#m_bwndless)並[m_bInPlaceSiteEx](#m_binplacesiteex)資料成員旗標：

|m_spInPlaceSite 類型|m_bWndLess 值|m_bInPlaceSiteEx 值|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|true|TRUE 或 FALSE|
|`IOleInPlaceSiteEx`|false|true|
|`IOleInPlaceSite`|false|false|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

提供一個方式來保存諮詢連接的標準實作。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要使用此資料成員，您的控制項類別中，您必須將它宣告為資料成員控制項類別中。 因為它等位中的基底類別內宣告您的控制項類別不會從基底類別繼承這個資料成員。

介面`m_spOleAdviseHolder`會實作[IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise)並[IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise)方法來建立和刪除容器的諮詢連接。 控制項的容器必須實作所支援的通知接收[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)介面。

##  <a name="ondraw"></a>  CComControlBase::OnDraw

覆寫這個方法，以繪製您的控制項。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*di*<br/>
參考[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)包含繪圖的資訊，例如繪製方面，而控制項界限內的結構和繪圖或未最佳化。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

預設值`OnDraw`刪除或還原裝置內容或不執行任何動作，根據設定的旗標[CComControlBase::OnDrawAdvanced](#ondrawadvanced)。

`OnDraw`方法會自動加入至您的控制項類別使用 ATL 控制項精靈建立您的控制項時。 精靈的預設`OnDraw`以"ATL 8.0"的標籤繪製一個矩形。

### <a name="example"></a>範例

範例，請參閱[CComControlBase::GetAmbientAppearance](#getambientappearance)。

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

預設值`OnDrawAdvanced`標準化的裝置內容準備繪圖，然後呼叫您的控制項類別`OnDraw`方法。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*di*<br/>
參考[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)包含繪圖的資訊，例如繪製方面，而控制項界限內的結構和繪圖或未最佳化。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果您想要接受由容器通過卻未標準化的裝置內容，請覆寫這個方法。

請參閱[CComControlBase::OnDraw](#ondraw)如需詳細資訊。

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

檢查控制項是就地啟用作用中且具有有效的控制站台就會通知容器控制項已遺失焦點。

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
保留的。

*wParam*<br/>
保留的。

*lParam*<br/>
保留的。

*bHandled*<br/>
旗標，指出是否已成功處理的視窗訊息。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

一律會傳回 1。

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

檢查 UI 是在使用者模式中，然後啟動控制項。

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
保留的。

*wParam*<br/>
保留的。

*lParam*<br/>
保留的。

*bHandled*<br/>
旗標，指出是否已成功處理的視窗訊息。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

一律會傳回 1。

##  <a name="onpaint"></a>  CComControlBase::OnPaint

準備容器來繪製，取得控制項的工作區，然後會呼叫控制項類別的`OnDrawAdvanced`方法。

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
保留的。

*wParam*<br/>
現有的 HDC。

*lParam*<br/>
保留的。

*lResult*<br/>
保留的。

### <a name="return-value"></a>傳回值

一律會傳回零。

### <a name="remarks"></a>備註

如果*wParam*不是 NULL，`OnPaint`假設它包含有效的 HDC，並使用它，而不要[CComControlBase::m_hWndCD](#m_hwndcd)。

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

檢查控制項是就地啟用作用中且具有有效的控制站台就會通知容器控制項已取得焦點。

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
保留的。

*wParam*<br/>
保留的。

*lParam*<br/>
保留的。

*bHandled*<br/>
旗標，指出是否已成功處理的視窗訊息。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

一律會傳回 1。

### <a name="remarks"></a>備註

傳送通知給容器的控制項已收到焦點。

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

覆寫這個方法，以提供您自己的鍵盤對應鍵處理常式。

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
保留的。

*hRet*<br/>
保留的。

### <a name="return-value"></a>傳回值

依預設會傳回 FALSE。

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

告知控制項已關閉的通知持有者註冊的所有諮詢接收。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

傳送通知控制項已關閉其通知的接收。

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

通知控制項資料已變更的通知持有者註冊的所有諮詢接收。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>參數

*advf*<br/>
通知旗標，指定如何在呼叫[IAdviseSink::OnDataChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-ondatachange)為止。 值是從[ADVF](/windows/desktop/api/objidl/ne-objidl-tagadvf)列舉型別。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

通知控制項有新的 moniker 的 advise 持有者註冊的所有諮詢接收。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>參數

*pmk*<br/>
新的 moniker，控制項的指標。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

傳送通知的 moniker 控制項已變更。

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

告知控制項已儲存的通知持有者註冊的所有諮詢接收。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

傳送通知，控制項就具有儲存其資料。

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

告知所有已登錄諮詢接收，控制項的檢視已變更。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>參數

*dwAspect*<br/>
外觀的控制項檢視。

*lindex*<br/>
檢視已變更的部分。 只有-1 是有效的。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

`SendOnViewChange` 呼叫[IAdviseSink::OnViewChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-onviewchange)。 唯一的值*lindex*目前支援為-1，這表示感興趣的是整個檢視。

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

設定或移除或從控制項的鍵盤焦點。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>參數

*bGrab*<br/>
如果為 TRUE，將鍵盤焦點設為呼叫控制項。 如果為 FALSE，移除鍵盤焦點從呼叫端的控制項，提供焦點。

### <a name="return-value"></a>傳回值

如果控制項成功接收焦點，為 true，則傳回否則為 FALSE。

### <a name="remarks"></a>備註

針對視窗型控制項，而 Windows API 函式[SetFocus](https://msdn.microsoft.com/library/windows/desktop/ms646312)呼叫。 無視窗控制項，如[IOleInPlaceSiteWindowless::SetFocus](/windows/desktop/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus)呼叫。 透過這個呼叫，無視窗控制項取得鍵盤焦點，並可回應視窗訊息。

##  <a name="setdirty"></a>  CComControlBase::SetDirty

設定資料成員`m_bRequiresSave`中的值*bDirty*。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>參數

*bDirty*<br/>
值的資料成員[CComControlBase::m_bRequiresSave](#m_brequiressave)。

### <a name="remarks"></a>備註

`SetDirty(TRUE)` 應該加上旗標已變更的控制項，自上次儲存後呼叫。 值`m_bRequiresSave`擷取[CComControlBase::GetDirty](#getdirty)。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
