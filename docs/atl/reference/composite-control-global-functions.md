---
title: 複合控制項全域函式 |Microsoft 文件
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
ms.openlocfilehash: 7c62d5056f28460644084296598ae865c6ff5f48
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="composite-control-global-functions"></a>複合控制項全域函式
這些函式會提供建立對話方塊，以及建立、 裝載和授權 ActiveX 控制項的支援。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。  
  
|||  
|-|-|  
|[AtlAxDialogBox](#atlaxdialogbox)|從使用者提供的對話方塊範本中建立強制回應對話方塊。 [結果] 對話方塊中可包含 ActiveX 控制項。|  
|[AtlAxCreateDialog](#atlaxcreatedialog)|從使用者提供的對話方塊範本中建立非強制回應對話方塊。 [結果] 對話方塊中可包含 ActiveX 控制項。|  
|[AtlAxCreateControl](#atlaxcreatecontrol)|建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|  
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|建立 ActiveX 控制項、 將它初始化，它裝載於指定的視窗，和從控制項擷取介面指標 （或指標）。|  
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|  
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制項、 將它初始化、 裝載於指定的視窗，並從控制項擷取介面指標 （或指標）。|  
|[AtlAxAttachControl](#atlaxattachcontrol)|將先前建立的控制項加入至指定的視窗。|  
|[AtlAxGetHost](#atlaxgethost)|用來取得指定視窗 （如果有的話），容器的直接介面指標控制代碼。|  
|[AtlAxGetControl](#atlaxgetcontrol)|用來取得所指定視窗 （如果有的話），內包含之控制項的直接介面指標控制代碼。|  
|[AtlSetChildSite](#atlsetchildsite)|初始化**IUnknown**子站台。|  
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 物件的裝載程式碼。|  
|[AtlAxWinTerm](#atlaxwinterm)|未初始化 AxWin 物件的裝載程式碼。|  
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
 `hInstance`  
 [in]識別執行個體，其可執行檔包含對話方塊範本的模組。  
  
 `lpTemplateName`  
 [in]識別對話方塊範本。 這個參數是指定名稱的對話方塊範本的 null 結尾字元字串的指標，或是指定的對話方塊範本資源識別碼的整數值。 如果參數指定的資源識別項，其高序位文字必須是零，其低序位字組必須包含識別項。 您可以使用[MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029)巨集來建立此值。  
  
 `hWndParent`  
 [in]識別擁有對話方塊視窗。  
  
 `lpDialogProc`  
 [in]指向對話方塊程序。 如需對話方塊程序的詳細資訊，請參閱[DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469)。  
  
 `dwInitParam`  
 [in]指定要傳遞至對話方塊中的值**lParam**參數**WM_INITDIALOG**訊息。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 若要使用**AtlAxDialogBox**與包含 ActiveX 控制項的對話方塊範本，請指定有效的**CLSID**， **APPID**或做為 URL 字串*文字*欄位**控制項**對話方塊資源，以及"AtlAxWin80"做為區段*類別名稱*欄位相同的區段底下。 以下示範哪些是有效**控制項**區段可能如下：  
  
```  
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,  
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100  
```  
  
 如需有關編輯資源指令碼的詳細資訊，請參閱[How to： 以文字格式開啟資源指令碼檔](../../windows/how-to-open-a-resource-script-file-in-text-format.md)。 如需有關控制資源定義陳述式的詳細資訊，請參閱[一般控制項參數](http://msdn.microsoft.com/library/windows/desktop/aa380902)下 Windows SDK *: SDK 工具*。  
  
 如需有關一般中對話方塊的詳細資訊，請參閱[對話方塊中](http://msdn.microsoft.com/library/windows/desktop/ms645452)和[CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) Windows SDK 中。  
  
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
 `hInstance`  
 [in]識別執行個體，其可執行檔包含對話方塊範本的模組。  
  
 `lpTemplateName`  
 [in]識別對話方塊範本。 這個參數是指定名稱的對話方塊範本的 null 結尾字元字串的指標，或是指定的對話方塊範本資源識別碼的整數值。 如果參數指定的資源識別項，其高序位文字必須是零，其低序位字組必須包含識別項。 您可以使用[MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029)巨集來建立此值。  
  
 `hWndParent`  
 [in]識別擁有對話方塊視窗。  
  
 `lpDialogProc`  
 [in]指向對話方塊程序。 如需對話方塊程序的詳細資訊，請參閱[DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469)。  
  
 `dwInitParam`  
 [in]指定要傳遞至對話方塊中的值**lParam**參數**WM_INITDIALOG**訊息。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 [結果] 對話方塊中可包含 ActiveX 控制項。  
  
 請參閱[CreateDialog](http://msdn.microsoft.com/library/windows/desktop/ms645434)和[CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) Windows SDK 中。  
  
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
 `lpszName`  
 要傳遞給控制項的字串指標。 格式必須如下的其中一個：  
  
-   ProgID，例如"MSCAL。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   URL，例如"http://www.microsoft.com"  
  
-   例如主動式文件的參考 「 file://\\\Documents\MyDoc.doc"  
  
-   這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」  
  
    > [!NOTE]
    >  「 MSHTML:"必須在前面的 HTML 片段，如此會將它指定為 MSHTML 資料流。  
  
 `hWnd`  
 [in]控制項將會附加至視窗的控制代碼。  
  
 `pStream`  
 [in]用來初始化控制項的屬性資料流的指標。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]指標將會接收位址**IUnknown**的容器。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 此全域函式可讓您與呼叫相同的結果[AtlAxCreateControlEx](#atlaxcreatecontrolex)( `lpszName` **，** `hWnd` **，** `pStream` **、 NULL、 為 NULL，NULL，NULL** );。  
  
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
 `lpszName`  
 要傳遞給控制項的字串指標。 格式必須如下的其中一個：  
  
-   ProgID，例如"MSCAL。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   URL，例如"http://www.microsoft.com"  
  
-   例如主動式文件的參考 「 file://\\\Documents\MyDoc.doc"  
  
-   這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」  
  
    > [!NOTE]
    >  「 MSHTML:"必須在前面的 HTML 片段，如此會將它指定為 MSHTML 資料流。  
  
 `hWnd`  
 [in]控制項將會附加至視窗的控制代碼。  
  
 `pStream`  
 [in]用來初始化控制項的屬性資料流的指標。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]指標將會接收位址**IUnknown**的容器。 可以是**NULL**。  
  
 `ppUnkControl`  
 [out]指標將會接收位址**IUnknown**的建立的控制項。 可以是**NULL**。  
  
 `iidSink`  
 所包含的物件上的輸出介面的介面識別碼。  
  
 *punkSink*  
 指標**IUnknown**介面連線到指定的連接點的接收器物件`iidSink`上所包含的物件已成功建立後，所包含的物件。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 `AtlAxCreateControlEx` 類似於[AtlAxCreateControl](#atlaxcreatecontrol)還能讓您接收新建立的控制項的介面指標，並將事件接收器設定為接收控制項引發的事件。  
  
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
 `lpszName`  
 要傳遞給控制項的字串指標。 格式必須如下的其中一個：  
  
-   ProgID，例如"MSCAL。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   URL，例如"http://www.microsoft.com"  
  
-   例如主動式文件的參考 「 file://\\\Documents\MyDoc.doc"  
  
-   這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」  
  
    > [!NOTE]
    >  「 MSHTML:"必須在前面的 HTML 片段，如此會將它指定為 MSHTML 資料流。  
  
 `hWnd`  
 控制項將會附加至視窗的控制代碼。  
  
 `pStream`  
 用來初始化控制項的屬性資料流的指標。 可以是**NULL**。  
  
 `ppUnkContainer`  
 指標將會接收位址**IUnknown**的容器。 可以是**NULL**。  
  
 `bstrLic`  
 BSTR，包含控制項的授權。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用方式的範例`AtlAxCreateControlLic`。  
  
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
 `lpszName`  
 要傳遞給控制項的字串指標。 格式必須如下的其中一個：  
  
-   ProgID，例如"MSCAL。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   URL，例如"http://www.microsoft.com"  
  
-   例如主動式文件的參考 「 file://\\\Documents\MyDoc.doc"  
  
-   這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」  
  
    > [!NOTE]
    >  「 MSHTML:"必須在前面的 HTML 片段，如此會將它指定為 MSHTML 資料流。  
  
 `hWnd`  
 控制項將會附加至視窗的控制代碼。  
  
 `pStream`  
 用來初始化控制項的屬性資料流的指標。 可以是**NULL**。  
  
 `ppUnkContainer`  
 指標將會接收位址**IUnknown**的容器。 可以是**NULL**。  
  
 `ppUnkControl`  
 [out]指標將會接收位址**IUnknown**的建立的控制項。 可以是**NULL**。  
  
 `iidSink`  
 所包含的物件上的輸出介面的介面識別碼。  
  
 *punkSink*  
 指標**IUnknown**介面連線到指定的連接點的接收器物件`iidSink`上所包含的物件已成功建立後，所包含的物件。  
  
 `bstrLic`  
 BSTR，包含控制項的授權。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 `AtlAxCreateControlLicEx` 類似於[AtlAxCreateControlLic](#atlaxcreatecontrollic)還能讓您接收新建立的控制項的介面指標，並將事件接收器設定為接收控制項引發的事件。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用方式的範例`AtlAxCreateControlLicEx`。  
  
##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl  
 將先前建立的控制項加入至指定的視窗。  
  
```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 [in]指標**IUnknown**的控制項。  
  
 `hWnd`  
 [in]將主控制項視窗的控制代碼。  
  
 `ppUnkContainer`  
 [out]指標的指標**IUnknown**容器物件。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)和[AtlAxCreateControl](#atlaxcreatecontrol)同時建立並附加控制項。  
  
> [!NOTE]
>  要附加的控制項物件必須先呼叫正確地初始化`AtlAxAttachControl`。  
  
##  <a name="atlaxgethost"></a>  AtlAxGetHost  
 在考慮控制代碼的情況下，取得所指定視窗 (如果有) 之容器的直接介面指標。  
  
```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>參數  
 `h`  
 [in]裝載控制項的視窗控制代碼。  
  
 `pp`  
 [out]**IUnknown**容器的控制項。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl  
 在考慮控制代碼的情況下，取得所指定視窗內包含之控制項的直接介面指標。  
  
```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>參數  
 `h`  
 [in]裝載控制項的視窗控制代碼。  
  
 `pp`  
 [out]**IUnknown**裝載的控制項。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="atlsetchildsite"></a>  AtlSetChildSite  
 呼叫此函式可設定子物件的站台**IUnknown**父物件。  
  
```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```  
  
### <a name="parameters"></a>參數  
 *punkChild*  
 [in]指標**IUnknown**介面之子系。  
  
 `punkParent`  
 [in]指標**IUnknown**介面的父系。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="atlaxwininit"></a>  AtlAxWinInit  
 此函式會初始化 ATL 的控制項裝載程式碼，藉由註冊 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 視窗類別以及幾個自訂視窗訊息。  
  
```
ATLAPI_(BOOL) AtlAxWinInit();
```  
  
### <a name="return-value"></a>傳回值  
 如果控制項裝載程式碼的初始化成功，則為非零否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 使用 ATL 控制項裝載 API 之前，必須呼叫此函式。 此函式，呼叫 **"AtlAxWin"** 視窗類別可用於呼叫[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)或[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)、 Windows SDK 中所述。  

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm  
 此函式未初始化 ATL 的控制項裝載程式碼取消註冊 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 視窗類別。  
  
```
inline BOOL AtlAxWinTerm();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回**TRUE**。  
  
### <a name="remarks"></a>備註  
 此函式只會呼叫[UnregisterClass](http://msdn.microsoft.com/library/windows/desktop/ms644899) Windows SDK 中所述。  
  
 呼叫此函式，如果您呼叫所有現有的主控件 windows 已終結後進行清理[AtlAxWinInit](#atlaxwininit)和您不需要再建立主應用程式視窗。 如果您未呼叫此函式，視窗類別會自動取消註冊處理序終止時。  
  
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
 `punkObj`  
 [in]要傳回資訊的物件的指標。  
  
 `plibid`  
 [out]包含來源介面定義的類型程式庫的 LIBID 指標。  
  
 `piid`  
 [out]物件的預設來源介面的介面 ID 的指標。  
  
 *pdwMajor*  
 [out]包含來源介面定義的類型程式庫的主要版本號碼的指標。  
  
 *pdwMinor*  
 [out]次要版本號碼，類型程式庫包含定義來源介面的指標。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 `AtlGetObjectSourceInterface` 可以提供您的預設來源介面，以及 LIBID 和主要的介面 ID 以及描述該介面的類型程式庫的次要版本號碼。  
  
> [!NOTE]
>  若要成功擷取要求的資訊。 這個函式，表示的物件`punkObj`必須實作`IDispatch`(和傳回型別資訊透過**IDispatch::GetTypeInfo**) 加上它也必須實作`IProvideClassInfo2`或`IPersist`。 來源介面的型別資訊必須位於相同的型別程式庫的型別資訊當做`IDispatch`。  
  
### <a name="example"></a>範例  
 下列範例示範如何定義事件接收器類別中， `CEasySink`，您可以傳遞給範本引數數目，以減少`IDispEventImpl`至基本的必要。 `EasyAdvise` 和`EasyUnadvise`使用`AtlGetObjectSourceInterface`初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成員之前呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)或[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)。  
  
 [!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)   
 [複合控制項巨集](../../atl/reference/composite-control-macros.md)
