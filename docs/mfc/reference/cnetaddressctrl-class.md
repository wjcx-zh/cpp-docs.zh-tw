---
title: CNetAddressCtrl 類別
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: 5e485c22bcc4bf35f61226d84345102052689f89
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "69504526"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl 類別

`CNetAddressCtrl` 類別表示網路位址控制項，您可以用來輸入和驗證 IPv4、IPv6 和具名 DNS 位址的格式。

## <a name="syntax"></a>語法

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|建構 `CNetAddressCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CNetAddressCtrl::Create](#create)|使用指定的樣式建立網路位址控制項，並將它附加至`CNetAddressCtrl`目前的物件。|
|[CNetAddressCtrl::CreateEx](#createex)|使用指定的擴充樣式建立網路位址控制項，並將它附加至`CNetAddressCtrl`目前的物件。|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|當使用者在目前的網路位址控制中輸入不支援的網路位址時，會顯示錯誤的氣球提示。|
|[CNetAddressCtrl::GetAddress](#getaddress)|抓取與目前網路位址控制相關聯之網路位址的已驗證和剖析標記法。|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|抓取目前網路位址控制可支援的網路位址類型。|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|設定目前網路位址控制可支援的網路位址類型。|

## <a name="remarks"></a>備註

網路位址控制會驗證使用者輸入的位址格式是否正確。 控制項實際上不會連接到網路位址。 [CNetAddressCtrl：： SetAllowType](#setallowtype)方法會指定[CNetAddressCtrl：： GetAddress](#getaddress)方法可以剖析和驗證的一或多個網址類別型。 位址的格式可以是 IPv4、IPv6，或是伺服器、網路、主機或廣播訊息目的地的已命名位址。 如果位址的格式不正確，您可以使用[CNetAddressCtrl：:D isplayerrortip](#displayerrortip)方法來顯示 [資訊提示] 訊息方塊，該方塊會以圖形方式指向網路位址控制項的文字方塊，並顯示預先定義的錯誤訊息。

類別衍生自 [CEdit 類別](../../mfc/reference/cedit-class.md)。`CNetAddressCtrl` 因此，網路位址控制會提供所有 Windows 編輯控制訊息的存取權。

下圖描述包含網路位址控制項的對話方塊。 網路位址控制項的文字方塊（1）包含不正確網路位址。 如果網路位址無效，則會顯示資訊提示訊息（2）。

![具有網路位址控制和提示的對話方塊。](../../mfc/reference/media/cnetaddctrl.png "具有網路位址控制和提示的對話方塊。")

## <a name="example"></a>範例

下列程式碼範例是驗證網路位址之對話方塊的一部分。 三個選項按鈕的事件處理常式會指定網路位址可以是三種地址類型的其中一種。 使用者會在網路控制項的文字方塊中輸入位址，然後按下按鈕以驗證位址。 如果位址有效，就會顯示成功訊息;否則，會顯示預先定義的資訊提示錯誤訊息。

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>範例

下列來自對話方塊標頭檔的程式碼範例會定義[CNetAddressCtrl：： GetAddress](#getaddress)方法所需的[NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address)和[NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)變數。

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

Windows Vista 和更新版本支援此類別。

如需此類別的其他需求，請參閱[Windows Vista 通用控制項的組建需求](../../mfc/build-requirements-for-windows-vista-common-controls.md)。

##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl

建構 `CNetAddressCtrl` 物件。

```
CNetAddressCtrl();
```

### <a name="remarks"></a>備註

使用[CNetAddressCtrl：： create](#create)或[CNetAddressCtrl：： CreateEx](#createex)方法來建立網路控制項，並將`CNetAddressCtrl`它附加至物件。

##  <a name="create"></a>  CNetAddressCtrl::Create

使用指定的樣式建立網路位址控制項，並將它附加至`CNetAddressCtrl`目前的物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*dwStyle*|在要套用至控制項之樣式的位元組合。 如需詳細資訊，請參閱[編輯樣式](../../mfc/reference/styles-used-by-mfc.md#edit-styles)。|
|*rect*|在[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考，其中包含控制項的位置和大小。|
|*pParentWnd*|在[CWnd](../../mfc/reference/cwnd-class.md)物件的非 null 指標，這是控制項的父視窗。|
|*nID*|在控制項的識別碼。|

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

##  <a name="createex"></a>  CNetAddressCtrl::CreateEx

使用指定的擴充樣式建立網路位址控制項，並將它附加至`CNetAddressCtrl`目前的物件。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwExStyle*|在要套用至控制項之擴充樣式的位元組合（或）。 如需詳細資訊，請參閱[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函數的*dwExStyle*參數。|
|*dwStyle*|在要套用至控制項之樣式的位元組合（OR）。 如需詳細資訊，請參閱[編輯樣式](../../mfc/reference/styles-used-by-mfc.md#edit-styles)。|
|*rect*|在[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考，其中包含控制項的位置和大小。|
|*pParentWnd*|在[CWnd](../../mfc/reference/cwnd-class.md)物件的非 null 指標，這是控制項的父視窗。|
|*nID*|在控制項的識別碼。|

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

##  <a name="displayerrortip"></a>CNetAddressCtrl：:D isplayErrorTip

在與目前網路位址控制項相關聯的氣球提示中，顯示錯誤訊息。

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>傳回值

如果此`S_OK`方法成功，則為值，否則為錯誤碼。

### <a name="remarks"></a>備註

使用[CNetAddressCtrl：： SetAllowType](#setallowtype)方法來指定目前的網路位址控制可支援的網址類別型。 使用[CNetAddressCtrl：： GetAddress](#getaddress)方法來驗證和剖析使用者輸入的網路位址。 如果[CNetAddressCtrl：： GetAddress](#getaddress)方法不成功，請使用[CNetAddressCtrl：:D isplayerrortip](#displayerrortip)方法來顯示錯誤訊息資訊提示。

此訊息會叫用[NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip)宏，如 Windows SDK 中所述。 該宏`NCM_DISPLAYERRORTIP`會傳送訊息。

##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress

針對與目前網路位址控制相關聯的網路位址，抓取已驗證和已剖析的標記法。

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>參數

*pAddress*<br/>
[in、out][NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address)結構的指標。  在呼叫 GetAddress 方法之前，請先將此結構的*pAddrInfo*成員設定為[NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)結構的位址。

### <a name="return-value"></a>傳回值

如果此方法成功，則值為 S_OK;否則為 COM 錯誤碼。 如需可能錯誤代碼的詳細資訊，請參閱[NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)宏的傳回值一節。

### <a name="remarks"></a>備註

如果此方法成功， [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)結構會包含網路位址的其他相關資訊。

使用[CNetAddressCtrl：： SetAllowType](#setallowtype)方法來指定目前的網路位址控制可支援的網址類別型。 使用[CNetAddressCtrl：： GetAddress](#getaddress)方法來驗證和剖析使用者輸入的網路位址。 如果[CNetAddressCtrl：： GetAddress](#getaddress)方法不成功，請使用[CNetAddressCtrl：:D isplayerrortip](#displayerrortip)方法來顯示錯誤訊息資訊提示。

這個方法會叫用[NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)宏，如 Windows SDK 中所述。 該宏會傳送 NCM_GETADDRESS 訊息。

##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType

抓取目前網路位址控制可支援的網路位址類型。

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>傳回值

旗標的位元組合（OR），指定網路位址控制可支援的網址類別型。 如需詳細資訊，請參閱[NET_STRING](/windows/win32/shell/net-string)。

### <a name="remarks"></a>備註

此訊息會叫用[NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype)宏，如 Windows SDK 中所述。 該宏會傳送 NCM_GETALLOWTYPE 訊息。

##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType

設定目前網路位址控制可支援的網路位址類型。

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwAddrMask*|在旗標的位元組合（OR），指定網路位址控制可支援的網址類別型。 如需詳細資訊，請參閱[NET_STRING](/windows/win32/shell/net-string)。|

### <a name="return-value"></a>傳回值

如果此方法成功，則為 S_OK;否則為 COM 錯誤碼。

### <a name="remarks"></a>備註

使用[CNetAddressCtrl：： SetAllowType](#setallowtype)方法來指定目前的網路位址控制可支援的網址類別型。 使用[CNetAddressCtrl：： GetAddress](#getaddress)方法來驗證和剖析使用者輸入的網路位址。 如果[CNetAddressCtrl：： GetAddress](#getaddress)方法不成功，請使用[CNetAddressCtrl：:D isplayerrortip](#displayerrortip)方法來顯示錯誤訊息資訊提示。

此訊息會叫用[NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype)宏，如 Windows SDK 中所述。 該宏會傳送 NCM_SETALLOWTYPE 訊息。

## <a name="see-also"></a>另請參閱

[CNetAddressCtrl 類別](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)
