---
title: 複合控制全域函數
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
ms.openlocfilehash: 99ecd4cf04b3eb696f897d6ef5a5e3839d46ef17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331604"
---
# <a name="composite-control-global-functions"></a>複合控制全域函數

這些功能支援創建對話方塊,以及創建、託管和許可 ActiveX 控制件。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|從使用者提供的對話方塊範本中建立強制回應對話方塊。 生成的對話框可以包含 ActiveX 控制件。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|從使用者提供的對話方塊範本中建立非強制回應對話方塊。 生成的對話框可以包含 ActiveX 控制件。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|創建 ActiveX 控制件,初始化它,在指定的視窗中託管它,並從控制項中檢索介面指標(或指標)。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|創建許可的 ActiveX 控制件,初始化它,在指定的視窗中託管它,並從控制項中檢索介面指標(或指標)。|
|[AtlAxAttachControl](#atlaxattachcontrol)|將先前建立的控制項加入至指定的視窗。|
|[AtlAxGetHost](#atlaxgethost)|用於獲取指向指定視窗(如果有)容器的直接介面指標,給定其句柄。|
|[AtlAxGetControl](#atlaxgetcontrol)|用於獲取指向指定視窗內(如果有)中包含的控制項的直接介面指標,給定其句柄。|
|[AtlSetChildSite](#atlsetchildsite)|初始化`IUnknown`子網站。|
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 物件的託管代碼。|
|[AtlAxWinTerm](#atlaxwinterm)|取消初始化 AxWin 物件的託管代碼。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|返回有關物件的預設源介面的資訊。|

## <a name="requirements"></a>需求

**標題:** atlhost.h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a>阿托克斯對話盒

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
[在]標識可執行檔的可執行檔包含對話框範本的模組的實例。

*lpTemplate 名稱*<br/>
[在]標識對話框範本。 這裡參數是指向指定對話方塊樣本名稱的 null 連接端的指標,或指定對話方塊樣本的資源識別符的整數值。 如果參數指定資源標識符,則其高階單詞必須為零,其低階字必須包含標識符。 您可以使用[MAKEINTRESOURCE 宏](/windows/win32/api/winuser/nf-winuser-makeintresourcew)建立此值。

*hWnd 父母*<br/>
[在]標識擁有對話框的視窗。

*lpDialogProc*<br/>
[在]指向對話框過程。 有關對話框過程的詳細資訊,請參閱[對話框過程](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*德維尼帕拉姆*<br/>
[在]指定要傳遞給WM_INITDIALOG訊息的*lParam*參數中的對話框的值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

要與`AtlAxDialogBox`包含 ActiveX 控制項的對話方塊樣本一起使用,請指定有效的 CLSID、APPID 或 URL 字串作為對話方塊資源**CONTROL**部分*的文本*欄位,以及同一節下的*類名*欄位的「AtlAxWin80」。。 下面展示了有效的**CONTROL**部分可能是什麼樣子:

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

有關編輯資源文稿的詳細資訊,請參考[如何: 以文字格式開啟資源文稿檔](../../windows/how-to-open-a-resource-script-file-in-text-format.md)。 有關控制項資源定義語句的詳細資訊,請參閱 Windows SDK[下的通用控制參數](/windows/win32/menurc/common-control-parameters):SDK 工具。

有關對話框的詳細資訊,請參閱 Windows SDK 中的[對話框](/windows/win32/api/winuser/nf-winuser-dialogboxw)與[建立對話帕拉姆](/windows/win32/api/winuser/nf-winuser-createdialogparamw)。

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a>AtlAx 建立對話

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
[在]標識可執行檔的可執行檔包含對話框範本的模組的實例。

*lpTemplate 名稱*<br/>
[在]標識對話框範本。 這裡參數是指向指定對話方塊樣本名稱的 null 連接端的指標,或指定對話方塊樣本的資源識別符的整數值。 如果參數指定資源標識符,則其高階單詞必須為零,其低階字必須包含標識符。 您可以使用[MAKEINTRESOURCE 宏](/windows/win32/api/winuser/nf-winuser-makeintresourcew)建立此值。

*hWnd 父母*<br/>
[在]標識擁有對話框的視窗。

*lpDialogProc*<br/>
[在]指向對話框過程。 有關對話框過程的詳細資訊,請參閱[對話框過程](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*德維尼帕拉姆*<br/>
[在]指定要傳遞給WM_INITDIALOG訊息的*lParam*參數中的對話框的值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

生成的對話框可以包含 ActiveX 控制件。

請參考 Windows SDK[建立對話](/windows/win32/api/winuser/nf-winuser-createdialogw)與[建立對話帕拉姆](/windows/win32/api/winuser/nf-winuser-createdialogparamw)。

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a>AtlAx 建立控制

建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向要傳遞給控制項的字串的指標。 必須採用以下方式之一進行格式化:

- ProgID,如`"MSCAL.Calendar.7"`

- CLSID,如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL,如`"<https://www.microsoft.com>"`

- 匯出文件的參考,例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段,例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必須在 HTML 片段之前,以便將其指定為 MSHTML 流。

*hWnd*<br/>
[在]處理控制項將附加到的視窗。

*pStream*<br/>
[在]指向用於初始化控制件屬性的流的指標。 可以是 NULL。

*ppUnk容器*<br/>
[出]將接收容器`IUnknown`的指標的位址。 可以是 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

此全域函數為您提供與調用 AtlAxCreateControlEx(lpszName、hwnd、pStream、NULL、NULL、NULL)相同的結果; [AtlAxCreateControlEx](#atlaxcreatecontrolex) *lpszName* *hWnd* *pStream*

要建立授權的 ActiveX 控制項,請參考[AtlAx 建立控制 。](#atlaxcreatecontrollic)

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a>AtlAx 建立控制Ex

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

*lpsz名稱*<br/>
指向要傳遞給控制項的字串的指標。 必須採用以下方式之一進行格式化:

- ProgID,如`"MSCAL.Calendar.7"`

- CLSID,如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL,如`"<https://www.microsoft.com>"`

- 匯出文件的參考,例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段,例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必須在 HTML 片段之前,以便將其指定為 MSHTML 流。

*hWnd*<br/>
[在]處理控制項將附加到的視窗。

*pStream*<br/>
[在]指向用於初始化控制件屬性的流的指標。 可以是 NULL。

*ppUnk容器*<br/>
[出]將接收容器`IUnknown`的指標的位址。 可以是 NULL。

*ppUnkControl*<br/>
[出]將接收已創建控制項`IUnknown`的指標的位址。 可以是 NULL。

*iidSink*<br/>
包含物件上傳出介面的介面標識符。

*龐克辛克*<br/>
指向接收器物件`IUnknown`介面的指標,用於在成功創建包含的物件后,將連接到*iidSink*在包含物件上指定的連接點。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

`AtlAxCreateControlEx`與[AtlAxCreateControl](#atlaxcreatecontrol)類似,但也允許您接收指向新創建的控制項的介面指標,並設置事件接收器以接收控制項觸發的事件。

要建立授權的 ActiveX 控制件,請參閱[AtlAxCreateControllicEx](#atlaxcreatecontrollicex)。

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a>AtlAx 建立控制

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

*lpsz名稱*<br/>
指向要傳遞給控制項的字串的指標。 必須採用以下方式之一進行格式化:

- ProgID,如`"MSCAL.Calendar.7"`

- CLSID,如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL,如`"<https://www.microsoft.com>"`

- 匯出文件的參考,例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段,例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必須在 HTML 片段之前,以便將其指定為 MSHTML 流。

*hWnd*<br/>
處理控制項將附加到的視窗。

*pStream*<br/>
指向用於初始化控制件屬性的流的指標。 可以是 NULL。

*ppUnk容器*<br/>
將接收容器`IUnknown`的指標的位址。 可以是 NULL。

*bstrLIC*<br/>
包含控制項授權的 BSTR。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="example"></a>範例

有關如何`AtlAxCreateControlLic`使用[的託管 ActiveX 控制項,請參閱 ATL AXHost。](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a>AtlAx 建立控制

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

*lpsz名稱*<br/>
指向要傳遞給控制項的字串的指標。 必須採用以下方式之一進行格式化:

- ProgID,如`"MSCAL.Calendar.7"`

- CLSID,如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL,如`"<https://www.microsoft.com>"`

- 匯出文件的參考,例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段,例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必須在 HTML 片段之前,以便將其指定為 MSHTML 流。

*hWnd*<br/>
處理控制項將附加到的視窗。

*pStream*<br/>
指向用於初始化控制件屬性的流的指標。 可以是 NULL。

*ppUnk容器*<br/>
將接收容器`IUnknown`的指標的位址。 可以是 NULL。

*ppUnkControl*<br/>
[出]將接收已創建控制項`IUnknown`的指標的位址。 可以是 NULL。

*iidSink*<br/>
包含物件上傳出介面的介面標識符。

*龐克辛克*<br/>
指向接收器物件`IUnknown`介面的指標,用於在成功創建包含的物件后,將連接到*iidSink*在包含物件上指定的連接點。

*bstrLIC*<br/>
包含控制項授權的 BSTR。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

`AtlAxCreateControlLicEx`與[AtlAxCreateControlLic](#atlaxcreatecontrollic)類似,但也允許您接收指向新創建的控制項的介面指標,並設置事件接收器以接收控制項觸發的事件。

### <a name="example"></a>範例

有關如何`AtlAxCreateControlLicEx`使用[的託管 ActiveX 控制項,請參閱 ATL AXHost。](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a>Atlax 附加控制

將先前建立的控制項加入至指定的視窗。

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*pControl*<br/>
[在]指向控件`IUnknown`的指標。

*hWnd*<br/>
[在]處理將承載控制件的視窗。

*ppUnk容器*<br/>
[出]指向容器物件的指標`IUnknown`。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)和[AtlAxCreateControl](#atlaxcreatecontrol)可同時創建和附加控制項。

> [!NOTE]
> 在調用`AtlAxAttachControl`之前,必須正確初始化所連接的控制項物件。

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a>AtlAxGetHost

在考慮控制代碼的情況下，取得所指定視窗 (如果有) 之容器的直接介面指標。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*H*<br/>
[在]承載控件的視窗的句柄。

*Pp*<br/>
[出]控制項`IUnknown`的容器的容器 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a>AtlAxGetControl

在考慮控制代碼的情況下，取得所指定視窗內包含之控制項的直接介面指標。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>參數

*H*<br/>
[在]承載控件的視窗的句柄。

*Pp*<br/>
[出]要`IUnknown`承載的控制項的 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a>AtlSet兒童網站

調用此函數以將子物件的網站設置為`IUnknown`父物件的網站。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>參數

*朋克兒童*<br/>
[在]指向`IUnknown`子介面的指標。

*朋克家長*<br/>
[在]指向父級`IUnknown`介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a>阿托爾克斯·維尼尼特

此功能通過註冊 **「AtlAxWin80」** 和 **「AtlAxWinLic80」** 視窗類以及幾個自定義視窗訊息來初始化 ATL 的控制託管代碼。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>傳回值

如果控件託管代碼的初始化成功,則非零;否則 FALSE。

### <a name="remarks"></a>備註

在使用 ATL 控制項託管 API 之前,必須調用此功能。 呼叫此功能後 **,「AtlAxWin」** 視窗類可用於[創建視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)或[創建WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的調用,如 Windows SDK 中所述。

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a>AtlAxWinterm

此函數通過取消註冊 **「AtlAxWin80」** 和 **「AtlAxWinLic80」** 視窗類來取消初始化 ATL 的控制託管代碼。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>傳回值

始終返回 TRUE。

### <a name="remarks"></a>備註

此函數只是呼叫 Windows SDK 中所述[的取消註冊類別](/windows/win32/api/winuser/nf-winuser-unregisterclassw)。

如果調用[AtlAxWinInit,](#atlaxwininit)並且不再需要建立主機視窗,則調用此函數以在所有現有主機視窗被銷毀後進行清理。 如果不調用此函數,則進程終止時將自動取消註冊視窗類。

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a>AtlGetObject來源介面

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

*龐克奧比*<br/>
[在]指向要為其返回資訊的物件的指標。

*普利比德*<br/>
[出]指向包含源介面定義的類型庫的 LIBID 的指標。

*皮伊德*<br/>
[出]指向物件預設源介面的介面 ID 的指標。

*pdwMajor*<br/>
[出]指向包含源介面定義的類型庫的主要版本號的指標。

*pdwMinor*<br/>
[出]指向包含源介面定義的類型庫的次要版本號的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`AtlGetObjectSourceInterface`可以為您提供預設源介面的介面 ID,以及描述該介面的類型庫的 LIBID 和主要版本號和次要版本號。

> [!NOTE]
> 若要成功檢查的資訊,*由 punkObj*`IDispatch`表示的物件必須實現(`IDispatch::GetTypeInfo`並透過傳回類型資訊),並且`IProvideClassInfo2`還`IPersist`必須實現或 。 源介面的類型信息必須與的類型資訊位於同一`IDispatch`類型庫中。

### <a name="example"></a>範例

下面的範例顯示了如何定義事件接收器類,`CEasySink`這減少了可以傳遞給`IDispEventImpl`基本要素的範本參數數。 `EasyAdvise`並`EasyUnadvise``AtlGetObjectSourceInterface`用於初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成員,然後再致電[DispEvent 建議](idispeventsimpleimpl-class.md#dispeventadvise)或[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[複合控制巨集](../../atl/reference/composite-control-macros.md)
