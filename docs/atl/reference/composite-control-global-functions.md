---
title: 複合控制項全域函式
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: fe9d9a3a0538e2e5744987adcd64e67562711ea8
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353112"
---
# <a name="composite-control-global-functions"></a>複合控制項全域函式

這些函式提供建立對話方塊的支援，以及用於建立、裝載及授權 ActiveX 控制項的功能。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|函式|說明|
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|從使用者提供的對話方塊範本中建立強制回應對話方塊。 產生的對話方塊可以包含 ActiveX 控制項。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|從使用者提供的對話方塊範本中建立非強制回應對話方塊。 產生的對話方塊可以包含 ActiveX 控制項。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|建立 ActiveX 控制項、將它初始化、將它裝載于指定的視窗中，以及抓取介面指標 (或從控制項) 的指標。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制項、將它初始化、將它裝載于指定的視窗中，以及抓取介面指標 (或從控制項) 的指標。|
|[AtlAxAttachControl](#atlaxattachcontrol)|將先前建立的控制項加入至指定的視窗。|
|[AtlAxGetHost](#atlaxgethost)|用來取得指定之視窗的容器的直接介面指標 (如果有任何) ，則指定其控制碼。|
|[AtlAxGetControl](#atlaxgetcontrol)|用來取得指定視窗內所含之控制項的直接介面指標 (如果有任何) ，則指定其控制碼。|
|[AtlSetChildSite](#atlsetchildsite)|初始化 `IUnknown` 子網站的。|
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 物件的裝載程式碼。|
|[AtlAxWinTerm](#atlaxwinterm)|取消初始化 AxWin 物件的裝載程式碼。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|傳回物件之預設來源介面的相關資訊。|

## <a name="requirements"></a>需求

**標頭：** atlhost。h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a> AtlAxDialogBox

從使用者提供的對話方塊範本中建立強制回應對話方塊。

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
在識別模組的實例，其可執行檔包含對話方塊範本。

*lpTemplateName*<br/>
在識別對話方塊範本。 這個參數是以 null 結束的字元字串指標，可指定對話方塊範本的名稱，或指定對話方塊範本之資源識別碼的整數值。 如果參數指定資源識別碼，其高序位單字必須為零，而且其低序位單字必須包含識別碼。 您可以使用 [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) 宏來建立這個值。

*hWndParent*<br/>
在識別擁有對話方塊的視窗。

*lpDialogProc*<br/>
在指向對話方塊程式。 如需對話方塊程式的詳細資訊，請參閱 [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*dwInitParam*<br/>
在指定要傳遞給 WM_INITDIALOG 訊息 *lParam* 參數中之對話方塊的值。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

若要使用 `AtlAxDialogBox` 包含 ActiveX 控制項的對話方塊範本，請指定有效的 CLSID、APPID 或 URL 字串作為對話方塊資源之**控制**區段的*文字*欄位，以及使用 "AtlAxWin80" 作為相同區段下的 [*類別名稱*] 欄位。 下列範例會示範有效的 **控制項** 區段看起來的樣子：

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

如需有關編輯資源腳本的詳細資訊，請參閱 [如何：建立資源](../../windows/how-to-create-a-resource-script-file.md)。 如需控制資源定義語句的詳細資訊，請參閱 Windows SDK： SDK Tools 下的 [通用控制項參數](/windows/win32/menurc/common-control-parameters) 。

如需有關一般對話方塊的詳細資訊，請參閱 Windows SDK 中的 [對話方塊](/windows/win32/api/winuser/nf-winuser-dialogboxw) 和 [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 。

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a> AtlAxCreateDialog

從使用者提供的對話方塊範本中建立非強制回應對話方塊。

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
在識別模組的實例，其可執行檔包含對話方塊範本。

*lpTemplateName*<br/>
在識別對話方塊範本。 這個參數是以 null 結束的字元字串指標，可指定對話方塊範本的名稱，或指定對話方塊範本之資源識別碼的整數值。 如果參數指定資源識別碼，其高序位單字必須為零，而且其低序位單字必須包含識別碼。 您可以使用 [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) 宏來建立這個值。

*hWndParent*<br/>
在識別擁有對話方塊的視窗。

*lpDialogProc*<br/>
在指向對話方塊程式。 如需對話方塊程式的詳細資訊，請參閱 [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*dwInitParam*<br/>
在指定要傳遞給 WM_INITDIALOG 訊息 *lParam* 參數中之對話方塊的值。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

產生的對話方塊可以包含 ActiveX 控制項。

請參閱 Windows SDK 中的 [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) 和 [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 。

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a> AtlAxCreateControl

建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 現用檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
在控制項將附加至的視窗控制碼。

*pStream*<br/>
在用來初始化控制項屬性之資料流程的指標。 可以是 NULL。

*ppUnkContainer*<br/>
擴展將接收容器之指標的位址 `IUnknown` 。 可以是 NULL。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

此全域函式提供與呼叫 [AtlAxCreateControlEx](#atlaxcreatecontrolex) 相同的結果 (*lpszName*、 *hWnd*、 *pStream*、null、null、null、null) ;。

若要建立授權的 ActiveX 控制項，請參閱 [AtlAxCreateControlLic](#atlaxcreatecontrollic)。

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a> AtlAxCreateControlEx

建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。 另外也可以建立新控制項的介面指標和事件接收器。

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 現用檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
在控制項將附加至的視窗控制碼。

*pStream*<br/>
在用來初始化控制項屬性之資料流程的指標。 可以是 NULL。

*ppUnkContainer*<br/>
擴展將接收容器之指標的位址 `IUnknown` 。 可以是 NULL。

*ppUnkControl*<br/>
擴展將接收所建立控制項之的指標位址 `IUnknown` 。 可以是 NULL。

*iidSink*<br/>
包含物件上之輸出介面的介面識別碼。

*punkSink*<br/>
在 `IUnknown` 成功建立包含的物件之後，要連接到包含物件上 *iidSink* 所指定之連接點的接收物件介面指標。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`AtlAxCreateControlEx` 類似于 [AtlAxCreateControl](#atlaxcreatecontrol) ，但也可讓您接收新建立控制項的介面指標，並設定事件接收以接收控制項所引發的事件。

若要建立授權的 ActiveX 控制項，請參閱 [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)。

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a> AtlAxCreateControlLic

建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 現用檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
控制項將附加至的視窗控制碼。

*pStream*<br/>
用來初始化控制項屬性之資料流程的指標。 可以是 NULL。

*ppUnkContainer*<br/>
將接收容器之指標的位址 `IUnknown` 。 可以是 NULL。

*bstrLic*<br/>
包含控制項授權的 BSTR。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="example"></a>範例

如需如何使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `AtlAxCreateControlLic` 。

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a> AtlAxCreateControlLicEx

建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。 另外也可以建立新控制項的介面指標和事件接收器。

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 現用檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
控制項將附加至的視窗控制碼。

*pStream*<br/>
用來初始化控制項屬性之資料流程的指標。 可以是 NULL。

*ppUnkContainer*<br/>
將接收容器之指標的位址 `IUnknown` 。 可以是 NULL。

*ppUnkControl*<br/>
擴展將接收所建立控制項之的指標位址 `IUnknown` 。 可以是 NULL。

*iidSink*<br/>
包含物件上之輸出介面的介面識別碼。

*punkSink*<br/>
在 `IUnknown` 成功建立包含的物件之後，要連接到包含物件上 *iidSink* 所指定之連接點的接收物件介面指標。

*bstrLic*<br/>
包含控制項授權的 BSTR。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`AtlAxCreateControlLicEx` 類似于 [AtlAxCreateControlLic](#atlaxcreatecontrollic) ，但也可讓您接收新建立控制項的介面指標，並設定事件接收以接收控制項所引發的事件。

### <a name="example"></a>範例

如需如何使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `AtlAxCreateControlLicEx` 。

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a> AtlAxAttachControl

將先前建立的控制項加入至指定的視窗。

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*pControl*<br/>
在控制項之的指標 `IUnknown` 。

*hWnd*<br/>
在將裝載控制項的視窗控制碼。

*ppUnkContainer*<br/>
擴展指向容器物件之指標的指標 `IUnknown` 。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

使用 [AtlAxCreateControlEx](#atlaxcreatecontrolex) 和 [AtlAxCreateControl](#atlaxcreatecontrol) ，同時建立和附加控制項。

> [!NOTE]
> 要附加的控制項物件必須在呼叫之前正確地初始化 `AtlAxAttachControl` 。

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a> AtlAxGetHost

在考慮控制代碼的情況下，取得所指定視窗 (如果有) 之容器的直接介面指標。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*h*<br/>
在裝載控制項的視窗控制碼。

*Pp*<br/>
擴展 `IUnknown` 控制項容器的。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a> AtlAxGetControl

在考慮控制代碼的情況下，取得所指定視窗內包含之控制項的直接介面指標。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*h*<br/>
在裝載控制項的視窗控制碼。

*Pp*<br/>
擴展所裝載 `IUnknown` 控制項的。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a> AtlSetChildSite

呼叫此函式可將子物件的網站設定為 `IUnknown` 父物件的。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>參數

*punkChild*<br/>
在子系介面的指標 `IUnknown` 。

*punkParent*<br/>
在父的介面指標 `IUnknown` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a> AtlAxWinInit

此函式會註冊 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 視窗類別以及幾個自訂視窗訊息，藉此初始化 ATL 的控制項裝載程式碼。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>傳回值

如果控制項裝載程式碼的初始化成功，則為非零。否則為 FALSE。

### <a name="remarks"></a>備註

使用 ATL 控制項裝載 API 之前，必須先呼叫此函式。 在呼叫此函式之後， **"AtlAxWin"** 視窗類別可用於對 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 或 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的呼叫，如 Windows SDK 所述。

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a> AtlAxWinTerm

此函式會取消註冊 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 視窗類別，藉此取消初始化 ATL 的控制項裝載程式碼。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>傳回值

一律傳回 TRUE。

### <a name="remarks"></a>備註

此函數只會呼叫 [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) ，如 Windows SDK 所述。

如果您呼叫 [AtlAxWinInit](#atlaxwininit) ，且不再需要建立主機視窗，請呼叫此函式，在所有現有的主機視窗都已終結之後進行清除。 如果您未呼叫此函式，則會在進程終止時自動取消註冊視窗類別。

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a> AtlGetObjectSourceInterface

呼叫此函式可擷取物件的預設來源介面的相關資訊。

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>參數

*punkObj*<br/>
在要傳回其資訊之物件的指標。

*plibid*<br/>
擴展類型程式庫的 LIBID 指標，其中包含來源介面的定義。

*piid*<br/>
擴展物件之預設來源介面的介面識別碼指標。

*pdwMajor*<br/>
擴展類型程式庫主要版本號碼的指標，其中包含來源介面的定義。

*pdwMinor*<br/>
擴展類型程式庫的次要版本號碼的指標，其中包含來源介面的定義。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`AtlGetObjectSourceInterface` 可以提供您預設來源介面的介面識別碼，以及描述該介面之類型程式庫的 LIBID 和主要和次要版本號碼。

> [!NOTE]
> 為了讓此函式成功取得要求的資訊， *punkObj* 所代表的物件必須 `IDispatch` 透過) 來執行 (和傳回型別資訊，而且 `IDispatch::GetTypeInfo` 它還必須執行 `IProvideClassInfo2` 或 `IPersist` 。 來源介面的類型資訊必須與類型資訊位於相同的類型程式庫中 `IDispatch` 。

### <a name="example"></a>範例

下列範例顯示如何定義事件接收器類別，以 `CEasySink` 減少可傳遞給裸機基本專案的範本引數數目 `IDispEventImpl` 。 `EasyAdvise`並 `EasyUnadvise` 使用在 `AtlGetObjectSourceInterface` 呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)或[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)之前，初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成員。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[複合控制項宏](../../atl/reference/composite-control-macros.md)
