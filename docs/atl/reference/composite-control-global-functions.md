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
ms.openlocfilehash: 58c7fed2d6e95967101e98589a13c114fe2e9a8a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496643"
---
# <a name="composite-control-global-functions"></a>複合控制項全域函式

這些函式提供建立對話方塊的支援, 以及建立、裝載和授權 ActiveX 控制項的功能。

> [!IMPORTANT]
>  下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|從使用者提供的對話方塊範本中建立強制回應對話方塊。 產生的對話方塊可以包含 ActiveX 控制項。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|從使用者提供的對話方塊範本中建立非強制回應對話方塊。 產生的對話方塊可以包含 ActiveX 控制項。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|建立 ActiveX 控制項、將它初始化、將它裝載于指定的視窗, 以及從控制項抓取介面指標 (或指標)。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制項、將它初始化、將它裝載于指定的視窗, 以及從控制項抓取介面指標 (或指標)。|
|[AtlAxAttachControl](#atlaxattachcontrol)|將先前建立的控制項加入至指定的視窗。|
|[AtlAxGetHost](#atlaxgethost)|用來取得指定視窗之容器的直接介面指標 (如果有的話), 並指定其控制碼。|
|[AtlAxGetControl](#atlaxgetcontrol)|用來取得包含在指定視窗 (如果有的話) 內之控制項的直接介面指標 (假設有其控制碼)。|
|[AtlSetChildSite](#atlsetchildsite)|`IUnknown`初始化子網站的。|
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 物件的主控程式碼。|
|[AtlAxWinTerm](#atlaxwinterm)|取消初始化 AxWin 物件的裝載程式碼。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|傳回物件之預設來源介面的相關資訊。|

## <a name="requirements"></a>需求

**標頭:** atlhost。h

##  <a name="atlaxdialogbox"></a>  AtlAxDialogBox

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
在識別其可執行檔包含對話方塊範本之模組的實例。

*lpTemplateName*<br/>
在識別對話方塊範本。 這個參數是以 null 結束之字元字串的指標, 可指定對話方塊範本的名稱, 或指定對話方塊範本之資源識別碼的整數值。 如果參數指定資源識別碼, 其高序位單字必須為零, 且其低序位字組必須包含識別碼。 您可以使用[MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew)宏來建立此值。

*hWndParent*<br/>
在識別擁有對話方塊的視窗。

*lpDialogProc*<br/>
在指向對話方塊程式。 如需對話方塊程式的詳細資訊, 請參閱[DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*dwInitParam*<br/>
在指定要傳遞至 WM_INITDIALOG 訊息之*lParam*參數中對話方塊的值。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

若要`AtlAxDialogBox`搭配包含 ActiveX 控制項的對話方塊範本使用, 請將有效的 CLSID、APPID 或 URL 字串指定為對話資源**控制項**區段的*文字*欄位, 並將 "AtlAxWin80" 當做 [*類別名稱*] 欄位在相同的區段下。 以下示範有效的**控制項**區段可能如下所示:

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

如需編輯資源腳本的詳細資訊, [請參閱如何:以文字格式](../../windows/how-to-open-a-resource-script-file-in-text-format.md)開啟資源腳本檔。 如需控制資源定義語句的詳細資訊, 請參閱 Windows SDK 下的[通用控制項參數](/windows/win32/menurc/common-control-parameters):SDK Tools。

如需一般對話方塊的詳細資訊, 請參閱 Windows SDK 中的[對話方塊](/windows/win32/api/winuser/nf-winuser-dialogboxw)和[CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 。

##  <a name="atlaxcreatedialog"></a>  AtlAxCreateDialog

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
在識別其可執行檔包含對話方塊範本之模組的實例。

*lpTemplateName*<br/>
在識別對話方塊範本。 這個參數是以 null 結束之字元字串的指標, 可指定對話方塊範本的名稱, 或指定對話方塊範本之資源識別碼的整數值。 如果參數指定資源識別碼, 其高序位單字必須為零, 且其低序位字組必須包含識別碼。 您可以使用[MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew)宏來建立此值。

*hWndParent*<br/>
在識別擁有對話方塊的視窗。

*lpDialogProc*<br/>
在指向對話方塊程式。 如需對話方塊程式的詳細資訊, 請參閱[DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*dwInitParam*<br/>
在指定要傳遞至 WM_INITDIALOG 訊息之*lParam*參數中對話方塊的值。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

產生的對話方塊可以包含 ActiveX 控制項。

請參閱 Windows SDK 中的[CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw)和[CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 。

##  <a name="atlaxcreatecontrol"></a>  AtlAxCreateControl

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
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化:

- ProgID, 例如 "MSCAL。Calendar. 7 "

- CLSID, 例如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，例如 " <http://www.microsoft.com> "

- 活動文檔的參考, 例如 "file://\\\Documents\MyDoc.doc"

- Html 片段, 例如\<"MSHTML: HTML >\<BODY > 這是一行文字\</BODY >\</HTML >"

   > [!NOTE]
   > 「MSHTML:」必須在 HTML 片段之前, 使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
在控制項將附加至之視窗的控制碼。

*pStream*<br/>
在資料流程的指標, 用來初始化控制項的屬性。 可以是 Null。

*ppUnkContainer*<br/>
脫銷將接收`IUnknown`容器之的指標位址。 可以是 Null。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

此全域函式提供的結果與呼叫[AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, null, null, null, null); 相同。

若要建立授權的 ActiveX 控制項, 請參閱[AtlAxCreateControlLic](#atlaxcreatecontrollic)。

##  <a name="atlaxcreatecontrolex"></a>  AtlAxCreateControlEx

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
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化:

- ProgID, 例如 "MSCAL。Calendar. 7 "

- CLSID, 例如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，例如 " <http://www.microsoft.com> "

- 活動文檔的參考, 例如 "file://\\\Documents\MyDoc.doc"

- Html 片段, 例如\<"MSHTML: HTML >\<BODY > 這是一行文字\</BODY >\</HTML >"

   > [!NOTE]
   > 「MSHTML:」必須在 HTML 片段之前, 使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
在控制項將附加至之視窗的控制碼。

*pStream*<br/>
在資料流程的指標, 用來初始化控制項的屬性。 可以是 Null。

*ppUnkContainer*<br/>
脫銷將接收`IUnknown`容器之的指標位址。 可以是 Null。

*ppUnkControl*<br/>
脫銷將接收`IUnknown`所建立控制項之的指標位址。 可以是 Null。

*iidSink*<br/>
所包含物件上傳出介面的介面識別碼。

*punkSink*<br/>
在包含的物件`IUnknown`成功建立之後, 要連接至包含物件上*iidSink*所指定連接點之接收器物件介面的指標。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`AtlAxCreateControlEx`類似于[AtlAxCreateControl](#atlaxcreatecontrol) , 但也可讓您接收新建立之控制項的介面指標, 並設定事件接收以接收控制項所引發的事件。

若要建立授權的 ActiveX 控制項, 請參閱[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)。

##  <a name="atlaxcreatecontrollic"></a>  AtlAxCreateControlLic

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
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化:

- ProgID, 例如 "MSCAL。Calendar. 7 "

- CLSID, 例如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，例如 " <http://www.microsoft.com> "

- 活動文檔的參考, 例如 "file://\\\Documents\MyDoc.doc"

- Html 片段, 例如\<"MSHTML: HTML >\<BODY > 這是一行文字\</BODY >\</HTML >"

   > [!NOTE]
   > 「MSHTML:」必須在 HTML 片段之前, 使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
控制項將附加至之視窗的控制碼。

*pStream*<br/>
資料流程的指標, 用來初始化控制項的屬性。 可以是 Null。

*ppUnkContainer*<br/>
將接收`IUnknown`容器之的指標位址。 可以是 Null。

*bstrLic*<br/>
包含控制項授權的 BSTR。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="example"></a>範例

如需如何使用`AtlAxCreateControlLic`的範例, 請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="atlaxcreatecontrollicex"></a>  AtlAxCreateControlLicEx

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
要傳遞至控制項之字串的指標。 必須以下列其中一種方式格式化:

- ProgID, 例如 "MSCAL。Calendar. 7 "

- CLSID, 例如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，例如 " <http://www.microsoft.com> "

- 活動文檔的參考, 例如 "file://\\\Documents\MyDoc.doc"

- Html 片段, 例如\<"MSHTML: HTML >\<BODY > 這是一行文字\</BODY >\</HTML >"

   > [!NOTE]
   > 「MSHTML:」必須在 HTML 片段之前, 使其被指定為 MSHTML 資料流程。

*hWnd*<br/>
控制項將附加至之視窗的控制碼。

*pStream*<br/>
資料流程的指標, 用來初始化控制項的屬性。 可以是 Null。

*ppUnkContainer*<br/>
將接收`IUnknown`容器之的指標位址。 可以是 Null。

*ppUnkControl*<br/>
脫銷將接收`IUnknown`所建立控制項之的指標位址。 可以是 Null。

*iidSink*<br/>
所包含物件上傳出介面的介面識別碼。

*punkSink*<br/>
在包含的物件`IUnknown`成功建立之後, 要連接至包含物件上*iidSink*所指定連接點之接收器物件介面的指標。

*bstrLic*<br/>
包含控制項授權的 BSTR。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`AtlAxCreateControlLicEx`類似于[AtlAxCreateControlLic](#atlaxcreatecontrollic) , 但也可讓您接收新建立之控制項的介面指標, 並設定事件接收以接收控制項所引發的事件。

### <a name="example"></a>範例

如需如何使用`AtlAxCreateControlLicEx`的範例, 請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl

將先前建立的控制項加入至指定的視窗。

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*pControl*<br/>
在控制項`IUnknown`之的指標。

*hWnd*<br/>
在將主控控制項之視窗的控制碼。

*ppUnkContainer*<br/>
脫銷容器物件`IUnknown`之指標的指標。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)和[AtlAxCreateControl](#atlaxcreatecontrol) , 同時建立及附加控制項。

> [!NOTE]
>  要附加的控制項物件必須在呼叫`AtlAxAttachControl`之前正確地初始化。

##  <a name="atlaxgethost"></a>  AtlAxGetHost

在考慮控制代碼的情況下，取得所指定視窗 (如果有) 之容器的直接介面指標。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*h*<br/>
在主控控制項之視窗的控制碼。

*pp*<br/>
脫銷`IUnknown`控制項容器的。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

在考慮控制代碼的情況下，取得所指定視窗內包含之控制項的直接介面指標。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*h*<br/>
在主控控制項之視窗的控制碼。

*pp*<br/>
脫銷主控`IUnknown`之控制項的。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="atlsetchildsite"></a>  AtlSetChildSite

呼叫此函式可將子物件的網站設定為`IUnknown`父物件的。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>參數

*punkChild*<br/>
在子系`IUnknown`介面的指標。

*punkParent*<br/>
在父系`IUnknown`介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="atlaxwininit"></a>  AtlAxWinInit

此函式會註冊 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 視窗類別以及幾個自訂視窗訊息, 藉此初始化 ATL 的控制項裝載程式碼。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>傳回值

如果控制項裝載程式碼的初始化成功, 則為非零。否則為 FALSE。

### <a name="remarks"></a>備註

您必須先呼叫此函式, 才能使用 ATL 控制項裝載 API。 呼叫此函式之後, 就可以在對[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)或[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的呼叫中使用 **"AtlAxWin"** 視窗類別, 如 Windows SDK 中所述。

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm

此函式會藉由取消註冊 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 視窗類別來取消初始化 ATL 的控制項裝載程式碼。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>傳回值

一律傳回 TRUE。

### <a name="remarks"></a>備註

此函式只會呼叫[UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) , 如 Windows SDK 中所述。

呼叫此函式, 在所有現有的主機視窗都已終結後進行清除 (如果您呼叫[AtlAxWinInit](#atlaxwininit) , 而且不再需要建立主機視窗)。 如果您未呼叫此函式, 則會在進程終止時自動取消註冊 window 類別。

##  <a name="atlgetobjectsourceinterface"></a>  AtlGetObjectSourceInterface

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
脫銷類型程式庫之 LIBID 的指標, 其中包含來源介面的定義。

*piid*<br/>
脫銷物件之預設來源介面的介面識別碼指標。

*pdwMajor*<br/>
脫銷類型程式庫之主要版本號碼的指標, 其中包含來源介面的定義。

*pdwMinor*<br/>
脫銷包含來源介面定義之類型程式庫次要版本號碼的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`AtlGetObjectSourceInterface`可以提供您預設來源介面的介面識別碼, 以及描述該介面之類型程式庫的 LIBID 和主要和次要版本號碼。

> [!NOTE]
>  若要讓此函式成功地抓取要求的資訊, *punkObj*所代表的`IDispatch`物件必須執行 (並傳回`IDispatch::GetTypeInfo`類型資訊`IProvideClassInfo2` ), 而且它也必須執行或`IPersist`. 來源介面的類型資訊必須與的類型資訊`IDispatch`位於相同的類型程式庫中。

### <a name="example"></a>範例

下列範例示範如何定義事件接收器類別, `CEasySink`以減少您可以傳遞至`IDispEventImpl`裸機基本概念的範本引數數目。 `EasyAdvise`和`EasyUnadvise`會`AtlGetObjectSourceInterface`在呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)或[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)之前, 用來初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成員。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[複合控制項巨集](../../atl/reference/composite-control-macros.md)
