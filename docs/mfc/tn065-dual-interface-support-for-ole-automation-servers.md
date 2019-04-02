---
title: TN065:Automation 伺服程式的雙重介面支援
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 33828f3979fb938ae6e88fa3cb0d6ee24daa958c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776670"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065:Automation 伺服程式的雙重介面支援

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本附註討論如何將雙重介面支援加入至 MFC 基礎 OLE Automation 伺服器應用程式。 [ACDUAL](../overview/visual-cpp-samples.md)範例說明雙重介面支援，並在此附註的範例程式碼取自 ACDUAL。 DECLARE_DUAL_ERRORINFO、 DUAL_ERRORINFO_PART，等 IMPLEMENT_DUAL_ERRORINFO，這個提示中所述的巨集是 ACDUAL 範例的一部分，而且可以 MFCDUAL 中找到。H.

## <a name="dual-interfaces"></a>雙重介面

雖然 OLE Automation 可讓您實作`IDispatch`介面、 VTBL 介面或雙重介面 （以包含這兩種情況），Microsoft 強烈建議您實作雙重介面，所有公開 OLE Automation 物件。 雙重介面上有顯著的優勢`IDispatch`-唯一或僅限 VTBL 介面：

- 繫結可以發生在編譯時期，透過 VTBL 介面，或在執行階段透過`IDispatch`。

- 可以使用 VTBL 介面的 OLE Automation 控制器可能會受益於更佳的效能。

- 現有的 OLE Automation 控制器來運用`IDispatch`介面將會繼續運作。

- VTBL 介面是從 c + + 呼叫的工作變得更容易。

- 雙重介面所需的 Visual Basic 物件支援的功能與相容性的。

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>將雙重介面支援加入至 CCmdTarget 類別

雙重介面是其實只是一種自訂介面衍生自`IDispatch`。 最直接的方法實作中的雙重介面支援`CCmdTarget`-基礎的類別是第一個正常的分派介面使用 MFC 和 ClassWizard，類別上，則稍後新增的自訂介面的實作。 大部分的情況下，您的自訂介面實作會直接委派回到 MFC`IDispatch`實作。

首先，修改您的伺服器，以定義您物件的雙重介面的 ODL 檔案。 若要定義雙重介面，您必須使用介面陳述式，而不是`DISPINTERFACE`Visual c + + 精靈產生的陳述式。 而不是移除現有`DISPINTERFACE`陳述式中，加入新的介面陳述式。 藉由保留`DISPINTERFACE`表單中，您可以繼續使用 ClassWizard 將屬性和方法新增至您的物件，但您必須將的對等的屬性和方法新增至您的介面陳述式。

雙重介面的介面陳述式必須有*OLEAUTOMATION*並*雙重*屬性和介面必須衍生自`IDispatch`。 您可以使用[GUIDGEN](../overview/visual-cpp-samples.md)範例，以建立**IID**雙重介面：

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

當您已備妥介面陳述式時，開始加入的方法和屬性的項目。 雙重介面，您需要重新排列參數清單，讓您的方法和雙重介面中的屬性存取子函式會傳回**HRESULT** ，並將其傳回值傳遞做為參數的屬性`[retval,out]`. 請記住，對於屬性，您必須將這兩個讀取 (`propget`) 和寫入 (`propput`) 存取函式具有相同識別碼。例如: 

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

定義方法和屬性之後，您需要在 coclass 陳述式加入介面陳述式的參考。 例如: 

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

ODL 檔案已更新之後，物件類別中定義的雙重介面的實作類別，並在 MFC 的對應項目中使用 MFC 的介面對應機制`QueryInterface`機制。 您需要在一個項目`INTERFACE_PART`區塊 ODL，介面陳述式中的每個項目，再加上分派介面的項目。 與每個 ODL 項目*propput*屬性需要名為函式`put_propertyname`。 與每個項目*propget*屬性需要名為函式`get_propertyname`。

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

要與 MFC 的雙重介面[QueryInterface](/windows/desktop/com/queryinterface--navigating-in-an-object)機制，新增`INTERFACE_PART`介面對應的項目：

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

接下來，您需要填寫介面的實作。 大部分的情況下，您可以在此處委派給現有的 MFC`IDispatch`實作。 例如: 

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

物件的方法和屬性存取子函式，您需要在實作填入。 您的方法和屬性函式通常可以回到使用 ClassWizard 所產生的方法委派。 不過，如果您直接存取變數設定屬性，您需要撰寫程式碼，以取得/放置值到變數。 例如: 

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

## <a name="passing-dual-interface-pointers"></a>將雙重介面指標傳遞

雙重介面指標傳遞不簡單，尤其是如果您需要呼叫`CCmdTarget::FromIDispatch`。 `FromIDispatch` 僅適用於 MFC 的`IDispatch`指標。 一種方式來解決這個問題是原始查詢`IDispatch`指標集由 MFC 及將該指標傳遞給需要它的函式。 例如: 

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

之前將指標傳遞回透過雙重介面方法，您可能需要將它從 MFC`IDispatch`雙重介面指標的指標。 例如: 

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

## <a name="registering-the-applications-type-library"></a>註冊應用程式的型別程式庫

AppWizard 不會產生向系統註冊 OLE Automation 伺服器應用程式的型別程式庫程式碼。 註冊類型程式庫的其他方法時，很方便地讓應用程式時它會更新其 OLE 型別資訊，也就每次執行獨立應用程式時，註冊類型程式庫。

若要註冊應用程式的型別程式庫每次執行應用程式時獨立項目：

- 包含 AFXCTL。在您的標準 H 包含標頭檔，STDAFX。H，若要存取的定義`AfxOleRegisterTypeLib`函式。

- 在您的應用程式`InitInstance`函式中，找出呼叫`COleObjectFactory::UpdateRegistryAll`。 遵循此呼叫，將呼叫加入`AfxOleRegisterTypeLib`，並指定**LIBID**對應至類型程式庫，以及您的型別程式庫的名稱：

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>修改專案組建設定，以配合型別程式庫的變更

若要修改的專案組建設定，讓標頭檔案，其中**UUID**定義會產生 MkTypLib 時就會重建型別程式庫：

1. 在上**建置**功能表上，按一下**設定**，然後從每個組態的檔案清單中選取 ODL 檔案。

2. 按一下 [ **OLE 類型**索引標籤，然後指定檔案名稱中的**輸出標頭**檔案名稱] 欄位。 因為 MkTypLib 將會覆寫任何現有的檔案，請使用已經不是專案，所使用的檔案名稱。 按一下 [ **[確定]** 以關閉**組建設定**] 對話方塊。

若要新增**UUID**從 MkTypLib 產生標頭檔至您的專案中的定義：

1. 包含 MkTypLib 產生在您的標準標頭檔包含標頭檔，STDAFX。H.

2. 建立新的檔案，INITIIDS。CPP，並將它新增至您的專案。 這個檔案中包含您 MkTypLib 產生標頭檔包含 OLE2 之後。H 和 INITGUID。H:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. 在 **建置** 功能表中，按一下**設定**，然後選取 INITIIDS。從檔案清單中的每個組態的 CPP。

4. 按一下  **c + +** 索引標籤上，按一下 類別**先行編譯標頭**，然後選取**未使用先行編譯標頭**選項按鈕。 按一下 確定 以關閉**組建設定** 對話方塊。

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>類型程式庫中指定正確的物件類別名稱

不正確地使用 Visual c + + 隨附的精靈會使用實作類別名稱來指定伺服器的 OLE 可建立類別的 ODL 檔案中的 coclass。 雖然這將會運作，實作類別名稱可能不是您想要使用物件的使用者的類別名稱。 若要指定正確的名稱，開啟 ODL 檔案，找出每個 coclass 陳述式，並實作類別名稱取代為正確的外部名稱。

請注意，coclass 陳述式變更時，變數的名稱**CLSID**MkTypLib 產生標頭檔中也會跟著變更。 您必須更新您的程式碼，以使用新的變數名稱。

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>處理例外狀況和自動化錯誤介面

Automation 物件的方法和屬性存取子函式可能會擲回例外狀況。 因此，您應該在雙重介面實作中處理它們，並傳遞例外狀況資訊傳回至控制器透過 OLE Automation 錯誤處理介面，如果`IErrorInfo`。 這個介面提供詳細的內容相關錯誤資訊透過`IDispatch`和 VTBL 介面。 若要指出的錯誤處理常式使用，您應該實作`ISupportErrorInfo`介面。

為了說明的錯誤處理機制，假設用來實作標準的分派支援 ClassWizard 產生函式擲回例外狀況。 MFC 實作`IDispatch::Invoke`通常會攔截這些例外狀況，並將它們轉換成經由傳回 EXCEPTINFO 結構`Invoke`呼叫。 不過，使用 VTBL 介面時，您會負責自行攔截例外狀況。 為保護您的雙重介面方法的範例：

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

`CATCH_ALL_DUAL` 會負責傳回正確的錯誤程式碼時發生例外狀況。 `CATCH_ALL_DUAL` 將 MFC 例外狀況轉換成 OLE Automation 錯誤處理資訊使用`ICreateErrorInfo`介面。 (範例`CATCH_ALL_DUAL`巨集是 MFCDUAL 檔案中。在 H [ACDUAL](../overview/visual-cpp-samples.md)範例。 若要處理的例外狀況，呼叫函式`DualHandleException`，MFCDUAL 檔案中。CPP。)`CATCH_ALL_DUAL`決定傳回根據發生的例外狀況類型的錯誤程式碼：

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) -在此情況下，`HRESULT`建構是使用下列程式碼：

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   這會建立`HRESULT`特定至造成例外狀況的介面。 錯誤碼偏移成 0x200 以避免任何系統定莪 je v konfliktu`HRESULT`的標準 OLE 介面。

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) -在此情況下，`E_OUTOFMEMORY`會傳回。

- 任何其他例外狀況-在此情況下，`E_UNEXPECTED`會傳回。

若要指出會使用 OLE Automation 錯誤處理常式，您也應該實作`ISupportErrorInfo`介面。

首先，將程式碼加入您的自動化類別定義，以顯示它支援`ISupportErrorInfo`。

第二，將程式碼加入您的自動化類別建立關聯的介面對應`ISupportErrorInfo`MFC 的實作類別`QueryInterface`機制。 `INTERFACE_PART`陳述式符合定義的類別`ISupportErrorInfo`。

最後，實作類別定義，以支援`ISupportErrorInfo`。

( [ACDUAL](../overview/visual-cpp-samples.md)範例包含三個巨集，以執行下列三個步驟，幫助`DECLARE_DUAL_ERRORINFO`， `DUAL_ERRORINFO_PART`，和`IMPLEMENT_DUAL_ERRORINFO`MFCDUAL 中全部包含。H.)

下列範例會實作類別定義，以支援`ISupportErrorInfo`。 `CAutoClickDoc` 是您的自動化類別的名稱和`IID_IDualAClick`已**IID**的介面，是透過 OLE Automation 錯誤物件所報告的錯誤來源：

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
