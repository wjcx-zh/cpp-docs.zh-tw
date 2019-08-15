---
title: TN065：OLE Automation 伺服器的雙重介面支援
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: afcbfd643d8b931e61b0f011b66482be5b2bcc82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510994"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065：OLE Automation 伺服器的雙重介面支援

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此附注討論如何將雙重介面支援新增至 MFC 型 OLE Automation 伺服器應用程式。 [Acdual:](../overview/visual-cpp-samples.md)範例說明雙重介面支援, 而此附注中的範例程式碼取自 acdual:。 此注意事項中所述的宏 (例如 DECLARE_DUAL_ERRORINFO、DUAL_ERRORINFO_PART 和 IMPLEMENT_DUAL_ERRORINFO) 是 ACDUAL: 範例的一部分, 可以在 MFCDUAL 中找到。H.

## <a name="dual-interfaces"></a>雙重介面

雖然 OLE Automation 可讓您實作為`IDispatch`介面、VTBL 介面或雙重介面 (其中包含兩者), 但 Microsoft 強烈建議您為所有公開的 OLE Automation 物件執行雙重介面。 雙重介面具有優於`IDispatch`或僅限 VTBL 介面的重要優點:

- 系結可以在編譯時期透過 VTBL 介面來進行, 或在執行時間透過`IDispatch`執行。

- 可以使用 VTBL 介面的 OLE Automation 控制器可受益于改善的效能。

- 使用`IDispatch`介面的現有 OLE Automation 控制器會繼續工作。

- VTBL 介面較容易從C++呼叫。

- 需要雙重介面, 才能與 Visual Basic 物件支援功能相容。

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>將雙重介面支援新增至以 CCmdTarget 為基礎的類別

雙重介面其實只是從`IDispatch`衍生的自訂介面。 在以為基礎的類別中`CCmdTarget`執行雙重介面支援最直接的方式, 是先使用 MFC 和 ClassWizard 在您的類別上執行一般分派介面, 然後在稍後新增自訂介面。 在大部分的情況下, 您的自訂介面執行只會委派回到`IDispatch` MFC 的執行。

首先, 修改您伺服器的 ODL 檔, 以定義物件的雙重介面。 若要定義雙重介面, 您必須使用介面語句, 而不是視覺`DISPINTERFACE`效果C++嚮導所產生的語句。 請加入新的介面`DISPINTERFACE`語句, 而不是移除現有的語句。 藉由保留`DISPINTERFACE`表單, 您可以繼續使用 ClassWizard 將屬性和方法新增至您的物件, 但您必須將對等的屬性和方法加入至您的介面語句。

雙重介面的介面語句必須具有*OLEAUTOMATION*和*雙重*屬性, 而且介面必須衍生自`IDispatch`。 您可以使用[GUIDGEN](../overview/visual-cpp-samples.md)範例來建立雙重介面的**IID** :

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

備妥介面語句之後, 開始加入方法和屬性的專案。 針對雙重介面, 您需要重新排列參數清單, 讓雙重介面中的方法和屬性存取子函式傳回**HRESULT** , 並以參數的形式傳遞其傳回值做`[retval,out]`為屬性。 請記住, 針對屬性, 您必須同時新增具有相同識別碼的`propget`read () 和`propput`write () 存取函數。例如：

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

定義方法和屬性之後, 您必須將參考加入至 coclass 語句中的介面語句。 例如：

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

更新 ODL 檔案之後, 請使用 MFC 的介面對應機制來定義物件類別中雙重介面的實作為類別, 並在 MFC 的`QueryInterface`機制中進行對應的專案。 在 ODL 的介面語句中`INTERFACE_PART` , 每個專案的區塊中都需要一個專案, 再加上分派介面的專案。 具有*propput*屬性的每個 ODL 專案都需要名`put_propertyname`為的函式。 具有*propget*屬性的每個專案都需要名`get_propertyname`為的函式。

若要定義雙重介面的實類別, 請在物件`DUAL_INTERFACE_PART`類別定義中加入區塊。 例如：

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

若要將雙重介面連接到 MFC 的[QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object)機制, 請`INTERFACE_PART`在介面對應中新增一個專案:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

接下來, 您需要填入介面的實作為。 在大部分的情況下, 您將能夠委派至現有的 MFC `IDispatch`執行。 例如：

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

對於物件的方法和屬性存取子函式, 您需要填入實作為。 您的方法和屬性函數通常可以委派回到使用 ClassWizard 產生的方法。 不過, 如果您將屬性設定為直接存取變數, 則需要撰寫程式碼以取得/將值放入變數中。 例如：

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>傳遞雙重介面指標

傳遞雙重介面指標並不簡單, 特別是在您需要呼叫`CCmdTarget::FromIDispatch`的情況下。 `FromIDispatch`僅適用于 MFC 的`IDispatch`指標。 解決這個情況的方法之一, 是查詢 MFC 所設定`IDispatch`的原始指標, 並將該指標傳遞給需要它的函式。 例如：

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

將指標傳回到雙重介面方法之前, 您可能需要將它從 MFC `IDispatch`指標轉換成雙介面指標。 例如：

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>註冊應用程式的類型程式庫

執行程式碼段不會產生可向系統註冊 OLE Automation 伺服器應用程式類型程式庫的程式碼。 雖然還有其他方式可以註冊類型程式庫, 但應用程式在更新其 OLE 類型資訊時 (也就是每當應用程式獨立執行時) 註冊類型程式庫會很方便。

每當應用程式獨立執行時, 註冊應用程式的類型程式庫:

- 包含 AFXCTL.H。H 在您的標準中包括標頭檔 (STDAFX.H)。H: 存取`AfxOleRegisterTypeLib`函數的定義。

- 在應用程式的`InitInstance`函式中, 找出`COleObjectFactory::UpdateRegistryAll`對的呼叫。 在此呼叫之後, 新增對`AfxOleRegisterTypeLib`的呼叫, 並指定對應至您類型程式庫的**LIBID** , 以及類型程式庫的名稱:

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>修改專案組建設定以配合類型程式庫變更

若要修改專案的組建設定, 讓包含**UUID**定義的標頭檔在每次重建型別程式庫時由 mktyplib.exe 產生:

1. 在 [**建立**] 功能表上, 按一下 [設定], 然後從 [檔案] 清單中選取每個**設定**的 ODL 檔案。

2. 按一下 [ **OLE 類型**] 索引標籤, 並在 [**輸出頭**檔案] 欄位中指定檔案名。 使用專案尚未使用的檔案名, 因為 Mktyplib.exe 會覆寫任何現有的檔案。 按一下 **[確定]** 以關閉 [**組建設定**] 對話方塊。

若要將 Mktyplib.exe 產生的標頭檔中的**UUID**定義新增至您的專案:

1. 在您的標準中包含 Mktyplib.exe 產生的標頭檔, 包括標頭檔 (STDAFX.H)。H.

2. 建立新的檔案 INITIIDS。CPP, 然後將它新增至您的專案。 在此檔案中, 請在包含 OLE2 之後包含 Mktyplib.exe 產生的標頭檔。H 和 d。H

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. 在 [**建立**] 功能表上, 按一下 [**設定**], 然後選取 [INITIIDS]。每個設定的檔案清單中的 CPP。

4. 按一下索引**C++** 標籤, 再按一下 [類別先行**編譯頭**檔], 然後選取 [**未使用先行編譯頭**檔] 選項按鈕。 按一下 [確定] 以關閉 [**組建設定**] 對話方塊。

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>在類型程式庫中指定正確的物件類別名稱

Visual C++隨附的程式不正確地使用實作為類別名稱, 在伺服器的 ODL 檔中指定 coclass 以用於 OLE 可新增的類別。 雖然這是可行的, 但實作為類別名稱可能不是您想要讓物件的使用者使用的類別名稱。 若要指定正確的名稱, 請開啟 ODL 檔案, 找出每個 coclass 語句, 然後以正確的外部名稱取代執行類別名稱。

請注意, 當 coclass 語句變更時, 在 Mktyplib.exe 產生的標頭檔中, **CLSID**的變數名稱會隨之變更。 您必須更新您的程式碼, 以使用新的變數名稱。

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>處理例外狀況和自動化錯誤介面

您的 automation 物件的方法和屬性存取子函數可能會擲回例外狀況。 若是如此, 您應該在雙重介面的執行中處理它們, 並透過 OLE Automation 錯誤處理介面`IErrorInfo`將例外狀況的相關資訊傳遞回控制器。 這個介面會透過`IDispatch`和 VTBL 介面, 提供詳細的內容相關錯誤資訊。 若要指出有錯誤處理常式可供使用, 您應該`ISupportErrorInfo`執行介面。

為了說明錯誤處理機制, 假設用來執行標準分派支援的 ClassWizard 產生函數會擲回例外狀況。 MFC 的執行`IDispatch::Invoke`通常會攔截這些例外狀況, 並將它們轉換成`Invoke`透過呼叫所傳回的 EXCEPTINFO 結構。 不過, 使用 VTBL 介面時, 您會負責自行捕捉例外狀況。 保護雙重介面方法的範例如下:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL`會在例外狀況發生時, 負責傳回正確的錯誤碼。 `CATCH_ALL_DUAL`使用介面, `ICreateErrorInfo`將 MFC 例外狀況轉換成 OLE Automation 錯誤處理資訊。 (範例`CATCH_ALL_DUAL`宏位於檔案 MFCDUAL 中。H 在[acdual:](../overview/visual-cpp-samples.md)範例中。 它呼叫來處理例外`DualHandleException`狀況的函式是在檔案 MFCDUAL 中。CPP)。`CATCH_ALL_DUAL`根據發生的例外狀況類型, 判斷要傳回的錯誤碼:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) -在此情況下`HRESULT` , 會使用下列程式碼來進行結構化:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   這會`HRESULT`針對造成例外狀況的介面建立特定的。 錯誤碼會由0x200 位移, 以避免與系統定義`HRESULT`的對標準 OLE 介面產生任何衝突。

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) -在此情況下`E_OUTOFMEMORY` , 會傳回。

- 任何其他例外狀況 (在此案例`E_UNEXPECTED`中為) 都會傳回。

若要指出使用 OLE Automation 錯誤處理常式, 您也應該執行`ISupportErrorInfo`介面。

首先, 將程式碼新增至您的 automation 類別定義, `ISupportErrorInfo`以顯示其支援。

第二, 將程式碼加入至您的 automation 類別的介面`ISupportErrorInfo`對應, 以將此`QueryInterface`實類別與 MFC 的機制產生關聯。 語句符合針對`ISupportErrorInfo`定義的類別。 `INTERFACE_PART`

最後, 執行定義為支援`ISupportErrorInfo`的類別。

( [Acdual:](../overview/visual-cpp-samples.md)範例包含三個宏, 可協助您執行這三`DECLARE_DUAL_ERRORINFO`個`DUAL_ERRORINFO_PART`步驟: `IMPLEMENT_DUAL_ERRORINFO`、和, 全都包含在 MFCDUAL 中。H)。

下列範例會執行定義為支援`ISupportErrorInfo`的類別。 `CAutoClickDoc`是您的 automation 類別的名稱, `IID_IDualAClick`而是介面的**IID** , 它是透過 OLE automation 錯誤物件所報告的錯誤來源:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
