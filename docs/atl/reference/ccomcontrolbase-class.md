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
ms.openlocfilehash: 2420e1643444e6cbbf8edff90bbd3ecb1eac8534
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320780"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 類別

此類提供用於創建和管理 ATL 控制項的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CCom 控制庫:外觀類型](#appearancetype)|如果`m_nAppearance`股票屬性不是**短**型,請覆蓋。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom控制庫:CCom控制庫](#ccomcontrolbase)|建構函式。|
|[CCom 控制庫:*CCom控制庫](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 控制庫::控制查詢介面](#controlqueryinterface)|擷取所要求介面的指標。|
|[CComControlBase::DesVerb啟動](#doesverbactivate)|檢查`IOleObjectImpl::DoVerb`所使用的*iVerb*參數是否啟動控制項的使用者介面 *(iVerb*等於OLEIVERB_UIACTIVATE),定義使用者雙擊控制項時執行的操作 *(iVerb*等於OLEIVERB_PRIMARY)、顯示控制項 *(iVerb*等於OLEIVERB_SHOW)或啟動控制件 *(iVerb*等於OLEIVERB_INPLACEACTIVATE)。|
|[CComControlBase::DesVerbUI啟動](#doesverbuiactivate)|檢查 所`IOleObjectImpl::DoVerb`使用的*iVerb*參數是否導致控制項的使用者介面啟動並返回 TRUE。|
|[CComControlBase::DoVerb屬性](#doverbproperties)|顯示控制項的屬性頁。|
|[CCom 控制庫::火檢視更改](#fireviewchange)|調用此方法告訴容器重新繪製控制項,或通知已註冊的通知接收器控制項的檢視已更改。|
|[CComControlBase:抓取環境外觀](#getambientappearance)|檢索DISPID_AMBIENT_APPEARANCE,控件的當前外觀設置為:0 表示平面,1 表示 3D。|
|[CCom 控制庫:抓取環境自動剪輯](#getambientautoclip)|檢索DISPID_AMBIENT_AUTOCLIP,指示容器是否支援自動剪切控件顯示區域的標誌。|
|[CCom 控制庫:抓取環境背面顏色](#getambientbackcolor)|檢索DISPID_AMBIENT_BACKCOLOR,即容器定義的所有控制項的環境背景顏色。|
|[CComControlBase:抓取環境字元集](#getambientcharset)|檢索DISPID_AMBIENT_CHARSET,即由容器定義的所有控制件的環境字元集。|
|[CCom 控制庫:抓取環境碼頁](#getambientcodepage)|檢索DISPID_AMBIENT_CODEPAGE,即由容器定義的所有控制項的環境字元集。|
|[CCom 控制庫:抓取環境顯示為預設](#getambientdisplayasdefault)|檢索DISPID_AMBIENT_DISPLAYASDEFAULT,如果容器將此網站中的控件標記為默認按鈕,則該標誌為 TRUE,因此按鈕控制項應使用較粗的框架繪製自身。|
|[CCom 控制庫:抓取環境顯示名稱](#getambientdisplayname)|檢索DISPID_AMBIENT_DISPLAYNAME,容器提供給控制項名稱。|
|[CComControlBase:抓取環境字型](#getambientfont)|檢索指向容器環境`IFont`介面的指標。|
|[CComControlBase:抓取環境方迪普](#getambientfontdisp)|檢索指向容器的環境`IFontDisp`調度介面的指標。|
|[CComControlBase:抓取環境福彩](#getambientforecolor)|檢索DISPID_AMBIENT_FORECOLOR,即容器定義的所有控制項的環境前景顏色。|
|[CComControlBase:抓取環境區域ID](#getambientlocaleid)|檢索容器使用的語言的DISPID_AMBIENT_LOCALEID標識符。|
|[CComControlBase:抓取環境資訊反射](#getambientmessagereflect)|檢索DISPID_AMBIENT_MESSAGEREFLECT,一個指示容器是否要接收視窗消息(如WM_DRAWITEM)作為事件的標誌。|
|[CCom 控制庫:抓取環境調色板](#getambientpalette)|檢索用於訪問容器的HPALETTE的DISPID_AMBIENT_PALETTE。|
|[CComControlBase:抓取環境屬性](#getambientproperty)|檢索*id*指定的容器屬性。|
|[CCom 控制庫:抓取環境右到左方](#getambientrighttoleft)|檢索DISPID_AMBIENT_RIGHTTOLEFT,容器顯示內容的方向。|
|[CCom 控制庫:抓取環境規模單位](#getambientscaleunits)|檢索DISPID_AMBIENT_SCALEUNITS,容器的環境單位(如英寸或釐米)用於標記顯示。|
|[CCom 控制庫:抓取環境](#getambientshowgrabhandles)|檢索DISPID_AMBIENT_SHOWGRABHANDLES,一個標誌指示容器是否允許控件在活動時顯示自身的抓取控點。|
|[CCom 控制庫:抓取環境顯示填滿](#getambientshowhatching)|檢索DISPID_AMBIENT_SHOWHATCHING,一個標誌,指示容器是否允許控件在 UI 處於活動狀態時使用陰影模式顯示自身。|
|[CComControlBase:取得環境支援Mnemonic](#getambientsupportsmnemonics)|檢索DISPID_AMBIENT_SUPPORTSMNEMONICS,一個指示容器是否支援鍵盤助記符的標誌。|
|[CComControlBase:抓取環境文字對齊](#getambienttextalign)|檢索DISPID_AMBIENT_TEXTALIGN、容器首選的文本對齊:0 表示一般對齊(數字右側,文本左側),左對齊為 1,中心對齊為 2,右對齊為 3。|
|[CCom 控制庫:抓取環境頂底](#getambienttoptobottom)|檢索DISPID_AMBIENT_TOPTOBOTTOM,容器顯示內容的方向。|
|[CComControlBase:抓取環境UI死](#getambientuidead)|檢索DISPID_AMBIENT_UIDEAD,指示容器是否希望控件回應使用者介面操作的標誌。|
|[CCom 控制庫:抓取環境使用者模式](#getambientusermode)|檢索DISPID_AMBIENT_USERMODE,指示容器處於運行模式 (TRUE) 還是設計模式 (FALSE) 的標誌。|
|[CComControlBase:取得髒](#getdirty)|返回數據成員`m_bRequiresSave`的值。|
|[CComControlBase:取得Zoominfo](#getzoominfo)|檢索為就地編輯而啟動的控制件的縮放因數的分子和分母的 x 和 y 值。|
|[CCom 控制庫:就地啟動](#inplaceactivate)|使控制項從非活動狀態轉換為*iVerb*中動詞指示的任何狀態。|
|[CComControlBase:內部取得網站](#internalgetsite)|調用此方法以查詢控制項網站以尋找指向已標識介面的指標。|
|[CComControlBase:ONDraw](#ondraw)|重寫此方法以繪製控制件。|
|[CComControlBase:OnDraw高級](#ondrawadvanced)|默認值`OnDrawAdvanced`為繪圖準備規範化的設備上下文,然後調用控制項`OnDraw`類的方法。|
|[CComControlBase::在基爾焦點上](#onkillfocus)|檢查控件是否就地處於活動狀態,並且具有有效的控制網站,然後通知容器控件已失去焦點。|
|[CComControlBase:滑鼠啟動](#onmouseactivate)|檢查 UI 是否處於使用者模式,然後啟動控制件。|
|[CComControlBase::上漆](#onpaint)|準備容器進行繪製,獲取控制項的工作區,然後調用控制項類`OnDraw`的方法。|
|[CComControlBase:關於焦點](#onsetfocus)|檢查控件是否就地處於活動狀態,並且具有有效的控制網站,然後通知容器控件已獲得焦點。|
|[CComControlBase::P重新翻譯加速器](#pretranslateaccelerator)|重寫此方法以提供您自己的鍵盤快捷鍵處理程式。|
|[CCom 控制庫::傳送關閉](#sendonclose)|通知在通知持有人登記的所有通知接收器,該控制已關閉。|
|[CCom 控制庫::傳送資料變更](#sendondatachange)|通知向通知持有人註冊的所有通知接收器控制數據已更改。|
|[CCom 控制庫::傳送重新命名](#sendonrename)|通知所有在通知持有人登記的諮詢接收器,該控制具有新的名字。|
|[CCom 控制庫:寄送儲存](#sendonsave)|通知向通知持有人登記的所有通知接收器,該控制已保存。|
|[CCom 控制庫::寄送檢視變更](#sendonviewchange)|通知所有已註冊的通知接收器控制項的檢視已更改。|
|[CCom 控制庫:設定控制焦點](#setcontrolfocus)|設置或移除鍵盤對焦到控件或從控制項。|
|[CCom 控制庫::設定髒](#setdirty)|將數據成員`m_bRequiresSave`設置為*bDirty*中的值。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComControlBase:m_bAutoSize](#m_bautosize)|指示控制的標誌不能是任何其他大小。|
|[CComControlBase:m_bDrawFromNatural](#m_bdrawfromnatural)|指示和`IDataObjectImpl::GetData``CComControlBase::GetZoomInfo`應從 而不是`m_sizeNatural``m_sizeExtent`從設置控制項大小的標誌。|
|[CCom控制庫:m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|指示繪製時`IDataObjectImpl::GetData`應使用 HIMETRIC 單位而不是像素的標誌。|
|[CComControlBase:m_bInPlaceActive](#m_binplaceactive)|指示控件已就地處於活動狀態的標誌。|
|[CComControlBase:m_bInPlaceSiteEx](#m_binplacesiteex)|指示容器的標誌支援`IOleInPlaceSiteEx`介面和 OCX96 控制功能,如無視窗和無閃爍控制元件。|
|[CCom 控制庫::m_bNegotiatedWnd](#m_bnegotiatedwnd)|指示控件是否已與容器協商支援 OCX96 控制功能(如無閃爍和無視窗控制件)以及控制項是視窗還是無視窗。|
|[CComControlBase:m_bRecomposeOnResize](#m_brecomposeonresize)|指示控制項的標誌希望在容器更改控制項的顯示大小時重新調整其演示文稿。|
|[CComControlBase:m_bRequiresSave](#m_brequiressave)|指示控件自上次保存以來已更改的標誌。|
|[CComControlBase:m_bResizeNatural](#m_bresizenatural)|指示控制項的標誌希望在容器更改控制項的顯示大小時調整其自然範圍(其未縮放的物理大小)。|
|[CComControlBase:m_bUIActive](#m_buiactive)|指示控制使用者介面(如功能表和工具列)的標誌處於活動狀態。|
|[CCom 控制庫::m_bUsingWindowRgn](#m_busingwindowrgn)|指示控制項正在使用容器提供的視窗區域的標誌。|
|[CCom控制庫:m_bWasOnceWindowless](#m_bwasoncewindowless)|指示控件已無視窗的標誌,但現在可能已無視窗,也可能不是無視窗。|
|[CComControlBase:m_bWindowOnly](#m_bwindowonly)|指示控件的標誌應視窗,即使容器支援無視窗控制項也是如此。|
|[CComControlBase:m_bWndLess](#m_bwndless)|指示控件無窗口的標誌。|
|[CComControlBase:m_hWndCD](#m_hwndcd)|包含對與控制項關聯的視窗句柄的引用。|
|[CComControlBase:m_nFreezeEvents](#m_nfreezeevents)|計算容器凍結事件(拒絕接受事件)的次數,而不干預事件解凍(接受事件)。|
|[CComControlBase:m_rcPos](#m_rcpos)|控制件的圖元位置,以容器的座標表示。|
|[CComControlBase:m_sizeExtent](#m_sizeextent)|特定顯示器的控制範圍(以 HIMETRIC 單位為單位(每個單位為 0.01 毫米)。|
|[CComControlBase:m_sizeNatural](#m_sizenatural)|以 HIMETRIC 單位(每個單位為 0.01 毫米)的控制的物理大小。|
|[CComControlBase:m_spAdviseSink](#m_spadvisesink)|指向容器上的諮詢連接的直接指標(容器的[IAdviseSink)。](/windows/win32/api/objidl/nn-objidl-iadvisesink)|
|[CComControlBase:m_spAmbientDispatch](#m_spambientdispatch)|一`CComDispatchDriver`個物件,允許您通過`IDispatch`指標檢索和設置容器的屬性。|
|[CComControlBase:m_spClientSite](#m_spclientsite)|指向容器中控制件的用戶端網站的指標。|
|[CComControlBase:m_spDataAdviseHolder](#m_spdataadviseholder)|提供一種標準方法,用於在數據物件和通知接收器之間保持諮詢連接。|
|[CCom控制庫:m_spInPlaceSite](#m_spinplacesite)|指向容器的[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlace無視窗](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面指標的[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)指標。|
|[CComControlBase:m_spOleAdviseHolder](#m_spoleadviseholder)|提供保存諮詢連接的方法的標準實現。|

## <a name="remarks"></a>備註

此類提供用於創建和管理 ATL 控制項的方法。 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)的`CComControlBase`手生自 。 使用 ATL 控制件精靈建立標準控制項或 DHTML 控制件時,嚮導`CComControlBase`將自動從派生類。

有關建立控制項的詳細資訊,請參閱[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有關 ATL 專案精靈的詳細資訊,請參閱創建[ATL 專案](../../atl/reference/creating-an-atl-project.md)的文章。

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a>CCom 控制庫:外觀類型

如果`m_nAppearance`股票屬性不是**短**型,請覆蓋。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>備註

ATL 控制精靈添加`m_nAppearance`短型的股票屬性。 如果使用`AppearanceType`其他數據類型,則覆蓋。

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a>CCom控制庫:CCom控制庫

建構函式。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>參數

*H*<br/>
與控制項關聯的視窗的句柄。

### <a name="remarks"></a>備註

將控制大小初始化為 5080X5080 HIMETRIC 單位(2"X2"),並將`CComControlBase`資料成員值初始化為 NULL 或 FALSE。

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a>CCom 控制庫:*CCom控制庫

解構函式。

```
~CComControlBase();
```

### <a name="remarks"></a>備註

如果控件是視窗的,則`~CComControlBase`通過調用[「銷毀視窗」](/windows/win32/api/winuser/nf-winuser-destroywindow)來銷毀它。

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a>CCom 控制庫::控制查詢介面

擷取所要求介面的指標。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>參數

*Iid*<br/>
請求的介面的 GUID。

*Ppv*<br/>
指向*iid*識別的介面指標,如果找不到介面,則指向 NULL 的指標。

### <a name="remarks"></a>備註

僅處理 COM 地圖表中的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a>CComControlBase::DesVerb啟動

檢查`IOleObjectImpl::DoVerb`所使用的*iVerb*參數是否啟動控制項的使用者介面 *(iVerb*等於OLEIVERB_UIACTIVATE),定義使用者雙擊控制項時執行的操作 *(iVerb*等於OLEIVERB_PRIMARY)、顯示控制項 *(iVerb*等於OLEIVERB_SHOW)或啟動控制件 *(iVerb*等於OLEIVERB_INPLACEACTIVATE)。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指示要執行的操作`DoVerb`的值。

### <a name="return-value"></a>傳回值

如果*iVerb*等於OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或OLEIVERB_INPLACEACTIVATE,則返回 TRUE;否則,返回 FALSE。

### <a name="remarks"></a>備註

您可以重寫此方法來定義自己的激活謂詞。

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a>CComControlBase::DesVerbUI啟動

檢查 所`IOleObjectImpl::DoVerb`使用的*iVerb*參數是否導致控制項的使用者介面啟動並返回 TRUE。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指示要執行的操作`DoVerb`的值。

### <a name="return-value"></a>傳回值

如果*iVerb*等於OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或OLEIVERB_INPLACEACTIVATE,則返回 TRUE。 否則,該方法將返回 FALSE。

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a>CComControlBase::DoVerb屬性

顯示控制項的屬性頁。

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
已保留。

*hwnd 家長*<br/>
包含控制項的視窗的句柄。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a>CCom 控制庫::火檢視更改

調用此方法告訴容器重新繪製控制項,或通知已註冊的通知接收器控制項的檢視已更改。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

如果控件處於活動狀態(控制項類數據成員[CComControlBase::m_bInPlaceActive](#m_binplaceactive)為 TRUE),則通知要重繪整個控制項的容器。 如果控件處於非活動狀態,則通知控件的已註冊通知接收器(通過控件類數據成員[CComControlBase::m_spAdviseSink)](#m_spadvisesink)該控件的檢視已更改。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a>CComControlBase:抓取環境外觀

檢索DISPID_AMBIENT_APPEARANCE,控件的當前外觀設置為:0 表示平面,1 表示 3D。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>參數

*n 外觀*<br/>
該屬性DISPID_AMBIENT_APPEARANCE。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a>CCom 控制庫:抓取環境自動剪輯

檢索DISPID_AMBIENT_AUTOCLIP,指示容器是否支援自動剪切控件顯示區域的標誌。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>參數

*b 自動剪輯*<br/>
屬性DISPID_AMBIENT_AUTOCLIP。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a>CCom 控制庫:抓取環境背面顏色

檢索DISPID_AMBIENT_BACKCOLOR,即容器定義的所有控制項的環境背景顏色。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>參數

*BackColor*<br/>
該物業DISPID_AMBIENT_BACKCOLOR。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a>CComControlBase:抓取環境字元集

檢索DISPID_AMBIENT_CHARSET,即由容器定義的所有控制件的環境字元集。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>參數

*bstrCharSet*<br/>
屬性DISPID_AMBIENT_CHARSET。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a>CCom 控制庫:抓取環境碼頁

檢索DISPID_AMBIENT_CODEPAGE,即容器定義的所有控制件的環境代碼頁。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>參數

*ulCodepage*<br/>
該物業DISPID_AMBIENT_CODEPAGE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a>CCom 控制庫:抓取環境顯示為預設

檢索DISPID_AMBIENT_DISPLAYASDEFAULT,如果容器將此網站中的控件標記為默認按鈕,則該標誌為 TRUE,因此按鈕控制項應使用較粗的框架繪製自身。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>參數

*b 顯示預設*<br/>
屬性DISPID_AMBIENT_DISPLAYASDEFAULT。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a>CCom 控制庫:抓取環境顯示名稱

檢索DISPID_AMBIENT_DISPLAYNAME,容器提供給控制項名稱。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>參數

*bstrDisplay名稱*<br/>
該物業DISPID_AMBIENT_DISPLAYNAME。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a>CComControlBase:抓取環境字型

檢索指向容器環境`IFont`介面的指標。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
指向容器環境[IFont](/windows/win32/api/ocidl/nn-ocidl-ifont)介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

如果屬性為 NULL,則指標為 NULL。 如果指標不是 NULL,則調用方必須釋放指標。

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a>CComControlBase:抓取環境方迪普

檢索指向容器的環境`IFontDisp`調度介面的指標。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
指向容器的環境[IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp)調度介面的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果屬性為 NULL,則指標為 NULL。 如果指標不是 NULL,則調用方必須釋放指標。

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a>CComControlBase:抓取環境福彩

檢索DISPID_AMBIENT_FORECOLOR,即容器定義的所有控制項的環境前景顏色。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>參數

*前色*<br/>
該物業DISPID_AMBIENT_FORECOLOR。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a>CComControlBase:抓取環境區域ID

檢索容器使用的語言的DISPID_AMBIENT_LOCALEID標識符。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>參數

*lcid*<br/>
該物業DISPID_AMBIENT_LOCALEID。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

控制項可以使用此識別碼將其使用者介面調整到不同的語言。

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a>CComControlBase:抓取環境資訊反射

檢索DISPID_AMBIENT_MESSAGEREFLECT,一個指示容器是否要接收視窗消息(如`WM_DRAWITEM`)作為事件的標誌。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>參數

*b消息反射*<br/>
該物業DISPID_AMBIENT_MESSAGEREFLECT。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a>CCom 控制庫:抓取環境調色板

檢索用於訪問容器的HPALETTE的DISPID_AMBIENT_PALETTE。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>參數

*hPalette*<br/>
該物業DISPID_AMBIENT_PALETTE。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a>CComControlBase:抓取環境屬性

檢索*由 dispid*指定的容器屬性。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要檢索的容器屬性的標識符。

*無 功*<br/>
要接收屬性的變數。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

ATL 提供了一組協助程式函數來檢索特定屬性,例如[CComControlBase::取得環境傳回顏色](#getambientbackcolor)。 如果沒有合適的方法可用,請使用`GetAmbientProperty`。

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a>CCom 控制庫:抓取環境右到左方

檢索DISPID_AMBIENT_RIGHTTOLEFT,容器顯示內容的方向。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>參數

*bRighttoLeft*<br/>
該屬性DISPID_AMBIENT_RIGHTTOLEFT。 如果內容從右向左顯示,則設置為 TRUE;如果內容從左到右顯示,則為 FALSE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a>CCom 控制庫:抓取環境規模單位

檢索DISPID_AMBIENT_SCALEUNITS,容器的環境單位(如英寸或釐米)用於標記顯示。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>參數

*bstrScale 單位*<br/>
該物業DISPID_AMBIENT_SCALEUNITS。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a>CCom 控制庫:抓取環境

檢索DISPID_AMBIENT_SHOWGRABHANDLES,一個標誌指示容器是否允許控件在活動時顯示自身的抓取控點。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>參數

*b 顯示GrabHandles*<br/>
該物業DISPID_AMBIENT_SHOWGRABHANDLES。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a>CCom 控制庫:抓取環境顯示填滿

檢索DISPID_AMBIENT_SHOWHATCHING,一個標誌,指示容器是否允許控件在控件的使用者介面處於活動狀態時使用陰影模式顯示自身。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>參數

*b 顯示填滿*<br/>
屬性DISPID_AMBIENT_SHOWHATCHING。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a>CComControlBase:取得環境支援Mnemonic

檢索DISPID_AMBIENT_SUPPORTSMNEMONICS,一個指示容器是否支援鍵盤助記符的標誌。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>參數

*b 支援Mnemonics*<br/>
該屬性DISPID_AMBIENT_SUPPORTSMNEMONICS。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a>CComControlBase:抓取環境文字對齊

檢索DISPID_AMBIENT_TEXTALIGN、容器首選的文本對齊:0 表示一般對齊(數字右側,文本左側),左對齊為 1,中心對齊為 2,右對齊為 3。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>參數

*n文字對齊*<br/>
屬性DISPID_AMBIENT_TEXTALIGN。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a>CCom 控制庫:抓取環境頂底

檢索DISPID_AMBIENT_TOPTOBOTTOM,容器顯示內容的方向。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>參數

*bTopto 底部*<br/>
房產DISPID_AMBIENT_TOPTOBOTTOM。 如果文本從上到下顯示,則設置為 TRUE;如果文本從下顯示到頂部,則 FALSE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a>CComControlBase:抓取環境UI死

檢索DISPID_AMBIENT_UIDEAD,指示容器是否希望控件回應使用者介面操作的標誌。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>參數

*bUIDead*<br/>
該酒店DISPID_AMBIENT_UIDEAD。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

如果為 TRUE,則控件不應回應。 此標誌適用於DISPID_AMBIENT_USERMODE標誌。 請參考[CComControlBase:取得環境使用者模式](#getambientusermode)。

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a>CCom 控制庫:抓取環境使用者模式

檢索DISPID_AMBIENT_USERMODE,指示容器處於運行模式 (TRUE) 還是設計模式 (FALSE) 的標誌。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>參數

*使用者模式*<br/>
屬性DISPID_AMBIENT_USERMODE。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a>CComControlBase:取得髒

返回數據成員`m_bRequiresSave`的值。

```
BOOL GetDirty();
```

### <a name="return-value"></a>傳回值

返回數據成員[m_bRequiresSave](#m_brequiressave)的值。

### <a name="remarks"></a>備註

這個值使用[CComControlBase 設定::設定髒話](#setdirty)。

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a>CComControlBase:取得Zoominfo

檢索為就地編輯而啟動的控制件的縮放因數的分子和分母的 x 和 y 值。

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*地*<br/>
保存縮放因數的分子和分母的結構。 有關詳細資訊,請參閱[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。

### <a name="remarks"></a>備註

縮放係數是控制的自然大小與其當前範圍的比例。

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a>CCom 控制庫:就地啟動

使控制項從非活動狀態轉換為*iVerb*中動詞指示的任何狀態。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指示[IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)) 要執行的操作的值。

*prcPosRect*<br/>
指向就地控制件的位置的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

在啟動之前,此方法檢查控件是否具有用戶端網站,檢查控件的可見量,並在父視窗中獲取控制項的位置。 啟動控制項後,此方法將啟動控制件的使用者介面,並告訴容器使控制項可見。

此方法還檢索控制件的`IOleInPlaceSite`,`IOleInPlaceSiteEx``IOleInPlaceSiteWindowless`或介面指標,並將其儲存在控制項類別的資料成員[CComControlBase:m_spInPlaceSite](#m_spinplacesite)。 控制類數據成員 CComControlBase::m_bInPlaceSiteEx、CComControlBase:m_bWndLess、CComControlBase::m_bWasOnceWindowless 和[CComControlBase:m_bNegotiatedWnd](#m_bnegotiatedwnd)根據需要[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)[CComControlBase::m_bWndLess](#m_bwndless)[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)設置為 true。

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a>CComControlBase:內部取得網站

調用此方法以查詢控制項網站以尋找指向已標識介面的指標。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>參數

*riid*<br/>
應在*ppUnkSite*中傳回的介面指標的 IID。

*ppUnkSite*<br/>
接收*riid*中請求的介面指標的指標變數的位址。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果網站支援*riid*中請求的介面,則指標將透過*ppUnkSite*返回。 否則 *,ppUnkSite*設置為 NULL。

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a>CComControlBase:m_bAutoSize

指示控制的標誌不能是任何其他大小。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>備註

此標誌由`IOleObjectImpl::SetExtent`和(如果 TRUE)檢查,則會導致函數返回E_FAIL。

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

如果在 ATL 控制件精靈[的「庫存屬性](../../atl/reference/stock-properties-atl-control-wizard.md)」選項卡上添加 **「自動大小**」選項,精靈將自動在控制項類別中創建此資料成員,為屬性創建 put 和 get 方法,並支援[IProperty NotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)在屬性更改時自動通知容器。

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a>CComControlBase:m_bDrawFromNatural

指示和`IDataObjectImpl::GetData``CComControlBase::GetZoomInfo`應從 而不是`m_sizeNatural``m_sizeExtent`從設置控制項大小的標誌。

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a>CCom控制庫:m_bDrawGetDataInHimetric

指示繪製時`IDataObjectImpl::GetData`應使用 HIMETRIC 單位而不是像素的標誌。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>備註

每個邏輯 HIMETRIC 單位為 0.01 毫米。

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a>CComControlBase:m_bInPlaceActive

指示控件已就地處於活動狀態的標誌。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>備註

這意味著控件是可見的,並且其視窗(如果有)可見,但其菜單和工具列可能不處於活動狀態。 該`m_bUIActive`標誌指示控件的使用者介面(如功能表)也處於活動狀態。

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a>CComControlBase:m_bInPlaceSiteEx

指示容器的標誌支援`IOleInPlaceSiteEx`介面和 OCX96 控制功能,如無視窗和無閃爍控制元件。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

`m_spInPlaceSite`數據成員指向[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlaceSite 無視窗](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)`m_bInPlaceSiteEx`介面,具體取決於[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)`m_bWndLess`和標誌的值。 (資料成員`m_bNegotiatedWnd`必須為`m_spInPlaceSite`TRUE, 指標才能有效。

如果`m_bWndLess`FALSE`m_bInPlaceSiteEx`為`m_spInPlaceSite``IOleInPlaceSiteEx`TRUE, 則為介面指標。 有關顯示這三個數據成員之間關係的表,請參閱[m_spInPlaceSite。](#m_spinplacesite)

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a>CCom 控制庫::m_bNegotiatedWnd

指示控件是否已與容器協商支援 OCX96 控制功能(如無閃爍和無視窗控制件)以及控制項是視窗還是無視窗。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

該`m_bNegotiatedWnd`標誌必須為`m_spInPlaceSite`TRUE, 指標才能有效。

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a>CComControlBase:m_bRecomposeOnResize

指示控制項的標誌希望在容器更改控制項的顯示大小時重新調整其演示文稿。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

此標誌由[IOleObjectImpl::SetAndina](../../atl/reference/ioleobjectimpl-class.md#setextent)檢查`SetExtent`,如果 為 TRUE,則通知容器的視圖更改。 如果設置了此標誌,也應設置[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)枚舉中的OLEMISC_RECOMPOSEONRESIZE位。

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a>CComControlBase:m_bRequiresSave

指示控件自上次保存以來已更改的標誌。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>備註

的值`m_bRequiresSave`可以使用[CComControlBase 設置:設定髒,](#setdirty)並檢索[CComControlBase::獲取髒。](#getdirty)

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a>CComControlBase:m_bResizeNatural

指示控制項的標誌希望在容器更改控制項的顯示大小時調整其自然範圍(其未縮放的物理大小)。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>備註

這個旗標由`IOleObjectImpl::SetExtent`與 (如果 TRUE)檢查,`SetExtent`則傳入的大小`m_sizeNatural`將分配給 。

傳入`SetExtent`的大小始終分配`m_sizeExtent`給 ,而不考慮`m_bResizeNatural`的值。

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a>CComControlBase:m_bUIActive

指示控制使用者介面(如功能表和工具列)的標誌處於活動狀態。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>備註

該`m_bInPlaceActive`標誌指示控件處於活動狀態,但指示其使用者介面處於活動狀態。

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a>CCom 控制庫::m_bUsingWindowRgn

指示控制項正在使用容器提供的視窗區域的標誌。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a>CCom控制庫:m_bWasOnceWindowless

指示控件已無視窗的標誌,但現在可能已無視窗,也可能不是無視窗。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a>CComControlBase:m_bWindowOnly

指示控件的標誌應視窗,即使容器支援無視窗控制項也是如此。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a>CComControlBase:m_bWndLess

指示控件無窗口的標誌。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

`m_spInPlaceSite`數據成員指向[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlaceSite 無視窗](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面,具體取決於`m_bWndLess`和[CComControlBase:m_bInPlaceSiteEx](#m_binplacesiteex)標誌的值。 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex) (數據成員[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)必須為[TRUE,CComControlBase::m_spInPlaceSite](#m_spinplacesite)指標才能有效。

如果`m_bWndLess`為`m_spInPlaceSite`TRUE,`IOleInPlaceSiteWindowless`則是介面指標。 有關顯示這些數據成員之間完整關係的表,請參閱[CComControlBase::m_spInPlaceSite。](#m_spinplacesite)

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a>CComControlBase:m_hWndCD

包含對與控制項關聯的視窗句柄的引用。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a>CComControlBase:m_nFreezeEvents

計算容器凍結事件(拒絕接受事件)的次數,而不干預事件解凍(接受事件)。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a>CComControlBase:m_rcPos

控制件的圖元位置,以容器的座標表示。

```
RECT m_rcPos;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a>CComControlBase:m_sizeExtent

特定顯示器的控制範圍(以 HIMETRIC 單位為單位(每個單位為 0.01 毫米)。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

此大小由顯示屏縮放。 控制項物理大小在資料成員中`m_sizeNatural`指定且固定。

您可以使用全域函數[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)將大小轉換為圖元。

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a>CComControlBase:m_sizeNatural

以 HIMETRIC 單位(每個單位為 0.01 毫米)的控制的物理大小。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

此大小是固定的,而`m_sizeExtent`中的大小由顯示屏縮放。

您可以使用全域函數[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)將大小轉換為圖元。

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a>CComControlBase:m_spAdviseSink

指向容器上的諮詢連接的直接指標(容器的[IAdviseSink)。](/windows/win32/api/objidl/nn-objidl-iadvisesink)

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a>CComControlBase:m_spAmbientDispatch

允許您`CComDispatchDriver``IDispatch`通過指標檢索和設置物件屬性的物件。

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a>CComControlBase:m_spClientSite

指向容器中控制件的用戶端網站的指標。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a>CComControlBase:m_spDataAdviseHolder

提供一種標準方法,用於在數據物件和通知接收器之間保持諮詢連接。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

數據物件是一種控制項,可以傳輸資料並實現[IDataObject,](/windows/win32/api/objidl/nn-objidl-idataobject)其方法指定資料的格式和傳輸媒體。

該介面`m_spDataAdviseHolder`實現[IDataObject::D建議](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise)和[IDataObject::D建立](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise)和刪除容器的諮詢連接的不知情方法。 控制項容器必須透過支援[IAdvise Sink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面來實現通知接收器。

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a>CCom控制庫:m_spInPlaceSite

指向容器的[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlace無視窗](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)介面指標的[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)指標。

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

僅當`m_spInPlaceSite`[m_bNegotiatedWnd](#m_bnegotiatedwnd)標誌為 TRUE 時,指標才有效。

下表顯示了`m_spInPlaceSite`指標類型如何依賴於[m_bWndLess](#m_bwndless)和[m_bInPlaceSiteEx](#m_binplacesiteex)資料成員標誌:

|m_spInPlaceSite類型|m_bWndLess值|m_bInPlaceSiteEx值|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|真或假|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a>CComControlBase:m_spOleAdviseHolder

提供保存諮詢連接的方法的標準實現。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>備註

> [!NOTE]
> 要在控件類中使用此數據成員,必須將其聲明為控制項類中的數據成員。 控件類不會從基類繼承此數據成員,因為它在基類中的聯合中聲明。

介面`m_spOleAdviseHolder`實現[IOleObject::建議](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise)和[IOleObject::取消建議](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise)方法來建立和刪除到容器的諮詢連接。 控制項容器必須透過支援[IAdvise Sink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面來實現通知接收器。

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a>CComControlBase:ONDraw

重寫此方法以繪製控制件。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*地*<br/>
對包含繪圖資訊(如繪製方面、控制邊界以及繪圖是否優化)[的ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)結構的引用。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

預設`OnDraw`刪除或還原裝置上下文或不執行任何操作,具體取決於[CComControlBase 中設定的標誌:onDrawAdvanced](#ondrawadvanced)。

使用`OnDraw`ATL 控制件精靈建立控制項時,方法將自動添加到控制項類別中。 嚮導的預設值`OnDraw`繪製一個帶有「ATL 8.0」標籤的矩形。

### <a name="example"></a>範例

請參考[CComControlBase 的範例:取得環境外觀](#getambientappearance)。

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a>CComControlBase:OnDraw高級

默認值`OnDrawAdvanced`為繪圖準備規範化的設備上下文,然後調用控制項`OnDraw`類的方法。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>參數

*地*<br/>
對包含繪圖資訊(如繪製方面、控制邊界以及繪圖是否優化)[的ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)結構的引用。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果要接受容器傳遞的設備上下文而不使其規範化,則重寫此方法。

有關詳細資訊[,請參閱 CComControlBase:OnDraw。](#ondraw)

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a>CComControlBase::在基爾焦點上

檢查控件是否就地處於活動狀態,並且具有有效的控制網站,然後通知容器控件已失去焦點。

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
已保留。

*wParam*<br/>
已保留。

*lParam*<br/>
已保留。

*bHandled*<br/>
指示視窗消息是否成功處理的標誌。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

始終返回 1。

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a>CComControlBase:滑鼠啟動

檢查 UI 是否處於使用者模式,然後啟動控制件。

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
已保留。

*wParam*<br/>
已保留。

*lParam*<br/>
已保留。

*bHandled*<br/>
指示視窗消息是否成功處理的標誌。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

始終返回 1。

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a>CComControlBase::上漆

準備容器進行繪製,獲取控制項的工作區,然後調用控制項類`OnDrawAdvanced`的方法。

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
已保留。

*wParam*<br/>
現有 HDC。

*lParam*<br/>
已保留。

*lResult*<br/>
已保留。

### <a name="return-value"></a>傳回值

永遠傳回零。

### <a name="remarks"></a>備註

如果*wParam*不是`OnPaint`NULL,則假定它包含有效的 HDC,並使用它而不是[CComControlBase::m_hWndCD](#m_hwndcd)。

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a>CComControlBase:關於焦點

檢查控件是否就地處於活動狀態,並且具有有效的控制網站,然後通知容器控件已獲得焦點。

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*nMsg*<br/>
已保留。

*wParam*<br/>
已保留。

*lParam*<br/>
已保留。

*bHandled*<br/>
指示視窗消息是否成功處理的標誌。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

始終返回 1。

### <a name="remarks"></a>備註

向容器發送控制件已收到焦點的通知。

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a>CComControlBase::P重新翻譯加速器

重寫此方法以提供您自己的鍵盤快捷鍵處理程式。

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
已保留。

*hRet*<br/>
已保留。

### <a name="return-value"></a>傳回值

默認情況下,返回 FALSE。

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a>CCom 控制庫::傳送關閉

通知在通知持有人登記的所有通知接收器,該控制已關閉。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

發送控制項已關閉通知接收器的通知。

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a>CCom 控制庫::傳送資料變更

通知向通知持有人註冊的所有通知接收器控制數據已更改。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>參數

*阿德夫夫*<br/>
建議指示如何呼叫[IAdviseSink::onDataChange 的標誌](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange)。 值來自[ADVF](/windows/win32/api/objidl/ne-objidl-advf)枚舉。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a>CCom 控制庫::傳送重新命名

通知所有在通知持有人登記的諮詢接收器,該控制具有新的名字。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>參數

*pmk*<br/>
指向控制項的新名字物件。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

發送控制項的綽號已更改的通知。

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a>CCom 控制庫:寄送儲存

通知向通知持有人登記的所有通知接收器,該控制已保存。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

發送控制項剛剛保存其資料的通知。

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a>CCom 控制庫::寄送檢視變更

通知所有已註冊的通知接收器控制項的檢視已更改。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>參數

*dwAspect*<br/>
控件的方面或視圖。

*利索引*<br/>
已經變更的檢視部分。 只有 -1 有效。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

`SendOnViewChange`呼叫[I 建議 Sink::開啟檢視變更](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange)。 當前支援的*lindex*的唯一值是 -1,這表明整個檢視是感興趣的。

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a>CCom 控制庫:設定控制焦點

設置或移除鍵盤對焦到控件或從控制項。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>參數

*bGrab*<br/>
如果為 TRUE,則將鍵盤焦點設置到呼叫控制項。 如果 FALSE,則從呼叫控件中刪除鍵盤焦點,前提是其具有焦點。

### <a name="return-value"></a>傳回值

如果控件成功接收焦點,則返回 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

對於視窗控制項,調用 Windows API 函數[SetFocus。](/windows/win32/api/winuser/nf-winuser-setfocus) 對於無視窗控制件[,IOleInPlaceSite無視窗::setFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus)調用。 通過此調用,無視窗控制項獲取鍵盤焦點並可以回應視窗訊息。

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a>CCom 控制庫::設定髒

將數據成員`m_bRequiresSave`設置為*bDirty*中的值。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>參數

*bDirty*<br/>
資料成員[CComControlBase 的值::m_bRequiresSave](#m_brequiressave)。

### <a name="remarks"></a>備註

`SetDirty(TRUE)`應調用 以標記控件自上次保存以來已更改。 的值`m_bRequiresSave`使用[CComControlBase 檢索::獲取髒。](#getdirty)

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
