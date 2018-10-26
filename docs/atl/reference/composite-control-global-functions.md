---
title: 複合控制項全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c8493650ef2c86a89c1a3060deb5ee6269a38a7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068641"
---
# <a name="composite-control-global-functions"></a>複合控制項全域函式

這些函式會提供建立對話方塊，以及建立、 裝載和授權的 ActiveX 控制項的支援。

> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|從使用者提供的對話方塊範本中建立強制回應對話方塊。 產生的對話方塊中可包含 ActiveX 控制項。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|從使用者提供的對話方塊範本中建立非強制回應對話方塊。 產生的對話方塊中可包含 ActiveX 控制項。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|建立 ActiveX 控制項、 將它初始化，裝載在指定的視窗中，並從控制項擷取介面指標 （或指標）。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制項、 將它初始化，裝載在指定的視窗中，並從控制項擷取介面指標 （或指標）。|
|[AtlAxAttachControl](#atlaxattachcontrol)|將先前建立的控制項加入至指定的視窗。|
|[AtlAxGetHost](#atlaxgethost)|用來取得指定的視窗 （如果有的話），容器的直接介面指標考慮控制代碼。|
|[AtlAxGetControl](#atlaxgetcontrol)|用來取得包含在指定的視窗 （如果有的話），該控制項的直接介面指標考慮控制代碼。|
|[AtlSetChildSite](#atlsetchildsite)|初始化`IUnknown`將子站台。|
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 物件的裝載程式碼。|
|[AtlAxWinTerm](#atlaxwinterm)|取消初始化 AxWin 物件的裝載程式碼。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|傳回物件的預設來源介面的相關資訊。|

## <a name="requirements"></a>需求

**標頭：** atlhost.h

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
[in]識別的模組，其可執行檔包含對話方塊範本的執行個體。

*lpTemplateName*<br/>
[in]識別對話方塊範本。 此參數會指定名稱的對話方塊範本的 null 結束的字元字串的指標，或是指定的對話方塊範本的資源識別碼的整數值。 如果參數指定資源識別項，其高序位文字必須是零，其低序位字組必須包含識別項。 您可以使用[MAKEINTRESOURCE](/windows/desktop/api/winuser/nf-winuser-makeintresourcea)巨集來建立此值。

*hWndParent*<br/>
[in]識別擁有對話方塊的視窗。

*lpDialogProc*<br/>
[in]指向對話方塊程序。 如需對話方塊程序的詳細資訊，請參閱[DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469)。

*dwInitParam*<br/>
[in]指定要傳遞至對話方塊中的值*lParam* WM_INITDIALOG 訊息參數。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

若要使用`AtlAxDialogBox`包含 ActiveX 控制項的對話方塊範本，請指定有效的 CLSID、 APPID 或 URL 字串做為*文字*欄位**控制**區段對話方塊資源，連同"AtlAxWin80"作為*類別名稱*欄位下相同的區段。 以下示範哪些有效**控制**區段看起來會像：

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

如需有關如何編輯資源指令碼的詳細資訊，請參閱 <<c0> [ 如何： 以文字格式開啟資源指令碼檔](../../windows/how-to-open-a-resource-script-file-in-text-format.md)。 如需有關控制資源定義陳述式的詳細資訊，請參閱[常見的控制參數](/windows/desktop/menurc/common-control-parameters)下方 Windows SDK *: SDK Tools*。

如需有關一般對話方塊的詳細資訊，請參閱[對話方塊中](/windows/desktop/api/winuser/nf-winuser-dialogboxa)並[CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) Windows SDK 中。

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
[in]識別的模組，其可執行檔包含對話方塊範本的執行個體。

*lpTemplateName*<br/>
[in]識別對話方塊範本。 此參數會指定名稱的對話方塊範本的 null 結束的字元字串的指標，或是指定的對話方塊範本的資源識別碼的整數值。 如果參數指定資源識別項，其高序位文字必須是零，其低序位字組必須包含識別項。 您可以使用[MAKEINTRESOURCE](/windows/desktop/api/winuser/nf-winuser-makeintresourcea)巨集來建立此值。

*hWndParent*<br/>
[in]識別擁有對話方塊的視窗。

*lpDialogProc*<br/>
[in]指向對話方塊程序。 如需對話方塊程序的詳細資訊，請參閱[DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469)。

*dwInitParam*<br/>
[in]指定要傳遞至對話方塊中的值*lParam* WM_INITDIALOG 訊息參數。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

產生的對話方塊中可包含 ActiveX 控制項。

請參閱[CreateDialog](/windows/desktop/api/winuser/nf-winuser-createdialoga)並[CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) Windows SDK 中。

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
要傳遞給控制項的字串指標。 格式必須如下的其中一個：

- ProgID，例如"MSCAL。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID

- URL，例如 " http://www.microsoft.com "

- 這類的主動式文件的參考 「 file://\\\Documents\MyDoc.doc"

- 這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」

   > [!NOTE]
   > 「 MSHTML: 「 必須在前面的 HTML 片段，因此，它會指定為 MSHTML 資料流。

*hWnd*<br/>
[in]控制項將會附加至視窗的控制代碼。

*pStream*<br/>
[in]用來初始化控制項的屬性資料流的指標。 可以是 NULL。

*ppUnkContainer*<br/>
[out]將會收到的指標位址`IUnknown`的容器。 可以是 NULL。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

此全域函式可讓您與呼叫相同的結果[AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*， *hWnd*， *pStream*，NULL，NULL，NULL，NULL);。

若要建立授權的 ActiveX 控制項，請參閱[AtlAxCreateControlLic](#atlaxcreatecontrollic)。

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
要傳遞給控制項的字串指標。 格式必須如下的其中一個：

- ProgID，例如"MSCAL。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID

- URL，例如 " http://www.microsoft.com "

- 這類的主動式文件的參考 「 file://\\\Documents\MyDoc.doc"

- 這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」

   > [!NOTE]
   > 「 MSHTML: 「 必須在前面的 HTML 片段，因此，它會指定為 MSHTML 資料流。

*hWnd*<br/>
[in]控制項將會附加至視窗的控制代碼。

*pStream*<br/>
[in]用來初始化控制項的屬性資料流的指標。 可以是 NULL。

*ppUnkContainer*<br/>
[out]將會收到的指標位址`IUnknown`的容器。 可以是 NULL。

*ppUnkControl*<br/>
[out]將會收到的指標位址`IUnknown`的建立的控制項。 可以是 NULL。

*iidSink*<br/>
在所包含的物件上的輸出介面的介面識別項。

*punkSink*<br/>
指標`IUnknown`連接到指定的連接點的接收器物件的介面*iidSink*上所包含的物件已成功建立後，所包含的物件。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

`AtlAxCreateControlEx` 類似於[AtlAxCreateControl](#atlaxcreatecontrol)也可讓您接收新建立之控制項的介面指標，並設定要接收控制項所引發的事件的事件接收。

若要建立授權的 ActiveX 控制項，請參閱[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)。

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
要傳遞給控制項的字串指標。 格式必須如下的其中一個：

- ProgID，例如"MSCAL。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID

- URL，例如 " http://www.microsoft.com "

- 這類的主動式文件的參考 「 file://\\\Documents\MyDoc.doc"

- 這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」

   > [!NOTE]
   > 「 MSHTML: 「 必須在前面的 HTML 片段，因此，它會指定為 MSHTML 資料流。

*hWnd*<br/>
控制項將會附加至視窗的控制代碼。

*pStream*<br/>
用來初始化控制項的屬性資料流的指標。 可以是 NULL。

*ppUnkContainer*<br/>
將會收到的指標位址`IUnknown`的容器。 可以是 NULL。

*bstrLic*<br/>
BSTR，其中包含控制項的授權。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="example"></a>範例

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需如何使用的範例`AtlAxCreateControlLic`。

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
要傳遞給控制項的字串指標。 格式必須如下的其中一個：

- ProgID，例如"MSCAL。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID

- URL，例如 " http://www.microsoft.com "

- 這類的主動式文件的參考 「 file://\\\Documents\MyDoc.doc"

- 這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」

   > [!NOTE]
   > 「 MSHTML: 「 必須在前面的 HTML 片段，因此，它會指定為 MSHTML 資料流。

*hWnd*<br/>
控制項將會附加至視窗的控制代碼。

*pStream*<br/>
用來初始化控制項的屬性資料流的指標。 可以是 NULL。

*ppUnkContainer*<br/>
將會收到的指標位址`IUnknown`的容器。 可以是 NULL。

*ppUnkControl*<br/>
[out]將會收到的指標位址`IUnknown`的建立的控制項。 可以是 NULL。

*iidSink*<br/>
在所包含的物件上的輸出介面的介面識別項。

*punkSink*<br/>
指標`IUnknown`連接到指定的連接點的接收器物件的介面*iidSink*上所包含的物件已成功建立後，所包含的物件。

*bstrLic*<br/>
BSTR，其中包含控制項的授權。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

`AtlAxCreateControlLicEx` 類似於[AtlAxCreateControlLic](#atlaxcreatecontrollic)也可讓您接收新建立之控制項的介面指標，並設定要接收控制項所引發的事件的事件接收。

### <a name="example"></a>範例

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需如何使用的範例`AtlAxCreateControlLicEx`。

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
[in]指標`IUnknown`的控制項。

*hWnd*<br/>
[in]將要裝載控制項的視窗控制代碼。

*ppUnkContainer*<br/>
[out]指標的指標`IUnknown`的容器物件。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)並[AtlAxCreateControl](#atlaxcreatecontrol)同時建立並附加控制項。

> [!NOTE]
>  所附加的控制項物件必須正確地初始化之前呼叫`AtlAxAttachControl`。

##  <a name="atlaxgethost"></a>  AtlAxGetHost

在考慮控制代碼的情況下，取得所指定視窗 (如果有) 之容器的直接介面指標。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*h*<br/>
[in]裝載控制項的視窗控制代碼。

*前置處理*<br/>
[out]`IUnknown`容器的控制項。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

在考慮控制代碼的情況下，取得所指定視窗內包含之控制項的直接介面指標。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*h*<br/>
[in]裝載控制項的視窗控制代碼。

*前置處理*<br/>
[out]`IUnknown`所裝載之控制項。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="atlsetchildsite"></a>  AtlSetChildSite

呼叫此函式可設定的子物件的站台`IUnknown`父物件。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>參數

*punkChild*<br/>
[in]指標`IUnknown`介面之子系。

*punkParent*<br/>
[in]指標`IUnknown`之父代的介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="atlaxwininit"></a>  AtlAxWinInit

此函式會初始化 ATL 的控制項裝載程式碼，藉由註冊 **"AtlAxWin80"** 並 **"AtlAxWinLic80"** 視窗類別加上幾個自訂視窗訊息。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>傳回值

如果控制項裝載程式碼的初始化是否成功; 非零值否則為 FALSE。

### <a name="remarks"></a>備註

使用 ATL 控制項裝載 API 之前，必須呼叫此函式。 這個函式，呼叫 **"AtlAxWin 」** 視窗類別可用於呼叫[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)或[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)、 Windows SDK 中所述。

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm

此函式取消初始化 ATL 的控制項裝載程式碼取消註冊 **"AtlAxWin80"** 並 **"AtlAxWinLic80"** 視窗類別。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>傳回值

一律會傳回 TRUE。

### <a name="remarks"></a>備註

此函式只會呼叫[UnregisterClass](https://msdn.microsoft.com/library/windows/desktop/ms644899) Windows SDK 中所述。

呼叫此函式來清除所有現有的主控件 windows 皆已終結，如果您呼叫[AtlAxWinInit](#atlaxwininit)而且您不再需要建立主應用程式視窗。 如果您未呼叫此函式，該視窗類別將會取消註冊自動處理序終止時。

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
[in]要傳回資訊的物件的指標。

*plibid*<br/>
[out]指標，包含來源介面的定義之類型程式庫的 LIBID。

*piid*<br/>
[out]物件的預設來源介面的介面識別碼指標。

*pdwMajor*<br/>
[out]包含來源介面的定義之類型程式庫的主要版本號碼指標。

*pdwMinor*<br/>
[out]包含來源介面的定義之類型程式庫的次要版本號碼指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`AtlGetObjectSourceInterface` 可以提供您的預設來源介面，以及 LIBID 和主要的介面 ID 和描述該介面的類型程式庫的次要版本號碼。

> [!NOTE]
>  若要成功擷取要求的資訊。 此函式，表示的物件*punkObj*必須實作`IDispatch`(和傳回型別資訊透過`IDispatch::GetTypeInfo`) 以及它必須同時實作任一`IProvideClassInfo2`或`IPersist`。 來源介面的型別資訊必須位於相同的型別程式庫，為的型別資訊`IDispatch`。

### <a name="example"></a>範例

下列範例示範如何定義事件接收器類別中， `CEasySink`，這樣可以降低，您可以傳遞給範本引數數目`IDispEventImpl`到基本的必要功能。 `EasyAdvise` 並`EasyUnadvise`使用`AtlGetObjectSourceInterface`初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成員，然後再呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)或是[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[複合控制項巨集](../../atl/reference/composite-control-macros.md)
