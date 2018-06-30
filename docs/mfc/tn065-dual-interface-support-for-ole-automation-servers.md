---
title: 'TN065: OLE automation 伺服程式的雙重介面支援 |Microsoft 文件'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.ole
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e30be46aeab92f63f1b4cba593cda52bf9aeef9a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122179"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065：OLE Automation 伺服程式的雙重介面支援

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示會討論如何以 MFC 為基礎 OLE Automation 伺服器應用程式中加入的雙重介面支援。 [ACDUAL](../visual-cpp-samples.md)範例說明的雙重介面支援，以及這個附註的範例程式碼取自 ACDUAL。 此附註，例如 DECLARE_DUAL_ERRORINFO、 DUAL_ERRORINFO_PART 和 IMPLEMENT_DUAL_ERRORINFO，所述巨集 ACDUAL 範例的一部分，而且可以 MFCDUAL 中找到。H.

## <a name="dual-interfaces"></a>雙重介面

雖然 OLE Automation 可讓您實作`IDispatch`介面、 VTBL 介面或雙重介面 （其中包含這兩種情況），Microsoft 強烈建議您實作雙重介面，所有公開 OLE Automation 物件。 雙重介面上有顯著的優勢`IDispatch`-唯一或僅限 VTBL 介面：

- 繫結可發生在編譯時期透過 VTBL 介面，或在執行階段透過`IDispatch`。

- 可以使用 VTBL 介面的 OLE Automation 控制器可能受益於更佳的效能。

- 使用的現有 OLE Automation 控制器`IDispatch`介面將會繼續運作。

- VTBL 介面是您更輕鬆地從 c + + 呼叫。

- 雙重介面所需的相容性 Visual Basic 物件支援的功能。

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>雙重介面支援加入 CCmdTarget 類別

雙重介面是其實只是自訂介面衍生自`IDispatch`。 最簡單的方式來實作中的雙重介面支援`CCmdTarget`-基礎的類別是正常的分派介面上使用 MFC 和類別，您的類別，然後稍後新增自訂介面的第一個實作。 大部分的情況下，您的自訂介面實作會將只是委派至 MFC`IDispatch`實作。

首先，修改您的伺服器定義為物件的雙重介面的 ODL 檔案。 若要定義雙重介面，您必須使用介面陳述式，而不是`DISPINTERFACE`Visual c + + 精靈產生的陳述式。 而不是移除現有`DISPINTERFACE`陳述式中，加入新的介面陳述式。 藉由保留`DISPINTERFACE`表單中，您可以繼續使用 ClassWizard 將屬性和方法新增至您的物件，但您必須將的對等的屬性和方法，加入您的介面陳述式。

雙重介面的介面陳述式必須有*OLEAUTOMATION*和*雙重*屬性和介面必須衍生自`IDispatch`。 您可以使用[GUIDGEN](../visual-cpp-samples.md)範例建立**IID**雙重介面：

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

一旦您已備妥介面陳述式，開始加入的方法和屬性的項目。 雙重介面，您需要重新排列參數清單，因此，您的方法和雙重介面中的屬性存取子函式傳回**HRESULT** ，並將其傳回值傳遞做為參數的屬性`[retval,out]`. 請記住，對於屬性，您必須加入兩個讀取 (`propget`) 和寫入 (`propput`) 存取函式具有相同的識別碼。例如: 

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

您的方法和屬性會定義之後，您需要在 coclass 陳述式中加入介面陳述式的參考。 例如: 

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

ODL 檔案已更新，一旦使用 MFC 的介面對應機制來定義物件類別中的雙重介面的實作類別，並建立 MFC 的對應項目`QueryInterface`機制。 您需要在一個項目`INTERFACE_PART`區塊 ODL，介面陳述式中的每個項目加上分派介面的項目。 每個 ODL 項*propput*屬性需要名為函式`put_propertyname`。 與每個項目*propget*屬性需要名為函式`get_propertyname`。

若要定義您的雙重介面的實作類別，新增`DUAL_INTERFACE_PART`物件類別定義的區塊。 例如: 

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

若要連接至 MFC 的雙重介面[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230)機制，新增`INTERFACE_PART`介面對應的項目：

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

接著，您必須填寫介面的實作。 大部分的情況下，您將能夠委派給現有的 MFC`IDispatch`實作。 例如: 

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

物件的方法和屬性存取子函式，您需要在實作填滿。 方法和屬性函式通常可以回到使用 ClassWizard 所產生的方法委派。 不過，如果您直接存取變數設定屬性，您需要撰寫程式碼以取得/放置值到變數。 例如: 

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

雙重介面指標傳遞並不簡單，特別是當您需要呼叫`CCmdTarget::FromIDispatch`。 `FromIDispatch` 只適用於 MFC 的`IDispatch`指標。 一種方式來解決這個問題是原始查詢`IDispatch`指標集由 MFC 並將該指標傳遞至需要的函數。 例如: 

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

之前將指標傳遞回透過雙重介面方法，您可能需要將它從 MFC 轉換`IDispatch`雙重介面指標的指標。 例如: 

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

AppWizard 不會產生程式碼，以註冊系統 OLE Automation 伺服器應用程式的型別程式庫。 註冊類型程式庫的其他方法時，並方便註冊類型程式庫，當它更新其 OLE 類型資訊時，也就每次執行獨立應用程式時將應用程式。

若要註冊應用程式的型別程式庫每次執行應用程式時獨立：

- 包含 AFXCTL。在您的標準 H 包括 STDAFX，標頭檔。H、 存取的定義`AfxOleRegisterTypeLib`函式。

- 在您的應用程式中`InitInstance`函式中，找出呼叫`COleObjectFactory::UpdateRegistryAll`。 遵循此呼叫，將呼叫加入`AfxOleRegisterTypeLib`，並指定**LIBID**對應至類型程式庫，以及您的型別程式庫的名稱：

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>修改專案組建設定，以配合型別程式庫變更

若要修改專案的建置設定，讓一個標頭檔，其中包含**UUID**每當類型程式庫會重建 MkTypLib 便產生定義：

1. 在**建置**功能表上，按一下 **設定**，然後從每個組態檔清單中選取 ODL 檔案。

2. 按一下**OLE 類型**索引標籤，然後指定檔案名稱中的**輸出標頭**檔案名稱 欄位。 因為 MkTypLib 將覆寫任何現有的檔案，請使用不已經由您的專案檔名。 按一下**確定**關閉**組建設定** 對話方塊。

若要加入**UUID** MkTypLib 產生標頭檔至您的專案中的定義：

1. 包含 MkTypLib 產生您的標準標頭檔包含 STDAFX，標頭檔。H.

2. 建立新的檔案，INITIIDS。CPP，並將它加入至您的專案。 這個檔案中包含您 MkTypLib 產生標頭檔加入 OLE2 之後。H 和 INITGUID。H:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. 在**建置**功能表上，按一下 **設定**，然後選取 INITIIDS。CPP 檔案清單，每個組態。

4. 按一下**c + +** 索引標籤上，按一下 [類別]**先行編譯標頭**，然後選取**未使用先行編譯標頭**選項按鈕。 按一下 確定 關閉**組建設定** 對話方塊。

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>類型程式庫中指定正確的物件類別名稱

隨附於 Visual c + + 不正確的精靈會使用實作類別名稱，來指定伺服器 ODL 檔案，可建立 OLE 類別中的 coclass。 這也能運作，而實作的類別名稱可能不是您想要使用物件的使用者的類別名稱。 若要指定正確的名稱，開啟 ODL 檔案，找出每個 coclass 陳述式，並實作類別名稱取代為正確的外部名稱。

請注意，當 coclass 陳述式變更時，變數名稱的**CLSID**MkTypLib 產生標頭檔中也會跟著變更。 您必須更新程式碼以使用新的變數名稱。

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>處理例外狀況和自動化錯誤介面

Automation 物件的方法和屬性存取子函式可能會擲回例外狀況。 因此，您應該雙重介面實作中處理它們，並將例外狀況資訊傳回透過 OLE Automation 錯誤處理介面、 控制站如果`IErrorInfo`。 這個介面提供內容、 詳細的錯誤資訊同時透過`IDispatch`和 VTBL 介面。 若要指出的錯誤處理常式使用，您應該實作`ISupportErrorInfo`介面。

為了說明錯誤處理機制，假設用來實作的標準分派支援 ClassWizard 產生函式擲回例外狀況。 MFC 實作`IDispatch::Invoke`通常會攔截這些例外狀況，並將其轉換透過傳回 EXCEPTINFO 結構`Invoke`呼叫。 不過，當使用 VTBL 介面時，您必須負責自行攔截例外狀況。 為保護您的雙重介面方法的範例：

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

`CATCH_ALL_DUAL` 處理的例外狀況發生時，傳回正確的錯誤碼。 `CATCH_ALL_DUAL` 將 MFC 例外狀況轉換成 OLE Automation 錯誤處理資訊使用`ICreateErrorInfo`介面。 (範例`CATCH_ALL_DUAL`巨集是 MFCDUAL 檔案中。在 H [ACDUAL](../visual-cpp-samples.md)範例。 若要處理的例外狀況，呼叫函式`DualHandleException`，MFCDUAL 檔案中。CPP。)`CATCH_ALL_DUAL`決定傳回根據發生的例外狀況類型的錯誤程式碼：

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) -在此情況下，`HRESULT`建構是使用下列程式碼：

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     這會建立`HRESULT`特有造成例外狀況的介面。 錯誤碼可經由 0x200 以避免與系統定義的任何衝突`HRESULT`s 標準 OLE 介面。

- [Afxthrowmemoryexception](../mfc/reference/cmemoryexception-class.md) -在此情況下，`E_OUTOFMEMORY`傳回。

- 任何其他例外狀況-在此情況下，`E_UNEXPECTED`傳回。

若要表示使用 OLE Automation 錯誤處理常式，您也應該實作`ISupportErrorInfo`介面。

首先，將程式碼加入您的自動化類別定義，以顯示其支援`ISupportErrorInfo`。

第二，將程式碼加入 automation 類別的介面對應關聯`ISupportErrorInfo`與 MFC 的實作類別`QueryInterface`機制。 `INTERFACE_PART`陳述式符合定義的類別`ISupportErrorInfo`。

最後，實作類別定義，以支援`ISupportErrorInfo`。

( [ACDUAL](../visual-cpp-samples.md)範例包含三個巨集來執行這三個步驟，幫助`DECLARE_DUAL_ERRORINFO`， `DUAL_ERRORINFO_PART`，和`IMPLEMENT_DUAL_ERRORINFO`，所有包含 MFCDUAL 中。H.)

下列範例會實作定義以支援的類別`ISupportErrorInfo`。 `CAutoClickDoc` automation 類別的名稱和`IID_IDualAClick`是**IID**是透過 OLE Automation 錯誤物件所報告的錯誤來源的介面：

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

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)  
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)  
