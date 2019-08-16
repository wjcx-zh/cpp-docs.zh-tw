---
title: CComControlBase 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 36afd716009848ccd2e2f0ab966f66f573acdfd8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497365"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 類別

這個類別會提供建立和管理 ATL 控制項的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|如果您`m_nAppearance`的庫存屬性不是**short**類型, 則覆寫。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|建構函式。|
|[CComControlBase:: ~ CComControlBase](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|擷取所要求介面的指標。|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|檢查所使用 `IOleObjectImpl::DoVerb`的 iVerb 參數是否啟動控制項的使用者介面 (*iVerb* equals OLEIVERB_UIACTI加值稅E), 定義使用者按兩下控制項時所採取的動作 (*iVerb* equals OLEIVERB_主要)、顯示控制項 (*iVerb* equals OLEIVERB_SHOW), 或啟動控制項 (*iVerb* equals OLEIVERB_INPLACEACTI加值稅E)。|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|檢查所使用 `IOleObjectImpl::DoVerb`的 iVerb 參數是否會使控制項的使用者介面啟動並傳回 TRUE。|
|[CComControlBase::DoVerbProperties](#doverbproperties)|顯示控制項的屬性頁。|
|[CComControlBase::FireViewChange](#fireviewchange)|呼叫這個方法來指示容器重繪控制項, 或通知已註冊的通知接收器, 控制項的 view 已變更。|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|抓取 DISPID_AMBIENT_APPEARANCE, 這是控制項目前的外觀設定:0代表平面, 1 代表3D。|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|抓取 DISPID_AMBIENT_AUTOCLIP, 這是一個旗標, 指出容器是否支援控制項顯示區域的自動裁剪。|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|抓取 DISPID_AMBIENT_BACKCOLOR, 這是容器所定義之所有控制項的環境背景色彩。|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|抓取容器所定義之所有控制項的環境字元集 (DISPID_AMBIENT_CHARSET)。|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|抓取容器所定義之所有控制項的環境字元集 (DISPID_AMBIENT_CODEPAGE)。|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|抓取 DISPID_AMBIENT_DISPLAYASDEFAULT, 如果容器已將此網站中的控制項標記為預設按鈕, 則為 TRUE 的旗標, 因此按鈕控制項應該以較寬的框架繪製其本身。|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|抓取 DISPID_AMBIENT_DISPLAYNAME, 也就是容器提供給控制項的名稱。|
|[CComControlBase::GetAmbientFont](#getambientfont)|抓取容器環境`IFont`介面的指標。|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|抓取容器環境`IFontDisp`分派介面的指標。|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|抓取 DISPID_AMBIENT_FORECOLOR, 這是容器所定義之所有控制項的環境前景色彩。|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|抓取 DISPID_AMBIENT_LOCALEID, 這是容器所使用之語言的識別碼。|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|抓取 DISPID_AMBIENT_MESSAGEREFLECT, 這是一個旗標, 指出容器是否想要接收視窗訊息 (例如 WM_DRAWITEM) 作為事件。|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|抓取 DISPID_AMBIENT_PALETTE, 用來存取容器的 HPALETTE。|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|抓取*識別碼*所指定的容器屬性。|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|抓取 DISPID_AMBIENT_RIGHTTOLEFT, 這是容器顯示內容的方向。|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|抓取 DISPID_AMBIENT_SCALEUNITS, 這是用於標記顯示的容器環境單位 (例如, 英寸或釐米)。|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|抓取 DISPID_AMBIENT_SHOWGRABHANDLES, 這是一個旗標, 指出容器是否允許控制項在使用中時顯示其本身的抓取控點。|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|抓取 DISPID_AMBIENT_SHOWHATCHING, 這是一個旗標, 指出容器是否允許控制項在 UI 作用中時, 以影線圖樣顯示其本身。|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|抓取 DISPID_AMBIENT_SUPPORTSMNEMONICS, 此旗標表示容器是否支援鍵盤助憶鍵。|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|抓取 DISPID_AMBIENT_TEXTALIGN, 這是容器慣用的文字對齊方式:0代表一般對齊 (數位 right、靠左文字)、1代表左對齊、2表示置中對齊, 而3用於右對齊。|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|抓取 DISPID_AMBIENT_TOPTOBOTTOM, 這是容器顯示內容的方向。|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|抓取 DISPID_AMBIENT_UIDEAD, 這是一個旗標, 指出容器是否希望控制項回應使用者介面動作。|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|抓取 DISPID_AMBIENT_USERMODE, 此旗標表示容器處於執行模式 (TRUE) 或設計模式 (FALSE)。|
|[CComControlBase::GetDirty](#getdirty)|傳回資料成員`m_bRequiresSave`的值。|
|[CComControlBase::GetZoomInfo](#getzoominfo)|抓取啟動進行就地編輯之控制項的顯示比例之分子和分母的 x 和 y 值。|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|使控制項從非使用中狀態轉換成*iVerb*中的動詞所指出的任何狀態。|
|[CComControlBase::InternalGetSite](#internalgetsite)|呼叫這個方法來查詢控制網站, 找出已識別介面的指標。|
|[CComControlBase::OnDraw](#ondraw)|覆寫此方法以繪製您的控制項。|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|預設`OnDrawAdvanced`會準備正規化的裝置內容以進行繪製, 然後呼叫控制項類別的`OnDraw`方法。|
|[CComControlBase::OnKillFocus](#onkillfocus)|檢查控制項是否為就地作用並具有有效的控制網站, 然後通知容器控制項已失去焦點。|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|檢查 UI 是否處於使用者模式, 然後啟用控制項。|
|[CComControlBase::OnPaint](#onpaint)|準備用於繪製的容器, 取得控制項的工作區, 然後呼叫控制項類別的`OnDraw`方法。|
|[CComControlBase::OnSetFocus](#onsetfocus)|檢查控制項是否為就地作用並具有有效的控制網站, 然後通知容器控制項已取得焦點。|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|覆寫這個方法, 以提供您自己的鍵盤快速鍵處理常式。|
|[CComControlBase::SendOnClose](#sendonclose)|通知已向通知持有者註冊控制項已關閉的所有諮詢接收器。|
|[CComControlBase::SendOnDataChange](#sendondatachange)|通知所有向通知持有者註冊的通知接收, 控制項資料已變更。|
|[CComControlBase::SendOnRename](#sendonrename)|通知已向通知持有者註冊的所有諮詢接收器, 控制項都有新的名字標記。|
|[CComControlBase::SendOnSave](#sendonsave)|通知所有向通知持有者註冊的通知接收器已儲存控制項。|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|通知所有已註冊的通知接收, 控制項的 view 已變更。|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|設定或移除控制項的鍵盤焦點。|
|[CComControlBase::SetDirty](#setdirty)|將資料成員`m_bRequiresSave`設定為*bDirty*中的值。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|表示控制項不能是任何其他大小的旗標。|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|旗標, `IDataObjectImpl::GetData`表示`CComControlBase::GetZoomInfo`和應該從`m_sizeNatural`設定控制項大小, 而不`m_sizeExtent`是來自。|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|旗標, `IDataObjectImpl::GetData`指出繪製時應該使用 HIMETRIC 單位, 而不是圖元。|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|表示控制項為就地作用中的旗標。|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|表示容器支援介面和 OCX96 `IOleInPlaceSiteEx`控制功能的旗標, 例如無視窗和無閃爍的控制項。|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|表示控制項是否已與容器進行協商的旗標, 以支援 OCX96 控制項功能 (例如不閃爍和無視窗控制項), 以及控制項是否為視窗型或無視窗。|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|表示控制項想要在容器變更控制項的顯示大小時 recompose 其呈現的旗標。|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|表示控制項自上次儲存後已變更的旗標。|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|旗標, 表示當容器變更控制項的顯示大小時, 控制項想要調整其自然範圍的大小 (其未縮放的實體大小)。|
|[CComControlBase::m_bUIActive](#m_buiactive)|表示控制項的使用者介面 (例如功能表和工具列) 為使用中的旗標。|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|表示控制項正在使用容器提供的視窗區域的旗標。|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|表示控制項已為無視窗的旗標, 但現在不一定是無視窗的。|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|表示控制項應為視窗型的旗標, 即使容器支援無視窗控制項也一樣。|
|[CComControlBase::m_bWndLess](#m_bwndless)|表示控制項為無視窗的旗標。|
|[CComControlBase::m_hWndCD](#m_hwndcd)|包含與控制項相關聯之視窗控制碼的參考。|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|容器具有凍結事件的次數計數 (拒絕接受事件), 而不會有事件的中途解除凍結 (接受事件)。|
|[CComControlBase::m_rcPos](#m_rcpos)|控制項的位置 (以圖元為單位), 以容器的座標表示。|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|特定顯示器的 HIMETRIC 單位 (每個單位為0.01 毫米) 控制項的範圍。|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|控制項在 HIMETRIC 單位中的實體大小 (每個單位為0.01 毫米)。|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|容器 (容器的[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)) 上諮詢連接的直接指標。|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|物件, 可讓您`IDispatch`透過指標來抓取和設定容器的屬性。 `CComDispatchDriver`|
|[CComControlBase::m_spClientSite](#m_spclientsite)|容器內控制項之用戶端網站的指標。|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|提供標準方法來保存資料物件與建議接收之間的諮詢連接。|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|容器的[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面指標的指標。|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|提供一種標準的執行方式來保存諮詢連接。|

## <a name="remarks"></a>備註

這個類別會提供建立和管理 ATL 控制項的方法。 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)衍生自`CComControlBase`。 當您使用 ATL 控制項 Wizard 建立標準控制項或 DHTML 控制項時, 嚮導會自動從`CComControlBase`衍生您的類別。

如需建立控制項的詳細資訊, 請參閱[ATL 教學](../../atl/active-template-library-atl-tutorial.md)課程。 如需 ATL 專案 Wizard 的詳細資訊, 請參閱[建立 Atl 專案一](../../atl/reference/creating-an-atl-project.md)文。

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="appearancetype"></a>CComControlBase::AppearanceType

如果您`m_nAppearance`的庫存屬性不是**short**類型, 則覆寫。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>備註

ATL 控制項嚮導會加入`m_nAppearance` short 類型的內建屬性。 如果`AppearanceType`您使用不同的資料類型, 則覆寫。

##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

建構函式。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>參數

*h*<br/>
與控制項相關聯之視窗的控制碼。

### <a name="remarks"></a>備註

將控制項大小初始化為 5080X5080 HIMETRIC 單位 (2 「X2」), 並將`CComControlBase`資料成員值初始化為 Null 或 FALSE。

##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase

解構函式。

```
~CComControlBase();
```

### <a name="remarks"></a>備註

如果控制項是視窗型, `~CComControlBase`則會藉由呼叫[DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow)來將其損毀。

##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

擷取所要求介面的指標。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>參數

*iid*<br/>
所要求之介面的 GUID。

*ppv*<br/>
*Iid*所識別之介面指標的指標, 如果找不到介面, 則為 Null。

### <a name="remarks"></a>備註

只處理 COM 對應表中的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

檢查所使用 `IOleObjectImpl::DoVerb`的 iVerb 參數是否啟動控制項的使用者介面 (*iVerb* equals OLEIVERB_UIACTI加值稅E), 定義使用者按兩下控制項時所採取的動作 (*iVerb* equals OLEIVERB_主要)、顯示控制項 (*iVerb* equals OLEIVERB_SHOW), 或啟動控制項 (*iVerb* equals OLEIVERB_INPLACEACTI加值稅E)。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指出要執行`DoVerb`之動作的值。

### <a name="return-value"></a>傳回值

如果*iVerb*等於 OLEIVERB_UIACTI加值稅E、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或 OLEIVERB_INPLACEACTI加值稅E, 則傳回 TRUE;否則, 會傳回 FALSE。

### <a name="remarks"></a>備註

您可以覆寫這個方法, 以定義您自己的啟用動詞。

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

檢查所使用 `IOleObjectImpl::DoVerb`的 iVerb 參數是否會使控制項的使用者介面啟動並傳回 TRUE。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指出要執行`DoVerb`之動作的值。

### <a name="return-value"></a>傳回值

如果*iVerb*等於 OLEIVERB_UIACTI加值稅E、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或 OLEIVERB_INPLACEACTI加值稅E, 則傳回 TRUE。 否則, 此方法會傳回 FALSE。

##  <a name="doverbproperties"></a>CComControlBase::D oVerbProperties

顯示控制項的屬性頁。

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
保留的。

*hwndParent*<br/>
包含控制項之視窗的控制碼。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>CComControlBase::FireViewChange

呼叫這個方法來指示容器重繪控制項, 或通知已註冊的通知接收器, 控制項的 view 已變更。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

如果控制項為使用中 (控制項類別資料成員[CComControlBase:: m_bInPlaceActive](#m_binplaceactive)為 TRUE), 則會通知容器您想要重繪整個控制項。 如果控制項處於非作用中狀態, 會通知控制項的已註冊的建議接收器 (透過控制項類別資料成員[CComControlBase:: m_spAdviseSink](#m_spadvisesink)), 控制項的視圖已變更。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

抓取 DISPID_AMBIENT_APPEARANCE, 這是控制項目前的外觀設定:0代表平面, 1 代表3D。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>參數

*nAppearance*<br/>
屬性 DISPID_AMBIENT_APPEARANCE。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

抓取 DISPID_AMBIENT_AUTOCLIP, 這是一個旗標, 指出容器是否支援控制項顯示區域的自動裁剪。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>參數

*bAutoClip*<br/>
屬性 DISPID_AMBIENT_AUTOCLIP。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

抓取 DISPID_AMBIENT_BACKCOLOR, 這是容器所定義之所有控制項的環境背景色彩。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>參數

*BackColor*<br/>
屬性 DISPID_AMBIENT_BACKCOLOR。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

抓取容器所定義之所有控制項的環境字元集 (DISPID_AMBIENT_CHARSET)。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>參數

*bstrCharSet*<br/>
屬性 DISPID_AMBIENT_CHARSET。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

抓取 DISPID_AMBIENT_CODEPAGE, 這是容器所定義之所有控制項的環境字碼頁。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>參數

*ulCodePage*<br/>
屬性 DISPID_AMBIENT_CODEPAGE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

抓取 DISPID_AMBIENT_DISPLAYASDEFAULT, 如果容器已將此網站中的控制項標記為預設按鈕, 則為 TRUE 的旗標, 因此按鈕控制項應該以較寬的框架繪製其本身。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>參數

*bDisplayAsDefault*<br/>
屬性 DISPID_AMBIENT_DISPLAYASDEFAULT。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

抓取 DISPID_AMBIENT_DISPLAYNAME, 也就是容器提供給控制項的名稱。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>參數

*bstrDisplayName*<br/>
屬性 DISPID_AMBIENT_DISPLAYNAME。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont

抓取容器環境`IFont`介面的指標。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
容器環境[IFont](/windows/win32/api/ocidl/nn-ocidl-ifont)介面的指標。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

如果屬性為 Null, 指標會是 Null。 如果指標不是 Null, 則呼叫端必須釋放指標。

##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

抓取容器環境`IFontDisp`分派介面的指標。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
容器環境[IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp)分派介面的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果屬性為 Null, 指標會是 Null。 如果指標不是 Null, 則呼叫端必須釋放指標。

##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

抓取 DISPID_AMBIENT_FORECOLOR, 這是容器所定義之所有控制項的環境前景色彩。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>參數

*ForeColor*<br/>
屬性 DISPID_AMBIENT_FORECOLOR。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

抓取 DISPID_AMBIENT_LOCALEID, 這是容器所使用之語言的識別碼。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>參數

*lcid*<br/>
屬性 DISPID_AMBIENT_LOCALEID。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

控制項可以使用這個識別碼, 將其使用者介面調整成不同的語言。

##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

抓取 DISPID_AMBIENT_MESSAGEREFLECT, 這是一個旗標, 指出容器是否想要接收視窗訊息`WM_DRAWITEM`(例如) 做為事件。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>參數

*bMessageReflect*<br/>
屬性 DISPID_AMBIENT_MESSAGEREFLECT。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

抓取 DISPID_AMBIENT_PALETTE, 用來存取容器的 HPALETTE。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>參數

*hPalette*<br/>
屬性 DISPID_AMBIENT_PALETTE。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

抓取*dispid*所指定的容器屬性。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>參數

*dispid*<br/>
要抓取的容器屬性識別碼。

*var*<br/>
要接收屬性的變數。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 提供了一組 helper 函式來抓取特定的屬性, 例如[CComControlBase:: GetAmbientBackColor](#getambientbackcolor)。 如果沒有適用的可用方法, 請使用`GetAmbientProperty`。

##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft

抓取 DISPID_AMBIENT_RIGHTTOLEFT, 這是容器顯示內容的方向。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>參數

*bRightToLeft*<br/>
屬性 DISPID_AMBIENT_RIGHTTOLEFT。 如果內容是由右至左顯示, 則設為 TRUE, 如果是由左至右顯示, 則設定為 FALSE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits

抓取 DISPID_AMBIENT_SCALEUNITS, 這是用於標記顯示的容器環境單位 (例如, 英寸或釐米)。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>參數

*bstrScaleUnits*<br/>
屬性 DISPID_AMBIENT_SCALEUNITS。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

抓取 DISPID_AMBIENT_SHOWGRABHANDLES, 這是一個旗標, 指出容器是否允許控制項在使用中時顯示其本身的抓取控點。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>參數

*bShowGrabHandles*<br/>
屬性 DISPID_AMBIENT_SHOWGRABHANDLES。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

抓取 DISPID_AMBIENT_SHOWHATCHING, 這是一個旗標, 指出容器是否允許控制項在控制項的使用者介面為作用中時, 以影線圖樣顯示其本身。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>參數

*bShowHatching*<br/>
屬性 DISPID_AMBIENT_SHOWHATCHING。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

抓取 DISPID_AMBIENT_SUPPORTSMNEMONICS, 此旗標表示容器是否支援鍵盤助憶鍵。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>參數

*bSupportsMnemonics*<br/>
屬性 DISPID_AMBIENT_SUPPORTSMNEMONICS。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

抓取 DISPID_AMBIENT_TEXTALIGN, 這是容器慣用的文字對齊方式:0代表一般對齊 (數位 right、靠左文字)、1代表左對齊、2表示置中對齊, 而3用於右對齊。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>參數

*nTextAlign*<br/>
屬性 DISPID_AMBIENT_TEXTALIGN。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

抓取 DISPID_AMBIENT_TOPTOBOTTOM, 這是容器顯示內容的方向。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>參數

*bTopToBottom*<br/>
屬性 DISPID_AMBIENT_TOPTOBOTTOM。 如果文字是從上到下顯示, 則設定為 TRUE, 如果顯示在下方, 則設為 FALSE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

抓取 DISPID_AMBIENT_UIDEAD, 這是一個旗標, 指出容器是否希望控制項回應使用者介面動作。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>參數

*bUIDead*<br/>
屬性 DISPID_AMBIENT_UIDEAD。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

若為 TRUE, 則控制項不應回應。 無論 DISPID_AMBIENT_USERMODE 旗標為何, 都適用此旗標。 請參閱[CComControlBase:: GetAmbientUserMode](#getambientusermode)。

##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

抓取 DISPID_AMBIENT_USERMODE, 此旗標表示容器處於執行模式 (TRUE) 或設計模式 (FALSE)。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>參數

*bUserMode*<br/>
屬性 DISPID_AMBIENT_USERMODE。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="getdirty"></a>CComControlBase::GetDirty

傳回資料成員`m_bRequiresSave`的值。

```
BOOL GetDirty();
```

### <a name="return-value"></a>傳回值

傳回資料成員[m_bRequiresSave](#m_brequiressave)的值。

### <a name="remarks"></a>備註

此值是使用[CComControlBase:: SetDirty](#setdirty)所設定。

##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo

抓取啟動進行就地編輯之控制項的顯示比例之分子和分母的 x 和 y 值。

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*di*<br/>
將保留縮放因數之分子和分母的結構。 如需詳細資訊, 請參閱[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。

### <a name="remarks"></a>備註

縮放因數是控制項的自然大小與目前範圍的比例。

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

使控制項從非使用中狀態轉換成*iVerb*中的動詞所指出的任何狀態。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指出要由 IOleObjectImpl 執行之動作的值[::D overb](../../atl/reference/ioleobjectimpl-class.md#doverb)。

*prcPosRect*<br/>
就地控制項位置的指標。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

在啟用之前, 這個方法會檢查控制項是否有用戶端網站、檢查有多少控制項可見, 以及取得控制項在父視窗中的位置。 控制項啟動之後, 這個方法會啟動控制項的使用者介面, 並告知容器讓控制項變成可見狀態。

這個方法`IOleInPlaceSite`也會抓取控制項`IOleInPlaceSiteEx`的、 `IOleInPlaceSiteWindowless`或介面指標, 並將它儲存在控制項類別的資料成員[CComControlBase:: m_spInPlaceSite](#m_spinplacesite)中。 控制項類別資料成員[CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex)、 [CComControlBase:: m_bWndLess](#m_bwndless)、 [CComControlBase:: M_bWasOnceWindowless](#m_bwasoncewindowless)和[CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd)會適當地設定為 true。

##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite

呼叫這個方法來查詢控制網站, 找出已識別介面的指標。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>參數

*riid*<br/>
應該在*ppUnkSite*中傳回之介面指標的 IID。

*ppUnkSite*<br/>
指標變數的位址, 它會接收在*riid*中要求的介面指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果網站支援*riid*中要求的介面, 則指標會透過*ppUnkSite*傳回。 否則, *ppUnkSite*會設定為 Null。

##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize

表示控制項不能是任何其他大小的旗標。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>備註

這個旗標是由`IOleObjectImpl::SetExtent`所檢查, 如果為 TRUE, 則會導致函數傳回 E_FAIL。

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

如果您在 ATL 控制項 Wizard 的 [內建[屬性](../../atl/reference/stock-properties-atl-control-wizard.md)] 索引標籤上加入 [**自動大小**] 選項, 則 Wizard 會在控制項類別中自動建立這個資料成員、建立屬性的 put 和 get 方法, 並支援[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)當屬性變更時, 自動通知容器。

##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

旗標, `IDataObjectImpl::GetData`表示`CComControlBase::GetZoomInfo`和應該從`m_sizeNatural`設定控制項大小, 而不`m_sizeExtent`是來自。

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

旗標, `IDataObjectImpl::GetData`指出繪製時應該使用 HIMETRIC 單位, 而不是圖元。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>備註

每個邏輯 HIMETRIC 單位為0.01 毫米。

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

表示控制項為就地作用中的旗標。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>備註

這表示控制項可見, 而且其視窗 (如果有的話) 可見, 但其功能表和工具列可能不在作用中。 `m_bUIActive`旗標表示控制項的使用者介面 (例如功能表) 也是使用中。

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

表示容器支援介面和 OCX96 `IOleInPlaceSiteEx`控制功能的旗標, 例如無視窗和無閃爍的控制項。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

資料成員`m_spInPlaceSite`會指向[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess`介面, 視和旗標的值而`m_bInPlaceSiteEx`定。 (資料成員`m_bNegotiatedWnd`必須為 TRUE `m_spInPlaceSite` , 指標才會是有效的)。

如果`m_bWndLess`為 FALSE 且`m_bInPlaceSiteEx` 為TRUE`m_spInPlaceSite` , 則為介面指標。`IOleInPlaceSiteEx` 如需顯示這三個資料成員之間關聯性的資料表, 請參閱[m_spInPlaceSite](#m_spinplacesite) 。

##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

表示控制項是否已與容器進行協商的旗標, 以支援 OCX96 控制項功能 (例如不閃爍和無視窗控制項), 以及控制項是否為視窗型或無視窗。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

旗標必須為 TRUE `m_spInPlaceSite` , 指標才會是有效的。 `m_bNegotiatedWnd`

##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

表示控制項想要在容器變更控制項的顯示大小時 recompose 其呈現的旗標。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

此旗標是由[IOleObjectImpl:: SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent)檢查, 如果為 TRUE `SetExtent` , 則會通知容器的視圖變更。 如果設定此旗標, 則也應該設定[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)列舉中的 OLEMISC_RECOMPOSEONRESIZE 位。

##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

表示控制項自上次儲存後已變更的旗標。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>備註

的值`m_bRequiresSave`可以使用[CComControlBase:: SetDirty](#setdirty)來設定, 並使用[CComControlBase:: GetDirty](#getdirty)來抓取。

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

旗標, 表示當容器變更控制項的顯示大小時, 控制項想要調整其自然範圍的大小 (其未縮放的實體大小)。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>備註

這個旗標是由`IOleObjectImpl::SetExtent`所檢查, 如果為 TRUE, 則`SetExtent`會將傳入的`m_sizeNatural`大小指派給。

不論的值為何`SetExtent` `m_sizeExtent`, 傳遞至的大小一律會指派給。 `m_bResizeNatural`

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive

表示控制項的使用者介面 (例如功能表和工具列) 為使用中的旗標。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>備註

`m_bInPlaceActive`旗標表示控制項為使用中, 但不是其使用者介面為使用中。

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

表示控制項正在使用容器提供的視窗區域的旗標。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless

表示控制項已為無視窗的旗標, 但現在不一定是無視窗的。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

表示控制項應為視窗型的旗標, 即使容器支援無視窗控制項也一樣。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess

表示控制項為無視窗的旗標。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

資料`m_spInPlaceSite`成員會指向[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess`介面, 視和[CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex)旗標的值而定。 (資料成員[CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd)必須為 TRUE, [CComControlBase:: m_spInPlaceSite](#m_spinplacesite)指標才會是有效的)。

如果`m_bWndLess`為 TRUE, `m_spInPlaceSite`則為`IOleInPlaceSiteWindowless`介面指標。 如需顯示這些資料成員之間完整關聯性的資料表, 請參閱[CComControlBase:: m_spInPlaceSite](#m_spinplacesite) 。

##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD

包含與控制項相關聯之視窗控制碼的參考。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

容器具有凍結事件的次數計數 (拒絕接受事件), 而不會有事件的中途解除凍結 (接受事件)。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_rcpos"></a>CComControlBase::m_rcPos

控制項的位置 (以圖元為單位), 以容器的座標表示。

```
RECT m_rcPos;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

特定顯示器的 HIMETRIC 單位 (每個單位為0.01 毫米) 控制項的範圍。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

此大小會依顯示星號調整。 控制項的實體大小是在`m_sizeNatural`資料成員中指定, 而且是固定的。

您可以使用全域函數[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel), 將大小轉換成圖元。

##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

控制項在 HIMETRIC 單位中的實體大小 (每個單位為0.01 毫米)。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

這種大小是固定的, 而中`m_sizeExtent`的大小則是由顯示星號調整。

您可以使用全域函數[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel), 將大小轉換成圖元。

##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

容器 (容器的[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)) 上諮詢連接的直接指標。

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

物件, 可讓您`IDispatch`透過指標來抓取和設定物件的屬性。 `CComDispatchDriver`

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite

容器內控制項之用戶端網站的指標。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

提供標準方法來保存資料物件與建議接收之間的諮詢連接。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

資料物件是可以傳送資料並執行[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的控制項, 其方法會指定資料的格式和傳送媒體。

介面`m_spDataAdviseHolder`會[執行 IDataObject::D advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise)和[IDataObject::D unadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise)方法, 以建立和刪除容器的諮詢連接。 控制項的容器必須藉由支援[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面來實作為建議的接收。

##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

容器的[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面指標的指標。

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

只有`m_spInPlaceSite`在[m_bNegotiatedWnd](#m_bnegotiatedwnd)旗標為 TRUE 時, 指標才有效。

下表顯示`m_spInPlaceSite`指標類型如何取決於[m_bWndLess](#m_bwndless)和[m_bInPlaceSiteEx](#m_binplacesiteex)資料成員旗標:

|m_spInPlaceSite Type|m_bWndLess 值|m_bInPlaceSiteEx 值|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|true|TRUE 或 FALSE|
|`IOleInPlaceSiteEx`|false|true|
|`IOleInPlaceSite`|false|false|

##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

提供一種標準的執行方式來保存諮詢連接。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  若要在控制項類別中使用這個資料成員, 您必須將它宣告為控制項類別中的資料成員。 您的控制項類別不會從基類繼承這個資料成員, 因為它是在基類的聯集內宣告的。

介面`m_spOleAdviseHolder`會[執行 IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise)和[IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise)方法, 以建立和刪除容器的諮詢連接。 控制項的容器必須藉由支援[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面來實作為建議的接收。

##  <a name="ondraw"></a>CComControlBase:: OnDraw

覆寫此方法以繪製您的控制項。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*di*<br/>
[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)結構的參考, 其中包含繪圖資訊, 例如繪製外觀、控制項範圍, 以及繪圖是否已優化。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

預設`OnDraw`會刪除或還原裝置內容, 或不執行任何動作, 視[CComControlBase:: OnDrawAdvanced](#ondrawadvanced)中設定的旗標而定。

當您使用 ATL 控制項嚮導來建立控制項時,方法會自動加入至您的控制項類別。`OnDraw` Wizard 的預設`OnDraw`會繪製一個具有 "ATL 8.0" 標籤的矩形。

### <a name="example"></a>範例

請參閱[CComControlBase:: GetAmbientAppearance](#getambientappearance)的範例。

##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

預設`OnDrawAdvanced`會準備正規化的裝置內容以進行繪製, 然後呼叫控制項類別的`OnDraw`方法。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*di*<br/>
[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)結構的參考, 其中包含繪圖資訊, 例如繪製外觀、控制項範圍, 以及繪圖是否已優化。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果您想要接受容器所傳遞的裝置內容, 而不將它正規化, 請覆寫此方法。

如需詳細資訊, 請參閱[CComControlBase:: OnDraw](#ondraw) 。

##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus

檢查控制項是否為就地作用並具有有效的控制網站, 然後通知容器控制項已失去焦點。

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
指出是否已成功處理視窗訊息的旗標。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

一律傳回1。

##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

檢查 UI 是否處於使用者模式, 然後啟用控制項。

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
指出是否已成功處理視窗訊息的旗標。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

一律傳回1。

##  <a name="onpaint"></a>CComControlBase:: OnPaint

準備用於繪製的容器, 取得控制項的工作區, 然後呼叫控制項類別的`OnDrawAdvanced`方法。

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

一律傳回零。

### <a name="remarks"></a>備註

如果*wParam*不是 Null, `OnPaint`則會假設它包含有效的 HDC 並使用它, 而不是[CComControlBase:: m_hWndCD](#m_hwndcd)。

##  <a name="onsetfocus"></a>CComControlBase::OnSetFocus

檢查控制項是否為就地作用並具有有效的控制網站, 然後通知容器控制項已取得焦點。

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
指出是否已成功處理視窗訊息的旗標。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

一律傳回1。

### <a name="remarks"></a>備註

將通知傳送至控制項已收到焦點的容器。

##  <a name="pretranslateaccelerator"></a>CComControlBase::P reTranslateAccelerator

覆寫這個方法, 以提供您自己的鍵盤快速鍵處理常式。

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

根據預設, 會傳回 FALSE。

##  <a name="sendonclose"></a>CComControlBase::SendOnClose

通知已向通知持有者註冊控制項已關閉的所有諮詢接收器。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

傳送控制項已關閉其諮詢接收的通知。

##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange

通知所有向通知持有者註冊的通知接收, 控制項資料已變更。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>參數

*advf*<br/>
指定呼叫[IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange)之方式的建議旗標。 值來自[ADVF](/windows/win32/api/objidl/ne-objidl-advf)列舉。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="sendonrename"></a>CComControlBase::SendOnRename

通知已向通知持有者註冊的所有諮詢接收器, 控制項都有新的名字標記。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>參數

*pmk*<br/>
控制項之新標記的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

傳送控制項的標記已變更的通知。

##  <a name="sendonsave"></a>CComControlBase::SendOnSave

通知所有向通知持有者註冊的通知接收器已儲存控制項。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

傳送控制項剛儲存其資料的通知。

##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

通知所有已註冊的通知接收, 控制項的 view 已變更。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>參數

*dwAspect*<br/>
控制項的外觀或觀點。

*lindex*<br/>
已變更的視圖部分。 只有-1 是有效的。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

`SendOnViewChange`呼叫[IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange)。 目前僅支援*lindex*的值為-1, 表示整個視圖都是相關的。

##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

設定或移除控制項的鍵盤焦點。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>參數

*bGrab*<br/>
若為 TRUE, 則會將鍵盤焦點設定為呼叫控制項。 若為 FALSE, 則會從呼叫控制項移除鍵盤焦點, 但前提是它有焦點。

### <a name="return-value"></a>傳回值

如果控制項成功接收焦點, 則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

針對視窗型控制項, 會呼叫 Windows API 函數[SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) 。 若為無視窗控制項, 則會呼叫[IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) 。 透過這個呼叫, 無視窗控制項會取得鍵盤焦點, 而且可以回應視窗訊息。

##  <a name="setdirty"></a>CComControlBase::SetDirty

將資料成員`m_bRequiresSave`設定為*bDirty*中的值。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>參數

*bDirty*<br/>
資料成員[CComControlBase:: m_bRequiresSave](#m_brequiressave)的值。

### <a name="remarks"></a>備註

`SetDirty(TRUE)`應呼叫以旗標, 表示控制項自上次儲存後已變更。 的值是`m_bRequiresSave`使用[CComControlBase:: GetDirty](#getdirty)來取得。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
