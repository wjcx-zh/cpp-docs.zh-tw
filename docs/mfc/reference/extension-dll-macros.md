---
title: 巨集和管理 Dll 函式
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: b27f8763b60dc7ce3ee074cad1365e7e1de3a7e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322198"
---
# <a name="macros-and-functions-for-managing-dlls"></a>巨集和管理 Dll 函式

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|匯出類別。|
|[AFX_MANAGE_STATE](#afx_manage_state)|保護在 dll 裡匯出函式。|
|[AfxOleInitModule](#afxoleinitmodule)|提供 OLE 支援從動態連結至 MFC 之標準 MFC DLL。|
|[AfxNetInitModule](#afxnetinitmodule)|提供從動態連結至 MFC 之標準 MFC DLL 的 MFC 通訊端支援。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|取得每個模組狀態旗標的目前狀態。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|設定初始化之前，及/或清除還原之後的前一個模組狀態的模組狀態。|
|[AfxInitExtensionModule](#afxinitextensionmodule)|初始化 DLL。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|設定每個模組狀態旗標，會影響 MFC 的 WinSxS 行為。|
|[AfxTermExtensionModule](#afxtermextensionmodule)|可讓每個處理序中斷連結的 DLL 時清除 MFC 擴充 DLL 的 MFC。|

## <a name="afx_ext_class"></a>  AFX_EXT_CLASS

[MFC 擴充 Dll](../../build/extension-dlls.md)匯出類別中使用 AFX_EXT_CLASS 巨集; 連結至 MFC 擴充 DLL 的可執行檔匯入類別使用巨集。

### <a name="remarks"></a>備註

使用 AFX_EXT_CLASS 巨集，用來建置 MFC 擴充 DLL 的相同標頭檔可以搭配連結至 DLL 的可執行檔。

在您的 DLL 的標頭檔，將 AFX_EXT_CLASS 關鍵字加入至類別的宣告，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

如需詳細資訊，請參閱 <<c0> [ 匯出和匯入使用 AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md)。

### <a name="requirements"></a>需求

**標頭：** afxv_dll.h

## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE

呼叫此巨集來保護匯出的 DLL 中函式。

### <a name="syntax"></a>語法

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>參數

*pModuleState*<br/>
指標`AFX_MODULE_STATE`結構。

### <a name="remarks"></a>備註

叫用此巨集時， *pModuleState*有效的模組狀態的其餘部分的立即包含範圍。 離開範圍時，將會自動還原先前的有效模組狀態。
`AFX_MODULE_STATE`結構包含全域模組，也就是推送入或快顯的模組狀態的部分資料。

根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果您有匯出函式在 DLL 中，例如會啟動一個對話方塊，在 DLL 時，此範本是實際上會儲存在 DLL 模組。 您需要切換模組狀態，要使用正確的控制代碼。 您可以將下列程式碼新增至函式開頭：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

這會從傳回的狀態與目前的模組狀態[AfxGetStaticModuleState](#afxgetstaticmodulestate)直到目前的範圍結束為止。

如需有關電子郵件地址 和 MFC 模組狀態的詳細資訊，請參閱 「 管理資料的 MFC 模組狀態 」 中[建立新的文件中，Windows，並檢視](../creating-new-documents-windows-and-views.md)並[技術提示 58](../tn058-mfc-module-state-implementation.md)。

> [!NOTE]
>  當 MFC 啟用內容建立組件時，它會使用[AfxWinInit](application-information-and-management.md#afxwininit)來建立內容和`AFX_MANAGE_STATE`啟用和停用它。 也請注意，`AFX_MANAGE_STATE`可供靜態 MFC 程式庫，以及 MFC Dll，才能讓 MFC 使用者 dll 選取適當啟用內容中執行的程式碼。 如需詳細資訊，請參閱 < [MFC 模組狀態的啟用內容支援](../support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="requirements"></a>需求

**標頭：** afxstat_.h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

如需 OLE 支援從動態連結至 MFC 之標準 MFC DLL，呼叫此函式在您的標準 MFC DLL 的`CWinApp::InitInstance`函式來初始化 MFC OLE DLL。

### <a name="syntax"></a>語法

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>備註

MFC OLE DLL 是一個 MFC 擴充 DLL;為了讓 MFC 擴充 DLL 連結至`CDynLinkLibrary`鏈結，它必須建立`CDynLinkLibrary`每個模組，將會使用它的內容中的物件。 `AfxOleInitModule` 會建立`CDynLinkLibrary`物件在您的標準 MFC DLL 的內容中，讓它取得連結至`CDynLinkLibrary`物件的標準 MFC DLL 的鏈結。

如果您要建置 OLE 控制項，並使用`COleControlModule`，您不應該呼叫`AfxOleInitModule`因為`InitInstance`成員函式`COleControlModule`呼叫`AfxOleInitModule`。

### <a name="requirements"></a>需求

**標頭**: \<afxdll_.h >

## <a name="afxnetinitmodule"></a>  AfxNetInitModule

MFC 通訊端支援從動態連結至 MFC 之標準 MFC DLL，將呼叫此函式新增在您的標準 MFC DLL 的`CWinApp::InitInstance`函式來初始化 MFC 通訊端 DLL。

### <a name="syntax"></a>語法

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>備註

MFC 通訊端 DLL 是一個 MFC 擴充 DLL;為了讓 MFC 擴充 DLL 連結至`CDynLinkLibrary`鏈結，它必須建立`CDynLinkLibrary`每個模組，將會使用它的內容中的物件。 `AfxNetInitModule` 會建立`CDynLinkLibrary`物件在您的標準 MFC DLL 的內容中，讓它取得連結至`CDynLinkLibrary`物件的標準 MFC DLL 的鏈結。

### <a name="requirements"></a>需求

**標頭：** \<afxdll_.h >

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx

您可以使用此函式來取得的每個模組狀態旗標，會影響 MFC 的 WinSxS 行為的目前狀態。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>傳回值

模組狀態旗標目前的值。

### <a name="remarks"></a>備註

當設定旗標 （這是預設值），且執行緒進入 MFC 模組 (請參閱[AFX_MANAGE_STATE](#afx_manage_state))，在啟用模組的內容。

如果未設定旗標，就不會啟用模組的內容。

模組的內容是從其資訊清單來決定的，通常是內嵌在模組資源中。

### <a name="requirements"></a>需求

**標頭：** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState

呼叫此函式來設定初始設定之前將模組狀態，和/或清除還原之後的前一個模組狀態。

### <a name="syntax"></a>語法

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>傳回值

指標`AFX_MODULE_STATE`結構。

### <a name="remarks"></a>備註

`AFX_MODULE_STATE`結構包含全域模組，也就是推送入或快顯的模組狀態的部分資料。

根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果您有匯出函式在 DLL 中，例如會啟動一個對話方塊，在 DLL 時，此範本是實際上會儲存在 DLL 模組。 您需要切換模組狀態，要使用正確的控制代碼。 您可以將下列程式碼新增至函式開頭：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

這會從傳回的狀態與目前的模組狀態`AfxGetStaticModuleState`直到目前的範圍結束為止。

如需有關電子郵件地址 和 MFC 模組狀態的詳細資訊，請參閱 「 管理資料的 MFC 模組狀態 」 中[建立新的文件中，Windows，並檢視](../creating-new-documents-windows-and-views.md)並[技術提示 58](../tn058-mfc-module-state-implementation.md)。

### <a name="requirements"></a>需求

**標頭：** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

呼叫此函式中的 MFC 擴充 DLL 的`DllMain`初始化的 DLL。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>參數

*state*<br/>
參考[AFX_EXTENSION_MODULE 結構](afx-extension-module-structure.md)結構，它會在初始化之後包含 MFC 擴充 DLL 模組的狀態。 此狀態包含一份已由 MFC 擴充 DLL 初始化之前執行的一般靜態物件建構的一部分的執行階段類別物件`DllMain`輸入。

*hModule*<br/>
MFC 擴充 DLL 模組控制代碼。

### <a name="return-value"></a>傳回值

如果已成功初始化 MFC 擴充 DLL;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

例如: 

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;
...
```

`AfxInitExtensionModule` 會建立一份 DLL 的 HMODULE，並擷取 DLL 的執行階段類別 (`CRuntimeClass`結構) 以及其物件處理站 (`COleObjectFactory`物件) 使用更新版本時`CDynLinkLibrary`建立物件。
MFC 擴充 Dll 需要做兩件事，在其`DllMain`函式：

- 呼叫[AfxInitExtensionModule](#afxinitextensionmodule)並檢查傳回的值。

- 建立`CDynLinkLibrary`物件如果將匯出的 DLL [CRuntimeClass 結構](cruntimeclass-structure.md)物件，或有它自己的自訂資源。

您可以呼叫`AfxTermExtensionModule`每個處理序中斷連結 MFC 擴充 DLL 時清除 MFC 擴充 DLL (恰好當處理序結束，或卸載 DLL 的`AfxFreeLibrary`呼叫)。

### <a name="requirements"></a>需求

**標頭：** afxdll_.h

## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx

使用這個函式來設定每個模組狀態旗標，這些旗標會影響 MFC 的 WinSxS 行為。

### <a name="syntax"></a>語法

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>參數

*bSet*<br/>
模組狀態旗標的新值。

### <a name="remarks"></a>備註

當設定旗標 （這是預設值），且執行緒進入 MFC 模組 (請參閱[AFX_MANAGE_STATE](#afx_manage_state))，在啟用模組的內容。
如果未設定旗標，就不會啟用模組的內容。
模組的內容是從其資訊清單來決定的，通常是內嵌在模組資源中。

### <a name="example"></a>範例

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>需求

**標頭：** afxcomctl32.h

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

呼叫此函式，可允許每個處理序中斷連結的 DLL 時清除 MFC 擴充 DLL 的 MFC (恰好當處理序結束，或卸載 DLL 的`AfxFreeLibrary`呼叫)。

### <a name="syntax"></a>語法

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>參數

*state*<br/>
參考[AFX_EXTENSION_MODULE](afx-extension-module-structure.md)結構，包含 MFC 擴充 DLL 模組的狀態。

*bAll*<br/>
如果為 TRUE，清除所有的 MFC 擴充 DLL 模組。 否則，清除目前 DLL 模組。

### <a name="remarks"></a>備註

`AfxTermExtensionModule` 會刪除任何附加至模組的本機儲存體，並從訊息對應快取中移除任何項目。 例如：

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}
```

如果您的應用程式載入，並動態釋放 MFC 擴充 Dll，務必呼叫`AfxTermExtensionModule`。 因為大部分的 MFC 擴充 Dll 不會以動態方式載入 （通常，他們所連結透過其匯入程式庫），呼叫`AfxTermExtensionModule`通常並不需要。

MFC 擴充 Dll 需要呼叫[AfxInitExtensionModule](#afxinitextensionmodule)在其`DllMain`。 如果將匯出的 DLL [CRuntimeClass](cruntimeclass-structure.md)物件，或有它自己的自訂資源，您也需要建立`CDynLinkLibrary`物件中`DllMain`。

### <a name="requirements"></a>需求

**標頭：** afxdll_.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[管理 MFC 模組的狀態資料](../managing-the-state-data-of-mfc-modules.md)<br/>
