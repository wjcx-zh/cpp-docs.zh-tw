---
title: "TN065：OLE Automation 伺服程式的雙重介面支援 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ACDUAL 範例 [MFC]"
  - "Automation 伺服程式, 雙重介面支援"
  - "雙重介面, OLE Automation"
  - "TN065"
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN065：OLE Automation 伺服程式的雙重介面支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個附註討論如何將雙重介面支援加入至 MFC 架構的 OLE Automation 伺服應用程式。  [ACDUAL](../top/visual-cpp-samples.md) 範例說明雙重介面支援，因此，在這個附註的範例程式碼從 ACDUAL 被接受。  在這個注意事項所述的巨集，例如 `DECLARE_DUAL_ERRORINFO`， `DUAL_ERRORINFO_PART`和 `IMPLEMENT_DUAL_ERRORINFO`，這是 ACDUAL 範例的一部分，而且可以在 MFCDUAL.H. 找到。  
  
## 雙重介面  
 雖然 OLE Automation 可讓您實作 `IDispatch` 介面、VTBL 介面或包含兩個\) 的雙重介面 \(Microsoft，強烈建議您實作所有公開的 OLE Automation 物件的雙重介面。  雙重介面明顯優於 `IDispatch`唯一或 VTBL 介面:  
  
-   繫結可以出現在編譯時期透過 VTBL 介面，或是在執行階段透過 `IDispatch`。  
  
-   可以使用 VTBL 介面的 OLE Automation 控制器可能會因提高效能。  
  
-   使用 `IDispatch` 介面的現有 OLE Automation 控制器將繼續運作。  
  
-   VTBL 介面更容易從 C\+\+ 呼叫。  
  
-   雙重介面對於相容性需要與 Visual Basic 物件支援功能。  
  
## 將雙重介面支援加入至以 CCmdTarget 的類別  
 雙重介面只是從 `IDispatch`取得的自訂介面。  最直接的方式實作 `CCmdTarget`的雙重介面支援\-使用 MFC 和 ClassWizard，基底類別是第一次實作類別中正常分派介面，然後加入自訂介面。  在大部分的情況下，您的自訂介面實作會委派至 MFC `IDispatch` 實作。  
  
 首先，請修改伺服器的 ODL 檔案來定義物件的雙重介面。  若要定義雙重介面，您必須使用介面陳述式，而非 Visual C\+\+ 精靈產生的 `DISPINTERFACE` 陳述式。  而不是移除現有的 `DISPINTERFACE` 陳述式，加入新介面的陳述式。  將 `DISPINTERFACE` 格式，您可以繼續使用 ClassWizard 添加屬性和方法加入至物件，不過，您必須將的屬性和方法加入至介面陳述式。  
  
 雙重介面的介面陳述式必須有 **OLEAUTOMATION** 和 **DUAL** 屬性，，且必須衍生自 `IDispatch`介面。  您可以使用 [GUIDGEN](../top/visual-cpp-samples.md) 範例建立雙重介面的 **IID** :  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
   oleautomation,  
   dual  
]  
interface IDualAClick : IDispatch  
  {  
  };  
```  
  
 一旦您有適當的陳述式，請啟動加入方法和屬性的項目。  如需雙重介面，您需要重新整理參數清單，讓您的方法和屬性存取子函式在雙重介面傳回 `HRESULT` 並將其傳回值做為參數的 `[retval,out]`屬性。  確定針對屬性，您就必須將讀取 \(`propget`\) 和具有相同 ID 的 . 寫入 \(`propput`\) 存取的功能。  例如：  
  
```  
[propput, id(1)] HRESULT text([in] BSTR newText);  
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);  
```  
  
 在您的方法和屬性之後的 Coclass 陳述式中定義，您需要加入介面陳述式的參考。  例如：  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
   dispinterface IAClick;  
   [default] interface IDualAClick;  
};  
```  
  
 一旦更新了 ODL 檔案，請使用 MFC 的介面對應機制定義雙重介面的實作類別中的物件類別和在 MFC 的 `QueryInterface` 機制的對應項目。  您可以在每個項目的 `INTERFACE_PART` 區塊必須在輸入在 ODL 介面的陳述式，以及分派介面上的項目。  與 **propput** 屬性的每個 ODL 輸入需要功能的 `put_propertyname`。  與 **propget** 屬性的每個項目都需要功能的 `get_propertyname`。  
  
 若要定義自己的雙重介面的實作類別，請將 `DUAL_INTERFACE_PART` 區塊加入至物件的類別定義。  例如：  
  
```  
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
  
 若要連接雙重介面加入至 MFC [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) 的機制，請將 `INTERFACE_PART` 項目加入至介面對應:  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)  
  INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)  
  INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)  
END_INTERFACE_MAP()  
```  
  
 接著，您需要填入介面的實作。  在大部分的情況下，您可以委派至現有 MFC `IDispatch` 實作。  例如：  
  
```  
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
             REFIID iid, LPVOID* ppvObj)  
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
          UINT itinfo, LCID lcid, ITypeInfo FAR* FAR* pptinfo)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(  
       REFIID riid, OLECHAR FAR* FAR* rgszNames, UINT cNames,  
       LCID lcid, DISPID FAR* rgdispid)   
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames,   
                                    lcid, rgdispid);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(  
    DISPID dispidMember, REFIID riid, LCID lcid, WORD wFlags,  
    DISPPARAMS FAR* pdispparams, VARIANT FAR* pvarResult,  
    EXCEPINFO FAR* pexcepinfo, UINT FAR* puArgErr)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->Invoke(dispidMember, riid, lcid,  
                             wFlags, pdispparams, pvarResult,  
                             pexcepinfo, puArgErr);  
}  
```  
  
 針對物件的方法和屬性存取子函式，您需要填入實作。  您的方法和屬性函式通常可以委派回使用 ClassWizard 產生的方法。  不過，因此，如果您直接將屬性設定為存取變數，您必須撰寫程式碼取得\/將值置入變數。  例如：  
  
```  
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
  
## 傳遞雙重介面指標。  
 特別是如果您需要呼叫 `CCmdTarget::FromIDispatch`，將雙重介面指標不是直接的。  `FromIDispatch` 在 MFC 的 `IDispatch` 指標才有作用。  一種解決將原始 `IDispatch` 指標設定的查詢由 MFC 並將該傳遞指標需要它的函式。  例如：  
  
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
  
 在透過指標的雙重介面方法，您可能需要將它轉換成從 MFC `IDispatch` 指標至雙重介面指標。  例如：  
  
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
  
## 註冊應用程式類型程式庫  
 AppWizard 不產生程式碼向系統中的 OLE Automation 伺服應用程式的型別程式庫。  當有其他方式註冊型別程式庫時，向應用程式註冊型別程式庫是很方便的，也就是說，，會更新其 OLE 型別資訊時，每當應用程式執行的獨立的。  
  
 註冊應用程式型別程式庫，當應用程式是個別執行的位置:  
  
-   在您的標準的包含 AFXCTL.H 包含標頭檔， STDAFX.H，存取 `AfxOleRegisterTypeLib` 函式的定義。  
  
-   在應用程式的 `InitInstance` 函式，找出呼叫 `COleObjectFactory::UpdateRegistryAll`。  在這個呼叫之後，立即將呼叫加入至 `AfxOleRegisterTypeLib`，指定 **LIBID** 與您的型別程式庫，其對應到與您的型別程式庫名稱:  
  
    ```  
    // When a server application is launched stand-alone, it is a good idea  
    // to update the system registry in case it has been damaged.  
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);  
    COleObjectFactory::UpdateRegistryAll();  
    // DUAL_SUPPORT_START  
    // Make sure the type library is registered or dual interface won't work.  
    AfxOleRegisterTypeLib(AfxGetInstanceHandle(), LIBID_ACDual, _T("AutoClik.TLB"));  
    // DUAL_SUPPORT_END  
    ```  
  
## 修改安裝專案建置容納型別程式庫變更  
 修改專案的建置設定，以便包含 **UUID** 定義的標頭檔是由 MkTypLib 產生，每當型別程式庫重建:  
  
1.  在 \[**組建**\] 功能表上，按一下 \[**設定**\]\]，然後選取 ODL 檔案從檔案清單為每個組態。  
  
2.  按一下 **OLE Types** 選項並在 **Output header** 檔名欄位指定檔名。  使用您的專案尚未使用的檔名，但，因為 MkTypLib 會覆寫任何現有的檔案。  按一下關閉 **Build Settings** 對話方塊中的 \[**好**\] 。  
  
 從 MkTypLib 所產生的標頭檔加入 **UUID** 定義加入至專案:  
  
1.  包括 MkTypLib 所產生的標頭檔中包含標準標頭檔， STDAFX.H。  
  
2.  建立新檔案， INITIIDS.CPP，並將它加入至您的專案。  在這個檔案，請將 MkTypLib 所產生的標頭檔包含 OLE2.H 和 INITGUID.H:  
  
    ```  
    // initIIDs.c: defines IIDs for dual interfaces  
    // This must not be built with precompiled header.  
      #include <ole2.h>  
      #include <initguid.h>  
      #include "acdual.h"  
    ```  
  
3.  在 \[**組建**\] 功能表上，按一下 \[**設定**\]\]，然後選取 INITIIDS.CPP 從檔案清單為每個組態。  
  
4.  按一下 **C\+\+** 索引標籤上，按一下分類， **Precompiled Headers**和 **Not using precompiled headers** 選取選項按鈕。  按一下確定關閉 **Build Settings** 對話方塊。  
  
## 指定正確的物件類別名稱在型別程式庫  
 精靈會隨附於 Visual C\+\+ 的 OLE 可建立類別不正確地使用實作類別名稱指定 coclass 在伺服器的 ODL 檔案。  在這個上運作時，實作類別名稱可能不是您要用來的使用者物件的類別名稱。  若要指定正確的名稱，請開啟 ODL 檔案，找出每個 Coclass 陳述式，並以正確的外部名稱取代實作類別名稱。  
  
 請注意，當變更 Coclass 陳述式， **CLSID**的變數名稱在 MkTypLib 產生標頭檔的會隨之變更。  您必須將程式碼更新為使用新的變數名稱。  
  
## 處理例外狀況和 Automation 錯誤介面  
 您的自動化物件的方法和屬性存取子函式可能會擲回例外狀況。  如果是這樣，您應該處理到雙重介面實作並將例外狀況的相關資訊傳回至控制器 OLE Automation 錯誤處理介面， **IErrorInfo**。  這個介面提供詳細內容，錯誤資訊傳遞 `IDispatch` 和 VTBL 介面。  表示錯誤處理常式可用，您應該實作 **ISupportErrorInfo** 介面。  
  
 為了說明錯誤處理機制，假設，用於 ClassWizard 產生函式實作標準分派支援擲回例外狀況。  **IDispatch::Invoke** 的 MFC 的實作通常會攔截這些例外狀況並將它們轉換成透過 `Invoke` 呼叫所傳回的 EXCEPTINFO 結構。  不過，當使用時， VTBL 介面，您必須負責攔截例外狀況。  例如保護您的雙重介面方法:  
  
```  
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
  
 當例外狀況發生時，`CATCH_ALL_DUAL` 負責傳回正確的錯誤碼。  使用 **ICreateErrorInfo** 介面，`CATCH_ALL_DUAL` 轉換 MFC 例外狀況至 OLE Automation 錯誤處理資訊。\(範例 `CATCH_ALL_DUAL` 巨集在 [ACDUAL](../top/visual-cpp-samples.md) 範例中的檔案 MFCDUAL.H。  它呼叫處理例外狀況的函式，則為 `DualHandleException`，在檔案 MFCDUAL.CPP\)。 `CATCH_ALL_DUAL` 判斷錯誤代碼根據產生例外狀況類型的傳回:  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) –使用下列程式碼，在這種情況下， `HRESULT` 建構:  
  
    ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF,   
                               (e->m_wCode + 0x200));  
    ```  
  
     建立這個 `HRESULT` 特定造成例外狀況的介面。  錯誤碼由 0x200 位移避免與系統定義之 `HRESULT`的所有衝突標準 OLE 介面的。  
  
-   [CMemoryException](../mfc/reference/cmemoryexception-class.md) \(在此例中，則會傳回 `E_OUTOFMEMORY` 。  
  
-   其他例外狀況 \(在此例中，則會傳回 `E_UNEXPECTED` 。  
  
 表示使用 OLE Automation 錯誤處理常式，您也應該實作 **ISupportErrorInfo** 介面。  
  
 首先，對顯示其 Automation 類別定義中加入程式碼以支援 **ISupportErrorInfo**。  
  
 其次，對您的自動化類別的關聯 **ISupportErrorInfo** 實作類別的介面對應加入程式碼以 MFC 的 `QueryInterface` 機制。  `INTERFACE_PART` 陳述式符合 **ISupportErrorInfo**所定義的類別。  
  
 最後，請實作定義的類別支援 **ISupportErrorInfo**。  
  
 \( [ACDUAL](../top/visual-cpp-samples.md) 範例包含說明的三個巨集做這三個步驟、 `DECLARE_DUAL_ERRORINFO`、 `DUAL_ERRORINFO_PART`和 `IMPLEMENT_DUAL_ERRORINFO`，在 MFCDUAL.H. 的所有包含的\)  
  
 下列範例會實作所定義的類別支援 **ISupportErrorInfo**。  `CAutoClickDoc` 為您自動化類別名稱，而 `IID_IDualAClick` 是透過 OLE Automation 錯誤物件報告錯誤的來源介面的 **IID** :  
  
```  
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
   REFIID iid, LPVOID* ppvObj)   
{   
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return pThis->ExternalQueryInterface(&iid, ppvObj);   
}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(   
   REFIID iid)   
{   
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return (iid == IID_IDualAClick) ? S_OK : S_FALSE;   
}  
```  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)