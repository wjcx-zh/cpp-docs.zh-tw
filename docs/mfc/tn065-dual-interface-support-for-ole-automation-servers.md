---
title: "TN065: OLE automation 伺服程式的雙重介面支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.ole
dev_langs: C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 959938be27e66a765ee0ae9e5aef9b3c1f1aed6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065：OLE Automation 伺服程式的雙重介面支援
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 此提示會討論如何以 MFC 為基礎 OLE Automation 伺服器應用程式中加入的雙重介面支援。 [ACDUAL](../visual-cpp-samples.md)範例說明的雙重介面支援，以及這個附註的範例程式碼取自 ACDUAL。 此附註所述，這類的巨集`DECLARE_DUAL_ERRORINFO`， `DUAL_ERRORINFO_PART`，和`IMPLEMENT_DUAL_ERRORINFO`、 ACDUAL 範例的一部分，而且可以位於 MFCDUAL。H.  
  
## <a name="dual-interfaces"></a>雙重介面  
 雖然 OLE Automation 可讓您實作`IDispatch`介面、 VTBL 介面或雙重介面 （其中包含這兩種情況），Microsoft 強烈建議您實作雙重介面，所有公開 OLE Automation 物件。 雙重介面上有顯著的優勢`IDispatch`-唯一或僅限 VTBL 介面：  
  
-   繫結可發生在編譯時期透過 VTBL 介面，或在執行階段透過`IDispatch`。  
  
-   可以使用 VTBL 介面的 OLE Automation 控制器可能受益於更佳的效能。  
  
-   使用的現有 OLE Automation 控制器`IDispatch`介面將會繼續運作。  
  
-   VTBL 介面是您更輕鬆地從 c + + 呼叫。  
  
-   雙重介面所需的相容性 Visual Basic 物件支援的功能。  
  
## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>雙重介面支援加入 CCmdTarget 類別  
 雙重介面是其實只是自訂介面衍生自`IDispatch`。 最簡單的方式來實作中的雙重介面支援`CCmdTarget`-基礎的類別是正常的分派介面上使用 MFC 和類別，您的類別，然後稍後新增自訂介面的第一個實作。 大部分的情況下，您的自訂介面實作會將只是委派至 MFC`IDispatch`實作。  
  
 首先，修改您的伺服器定義為物件的雙重介面的 ODL 檔案。 若要定義雙重介面，您必須使用介面陳述式，而不是`DISPINTERFACE`Visual c + + 精靈產生的陳述式。 而不是移除現有`DISPINTERFACE`陳述式中，加入新的介面陳述式。 藉由保留`DISPINTERFACE`表單中，您可以繼續使用 ClassWizard 將屬性和方法新增至您的物件，但您必須將的對等的屬性和方法，加入您的介面陳述式。  
  
 雙重介面的介面陳述式必須有**OLEAUTOMATION**和**雙重**屬性和介面必須衍生自`IDispatch`。 您可以使用[GUIDGEN](../visual-cpp-samples.md)範例建立**IID**雙重介面：  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
    oleautomation, 
    dual 
]  
interface IDualAClick : IDispatch  
 {  
 };  
```  
  
 一旦您已備妥介面陳述式，開始加入的方法和屬性的項目。 雙重介面，您需要重新排列參數清單，因此，您的方法和雙重介面中的屬性存取子函式傳回`HRESULT`，並將其傳回值傳遞做為參數的屬性`[retval,out]`。 請記住，對於屬性，您必須加入兩個讀取 (`propget`) 和寫入 (`propput`) 存取函式具有相同的識別碼。例如:   
  
```  
[propput,
    id(1)] HRESULT text([in] BSTR newText);

[propget,
    id(1)] HRESULT text([out,
    retval] BSTR* retval);
```  
  
 您的方法和屬性會定義之後，您需要在 coclass 陳述式中加入介面陳述式的參考。 例如:   
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
    dispinterface IAClick;  
 [default] interface IDualAClick;  
};  
```  
  
 ODL 檔案已更新，一旦使用 MFC 的介面對應機制來定義物件類別中的雙重介面的實作類別，並建立 MFC 的對應項目`QueryInterface`機制。 您需要在一個項目`INTERFACE_PART`區塊 ODL，介面陳述式中的每個項目加上分派介面的項目。 每個 ODL 項**propput**屬性需要名為函式`put_propertyname`。 與每個項目**propget**屬性需要名為函式`get_propertyname`。  
  
 若要定義您的雙重介面的實作類別，新增`DUAL_INTERFACE_PART`物件類別定義的區塊。 例如:   
  
```  
BEGIN_DUAL_INTERFACE_PART(DualAClick,
    IDualAClick)  
    STDMETHOD(put_text)(THIS_ BSTR newText);

    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);

    STDMETHOD(put_x)(THIS_ short newX);

    STDMETHOD(get_x)(THIS_ short FAR* retval);

    STDMETHOD(put_y)(THIS_ short newY);

    STDMETHOD(get_y)(THIS_ short FAR* retval);

    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);

    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);

    STDMETHOD(RefreshWindow)(THIS);

 STDMETHOD(SetAllProps)(THIS_ short x,
    short y,
    BSTR text);

    STDMETHOD(ShowWindow)(THIS);

END_DUAL_INTERFACE_PART(DualAClick) 
```  
  
 若要連接至 MFC 的雙重介面[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230)機制，新增`INTERFACE_PART`介面對應的項目：  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc,
    CDocument)  
    INTERFACE_PART(CAutoClickDoc,
    DIID_IAClick,
    Dispatch)  
    INTERFACE_PART(CAutoClickDoc,
    IID_IDualAClick,
    DualAClick)  
END_INTERFACE_MAP()  
```  
  
 接著，您必須填寫介面的實作。 大部分的情況下，您將能夠委派給現有的 MFC`IDispatch`實作。 例如:   
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalAddRef();

}  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalRelease();

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfoCount(pctinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo,
    lcid,
    pptinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,  
    LCID lcid,
    DISPID FAR* rgdispid)   
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid,
    rgszNames,
    cNames,   
    lcid,
    rgdispid);

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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember,
    riid,
    lcid,  
    wFlags,
    pdispparams,
    pvarResult,  
    pexcepinfo,
    puArgErr);

}  
```  
  
 物件的方法和屬性存取子函式，您需要在實作填滿。 方法和屬性函式通常可以回到使用 ClassWizard 所產生的方法委派。 不過，如果您直接存取變數設定屬性，您需要撰寫程式碼以取得/放置值到變數。 例如:   
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Unicode BSTR to *// Ansi CString,
    if necessary...  
    pThis->m_str = newText;  
    return NOERROR;  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Ansi CString to *// Unicode BSTR,
    if necessary...  
    pThis->m_str.SetSysString(retval);

 return NOERROR;  
}  
```  
  
## <a name="passing-dual-interface-pointers"></a>傳遞雙重介面指標  
 雙重介面指標傳遞並不簡單，特別是當您需要呼叫`CCmdTarget::FromIDispatch`。 `FromIDispatch`只適用於 MFC 的`IDispatch`指標。 一種方式來解決這個問題是原始查詢`IDispatch`指標集由 MFC 並將該指標傳遞至需要的函數。 例如:   
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp;  
    lpDisp = pThis->GetPosition();
lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);

    return NOERROR;  
}  
```  
  
## <a name="registering-the-applications-type-library"></a>註冊應用程式的類型程式庫  
 AppWizard 不會產生程式碼，以註冊系統 OLE Automation 伺服器應用程式的型別程式庫。 註冊類型程式庫的其他方法時，並方便註冊類型程式庫，當它更新其 OLE 類型資訊時，也就每次執行獨立應用程式時將應用程式。  
  
 若要註冊應用程式的型別程式庫每次執行應用程式時獨立：  
  
-   包含 AFXCTL。在您的標準 H 包括 STDAFX，標頭檔。H、 存取的定義`AfxOleRegisterTypeLib`函式。  
  
-   在您的應用程式中`InitInstance`函式中，找出呼叫`COleObjectFactory::UpdateRegistryAll`。 遵循此呼叫，將呼叫加入`AfxOleRegisterTypeLib`，並指定**LIBID**對應至類型程式庫，以及您的型別程式庫的名稱：  
  
 '' * / / 伺服器應用程式啟動時獨立的所以最好 * / / 到更新系統登錄，以防已損毀。  
    m_server。UpdateRegistry(OAT_DISPATCH_OBJECT);

 COleObjectFactory::UpdateRegistryAll();* / DUAL_SUPPORT_START * / / 請確定已註冊型別程式庫，或雙重介面將無法運作。  
AfxOleRegisterTypeLib(AfxGetInstanceHandle()，LIBID_ACDual，_T("AutoClik.TLB"));* / DUAL_SUPPORT_END  
 ```  
  
## Modifying Project Build Settings to Accommodate Type Library Changes  
 To modify a project's build settings so that a header file containing **UUID** definitions is generated by MkTypLib whenever the type library is rebuilt:  
  
1.  On the **Build** menu, click **Settings**, and then select the ODL file from the file list for each configuration.  
  
2.  Click the **OLE Types** tab and specify a filename in the **Output header** filename field. Use a filename that is not already used by your project, because MkTypLib will overwrite any existing file. Click **OK** to close the **Build Settings** dialog box.  
  
 To add the **UUID** definitions from the MkTypLib-generated header file to your project:  
  
1.  Include the MkTypLib-generated header file in your standard includes header file, STDAFX.H.  
  
2.  Create a new file, INITIIDS.CPP, and add it to your project. In this file, include your MkTypLib-generated header file after including OLE2.H and INITGUID.H:  
  
 ```  
    initIIDs.c： 定義 Iid 雙重介面  
    這必須不建置先行編譯標頭。  
      #<a name="include-ole2h"></a>包含 < ole2.h >  
      #<a name="include-initguidh"></a>包含 < h >  
      #<a name="include-acdualh"></a>包含 「 acdual.h"  
 ```  
  
3.  On the **Build** menu, click **Settings**, and then select INITIIDS.CPP from the file list for each configuration.  
  
4.  Click the **C++** tab, click category **Precompiled Headers**, and select the **Not using precompiled headers** radio button. Click OK to close the **Build Settings** dialog box.  
  
## Specifying the Correct Object Class Name in the Type Library  
 The wizards shipped with Visual C++ incorrectly use the implementation class name to specify the coclass in the server's ODL file for OLE-creatable classes. While this will work, the implementation class name is probably not the class name you want users of your object to use. To specify the correct name, open the ODL file, locate each coclass statement, and replace the implementation class name with the correct external name.  
  
 Note that when the coclass statement is changed, the variable names of **CLSID**s in the MkTypLib-generated header file will change accordingly. You will need to update your code to use the new variable names.  
  
## Handling Exceptions and the Automation Error Interfaces  
 Your automation object's methods and property accessor functions may throw exceptions. If so, you should handle them in your dual-interface implementation and pass information about the exception back to the controller through the OLE Automation error-handling interface, **IErrorInfo**. This interface provides for detailed, contextual error information through both `IDispatch` and VTBL interfaces. To indicate that an error handler is available, you should implement the **ISupportErrorInfo** interface.  
  
 To illustrate the error-handling mechanism, assume that the ClassWizard-generated functions used to implement the standard dispatch support throw exceptions. MFC's implementation of **IDispatch::Invoke** typically catches these exceptions and converts them into an EXCEPTINFO structure that is returned through the `Invoke` call. However, when VTBL interface is used, you are responsible for catching the exceptions yourself. As an example of protecting your dual-interface methods:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE （CAutoClickDoc、 DualAClick）  
    TRY_DUAL(IID_IDualAClick) {* / / MFC 會自動將轉換的 Unicode BSTR * / / Ansi CString，視...  
    pThis]-> [m_str = newText;  
    傳回 NOERROR。  
 }  
    CATCH_ALL_DUAL}  
```  
  
 `CATCH_ALL_DUAL` takes care of returning the correct error code when an exception occurs. `CATCH_ALL_DUAL` converts an MFC exception into OLE Automation error-handling information using the **ICreateErrorInfo** interface. (An example `CATCH_ALL_DUAL` macro is in the file MFCDUAL.H in the [ACDUAL](../visual-cpp-samples.md) sample. The function it calls to handle exceptions, `DualHandleException`, is in the file MFCDUAL.CPP.) `CATCH_ALL_DUAL` determines the error code to return based on the type of exception that occurred:  
  
- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) - In this case, `HRESULT` is constructed using the following code:  
  
 ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR,
    FACILITY_ITF,   
 (e]-> [m_wCode + 0x200));

 ```  
  
     This creates an `HRESULT` specific to the interface that caused the exception. The error code is offset by 0x200 to avoid any conflicts with system-defined `HRESULT`s for standard OLE interfaces.  
  
- [CMemoryException](../mfc/reference/cmemoryexception-class.md) - In this case, `E_OUTOFMEMORY` is returned.  
  
-   Any other exception - In this case, `E_UNEXPECTED` is returned.  
  
 To indicate that the OLE Automation error handler is used, you should also implement the **ISupportErrorInfo** interface.  
  
 First, add code to your automation class definition to show it supports **ISupportErrorInfo**.  
  
 Second, add code to your automation class's interface map to associate the **ISupportErrorInfo** implementation class with MFC's `QueryInterface` mechanism. The `INTERFACE_PART` statement matches the class defined for **ISupportErrorInfo**.  
  
 Finally, implement the class defined to support **ISupportErrorInfo**.  
  
 (The [ACDUAL](../visual-cpp-samples.md) sample contains three macros to help do these three steps, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, and `IMPLEMENT_DUAL_ERRORINFO`, all contained in MFCDUAL.H.)  
  
 The following example implements a class defined to support **ISupportErrorInfo**. `CAutoClickDoc` is the name of your automation class and `IID_IDualAClick` is the **IID** for the interface that is the source of errors reported through the OLE Automation error object:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()   
{  
    METHOD_PROLOGUE （CAutoClickDoc、 SupportErrorInfo）   
    傳回 pThis]-> [ExternalAddRef();

}   
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()   
{   
    METHOD_PROLOGUE （CAutoClickDoc、 SupportErrorInfo）   
    傳回 pThis]-> [ExternalRelease();

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface （REFIID iid，LPVOID * ppvObj）   
{   
    METHOD_PROLOGUE （CAutoClickDoc、 SupportErrorInfo）   
    傳回 pThis]-> [ExternalQueryInterface & iid (ppvObj）;

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo (REFIID iid)   
{   
    METHOD_PROLOGUE （CAutoClickDoc、 SupportErrorInfo）   
    傳回 (iid = = IID_IDualAClick) S_OK: S_FALSE。   
}  
```  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

