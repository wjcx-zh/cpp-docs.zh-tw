---
title: CAxWindow 類別
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5629370bc1f821dac0a08cc76b5df1450f7a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318727"
---
# <a name="caxwindow-class"></a>CAxWindow 類別

此類提供了用於操作承載 ActiveX 控制件的視窗的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAxWindow : public CWindow
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[附加控制](#attachcontrol)|將現有的 ActiveX 控制件`CAxWindow`附加到 物件。|
|[薩克斯視窗](#caxwindow)|建構 `CAxWindow` 物件。|
|[CreateControl](#createcontrol)|創建 ActiveX 控制件,初始化它,並將其託管`CAxWindow`在 視窗中。|
|[建立控制Ex](#createcontrolex)|創建 ActiveX 控制件並從控制項中檢索介面指標(或指標)。|
|[取得 WndClass 名稱](#getwndclassname)|(靜態)檢索`CAxWindow`物件的預定義的類名稱。|
|[查詢控制](#querycontrol)|檢索託管`IUnknown`的 ActiveX 控制件。|
|[查詢主機](#queryhost)|檢索`IUnknown``CAxWindow`物件的指標。|
|[設定外部排程](#setexternaldispatch)|設置`CAxWindow`物件使用的外部調度介面。|
|[設定外部 UIHandler](#setexternaluihandler)|設置`CAxWindow`物件`IDocHostUIHandler`使用的外部介面。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算符 |](#operator_eq)|將 HWND 分配`CAxWindow`給現有 物件。|

## <a name="remarks"></a>備註

此類提供了用於操作承載 ActiveX 控制件的視窗的方法。 託管由 **「AtlAxWin80」** 提供,由`CAxWindow`包裝 。

類`CAxWindow`作為`CAxWindowT`類的專業化實現。 此專業化化聲明為:

`typedef CAxWindowT<CWindow> CAxWindow;`

如果需要更改基類,可以使用`CAxWindowT`並將新基類指定為範本參數。

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAx 視窗::附加控制

如果一個主機尚未存在,則創建新的主機物件,並將指定的控制項附加到主機。

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*pControl*<br/>
[在]指向控件`IUnknown`的指標。

*ppUnk容器*<br/>
[出]指向主機(`IUnknown`物件的)的`AxWin`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

在調用`AttachControl`之前,必須正確初始化所連接的控制項物件。

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a>薩克斯視窗::薩克斯視窗

使用現有視窗`CAxWindow`物件句柄建構物件。

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗物件的句柄。

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::建立控制

建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向字串的指標以建立控制項。 必須採用以下方式之一進行格式化:

- ProgID,如`"MSCAL.Calendar.7"`

- CLSID,如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL,如`"<https://www.microsoft.com>"`

- 匯出文件的參考,例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段,例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必須在 HTML 片段之前,以便將其指定為 MSHTML 流。 Windows 行動平臺中僅支援 ProgID 和 CLSID。 Windows CE 嵌入式平臺(Windows Mobile 外,支援 CE IE)支援所有類型的內容,包括 ProgID、CLSID、URL、對活動文件的引用和 HTML 片段。

*pStream*<br/>
[在]指向用於初始化控制件屬性的流的指標。 可以是 NULL。

*ppUnk容器*<br/>
[出]將接收容器`IUnknown`的指標的位址。 可以是 NULL。

*德雷斯ID*<br/>
HTML 資源的資源識別碼。 Web瀏覽器控制項將建立並載入指定資源。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果使用此方法的第二個版本,則創建 HTML 控制項並將其綁定到*dwResID*識別的資源。

此方法為您提供與呼叫相同的結果:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

請參閱[CAxWindow2T::建立控制,](../../atl/reference/caxwindow2t-class.md#createcontrollic)以建立、初始化和託管許可的 ActiveX 控制件。

### <a name="example"></a>範例

有關`CreateControl`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAx 視窗:建立控制Ex

建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向字串的指標以建立控制項。 必須採用以下方式之一進行格式化:

- ProgID,如`"MSCAL.Calendar.7"`

- CLSID,如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL,如`"<https://www.microsoft.com>"`

- 匯出文件的參考,例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段,例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必須在 HTML 片段之前,以便將其指定為 MSHTML 流。 Windows 行動平臺中僅支援 ProgID 和 CLSID。 Windows CE 嵌入式平臺(Windows Mobile 外,支援 CE IE)支援所有類型的內容,包括 ProgID、CLSID、URL、對活動文件的引用和 HTML 片段。

*pStream*<br/>
[在]指向用於初始化控制件屬性的流的指標。 可以是 NULL。

*ppUnk容器*<br/>
[出]將接收容器`IUnknown`的指標的位址。 可以是 NULL。

*ppUnkControl*<br/>
[出]將接收控制項`IUnknown`的指標的位址。 可以是 NULL。

*iidSink*<br/>
[在]包含物件上傳出介面的介面標識符。 可以IID_NULL。

*龐克辛克*<br/>
[在]指向接收器物件`IUnknown`介面的指標,用於連接到*iidSink*指定的包含物件上的連接點。

*德雷斯ID*<br/>
[在]HTML 資源的資源識別碼。 Web瀏覽器控制項將建立並載入指定資源。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此方法類似於[CAxWindow::createControl](#createcontrol),但與該方法`CreateControlEx`不同, 還允許您接收指向新創建的控制項的介面指標,並設置事件接收器以接收控制項觸發的事件。

請參閱[CAxWindow2T::建立控制 LicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex)以建立、初始化和託管許可的 ActiveX 控制件。

### <a name="example"></a>範例

有關`CreateControlEx`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAx 視窗:抓取WndClass名稱

檢索視窗類的名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

指向一個字串的指標,其中包含可以承載無許可的 ActiveX 控件的視窗類的名稱。

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::運算符 |

將 HWND 分配`CAxWindow`給現有 物件。

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的句柄。

### <a name="return-value"></a>傳回值

傳回目前 `CAxWindow` 物件的參考。

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a>CAx 視窗:查詢控制

檢索托管控件的指定介面。

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]指定控制埠介面的 IID。

*普恩克*<br/>
[出]指向控件介面的指標。 在此方法的範本版本中,只要傳遞了具有關聯 UUID 的鍵入介面,就不需要引用 ID。

*Q*<br/>
[在]正在查詢的介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a>CAx 視窗::查詢主機

返回主機的指定介面。

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]指定控制埠介面的 IID。

*普恩克*<br/>
[出]指向主機上介面的指標。 在此方法的範本版本中,只要傳遞了具有關聯 UUID 的鍵入介面,就不需要引用 ID。

*Q*<br/>
[在]正在查詢的介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

主機的介面允許訪問由實現`AxWin`的視窗託管代碼的基礎功能。

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::設定外部調度

設置`CAxWindow`物件的外部調度介面。

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[在]指向介面的`IDispatch`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::設置外部UIHandler

設定`CAxWindow`物件的外部[IDocHostUIHandlerDispatch 介面](../../atl/reference/idochostuihandlerdispatch-interface.md)。

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>參數

*pUIHandler*<br/>
[在]指向介面的`IDocHostUIHandlerDispatch`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

外部`IDocHostUIHandlerDispatch`介面由查詢介面主機網站`IDocHostUIHandlerDispatch`的控制項使用。 Web瀏覽器控制項是執行此功能的一個控制項。

## <a name="see-also"></a>另請參閱

[ATLCON 樣品](../../overview/visual-cpp-samples.md)<br/>
[CWindow 類別](../../atl/reference/cwindow-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)
