---
title: 用於管理 Dll 的宏和函式
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: e4170ba95775fd3380837673a76a8adafc8ad011
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837174"
---
# <a name="macros-and-functions-for-managing-dlls"></a>用於管理 Dll 的宏和函式

|名稱|描述|
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|匯出類別。|
|[AFX_MANAGE_STATE](#afx_manage_state)|保護 DLL 中匯出的函式。|
|[AfxOleInitModule](#afxoleinitmodule)|從動態連結至 MFC 的標準 MFC DLL 提供 OLE 支援。|
|[AfxNetInitModule](#afxnetinitmodule)|從動態連結至 MFC 的標準 MFC DLL 提供 MFC 通訊端支援。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|取得每個模組狀態旗標的目前狀態。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|設定初始化之前的模組狀態，以及/或在清除後還原先前的模組狀態。|
|[AfxInitExtensionModule](#afxinitextensionmodule)|初始化 DLL。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|設定每個模組的狀態旗標，其會影響 MFC 的 WinSxS 行為。|
|[AfxTermExtensionModule](#afxtermextensionmodule)|當每個進程從 DLL 卸離時，允許 MFC 清除 MFC 擴充 DLL。|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a> AFX_EXT_CLASS

[MFC 擴充 dll](../../build/extension-dlls.md) 會使用宏 AFX_EXT_CLASS 來匯出類別;連結至 MFC 擴充 DLL 的可執行檔會使用宏來匯入類別。

### <a name="remarks"></a>備註

使用 AFX_EXT_CLASS 宏時，用來建立 MFC 擴充 DLL 的相同標頭檔 () s，可以與連結至 DLL 的可執行檔搭配使用。

在您的 DLL 的標頭檔中，將 AFX_EXT_CLASS 關鍵字加入至類別的宣告，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

如需詳細資訊，請參閱 [使用 AFX_EXT_CLASS 匯出和匯入](../../build/exporting-and-importing-using-afx-ext-class.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxv_dll。h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a> AFX_MANAGE_STATE

呼叫這個宏以保護 DLL 中匯出的函式。

### <a name="syntax"></a>語法

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>參數

*pModuleState*<br/>
結構的指標 `AFX_MODULE_STATE` 。

### <a name="remarks"></a>備註

叫用此宏時， *pModuleState* 是最適合立即包含範圍之其餘部分的有效模組狀態。 離開範圍之後，將會自動還原先前的有效模組狀態。
`AFX_MODULE_STATE`結構包含模組的全域資料，也就是已推送或彈出的模組狀態部分。

根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果您在 dll 中有匯出的函式（例如在 DLL 中啟動對話方塊的函式），此範本實際上會儲存在 DLL 模組中。 您必須切換模組狀態，才能使用正確的控制碼。 您可以藉由將下列程式碼新增至函式的開頭來執行此動作：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

這會將目前的模組狀態與從 [AfxGetStaticModuleState](#afxgetstaticmodulestate) 傳回的狀態交換，直到目前的範圍結束為止。

如需模組狀態和 MFC 的詳細資訊，請參閱 [建立新檔、視窗和查看](../creating-new-documents-windows-and-views.md) 和 [技術附注 58](../tn058-mfc-module-state-implementation.md)中的「管理 MFC 模組的狀態資料」。

> [!NOTE]
> 當 MFC 建立元件的啟用內容時，會使用 [AfxWinInit](application-information-and-management.md#afxwininit) 來建立內容，以及 `AFX_MANAGE_STATE` 啟用和停用它。 另外也請注意， `AFX_MANAGE_STATE` 針對靜態 MFC 程式庫和 MFC dll 啟用，以便讓 mfc 程式碼在使用者 DLL 所選取的適當啟用內容中執行。 如需詳細資訊，請參閱 [MFC 模組狀態中的啟用內容支援](../support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxstat_。h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

若要從動態連結至 MFC 的標準 MFC DLL 取得 OLE 支援，請在您的一般 MFC DLL 函式中呼叫此函式， `CWinApp::InitInstance` 以初始化 MFC OLE DLL。

### <a name="syntax"></a>語法

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>備註

MFC OLE DLL 是 MFC 擴充 DLL;為了讓 MFC 擴充 DLL 能夠進入 `CDynLinkLibrary` 鏈中，它必須 `CDynLinkLibrary` 在將使用它的每個模組的內容中建立物件。 `AfxOleInitModule``CDynLinkLibrary`在您的一般 MFC dll 內容中建立物件，使其成為 `CDynLinkLibrary` 一般 mfc dll 的物件鏈。

如果您要建立 OLE 控制項並使用 `COleControlModule` ，您不應該呼叫， `AfxOleInitModule` 因為呼叫的 `InitInstance` 成員函式 `COleControlModule` `AfxOleInitModule` 。

### <a name="requirements"></a>規格需求

**標頭**： \<afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a> AfxNetInitModule

針對可動態連結至 MFC 的標準 MFC DLL 支援 MFC 通訊端，請在您的一般 MFC DLL 函式中加入此函式的呼叫， `CWinApp::InitInstance` 以初始化 MFC 通訊端 dll。

### <a name="syntax"></a>語法

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>備註

MFC 通訊端 DLL 是 MFC 擴充 DLL;為了讓 MFC 擴充 DLL 能夠進入 `CDynLinkLibrary` 鏈中，它必須 `CDynLinkLibrary` 在將使用它的每個模組的內容中建立物件。 `AfxNetInitModule``CDynLinkLibrary`在您的一般 MFC dll 內容中建立物件，使其成為 `CDynLinkLibrary` 一般 mfc dll 的物件鏈。

### <a name="requirements"></a>規格需求

**標頭：**\<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a> AfxGetAmbientActCtx

您可以使用此函式來取得每個模組狀態旗標的目前狀態，這會影響 MFC 的 WinSxS 行為。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>傳回值

模組狀態旗標目前的值。

### <a name="remarks"></a>備註

設定旗標時 (預設) ，而執行緒進入 MFC 模組 (請參閱 [AFX_MANAGE_STATE](#afx_manage_state)) ，模組的內容會啟用。

如果未設定旗標，就不會啟用模組的內容。

模組的內容是從其資訊清單來決定的，通常是內嵌在模組資源中。

### <a name="requirements"></a>規格需求

**標頭：** >afxcomctl32.h>。h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState

呼叫此函式可在初始化之前設定模組狀態，以及/或在清除後還原先前的模組狀態。

### <a name="syntax"></a>語法

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>傳回值

結構的指標 `AFX_MODULE_STATE` 。

### <a name="remarks"></a>備註

`AFX_MODULE_STATE`結構包含模組的全域資料，也就是已推送或彈出的模組狀態部分。

根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果您在 dll 中有匯出的函式（例如在 DLL 中啟動對話方塊的函式），此範本實際上會儲存在 DLL 模組中。 您必須切換模組狀態，才能使用正確的控制碼。 您可以藉由將下列程式碼新增至函式的開頭來執行此動作：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

這會將目前的模組狀態與從傳回的狀態交換 `AfxGetStaticModuleState` 到目前的範圍結束為止。

如需模組狀態和 MFC 的詳細資訊，請參閱 [建立新檔、視窗和查看](../creating-new-documents-windows-and-views.md) 和 [技術附注 58](../tn058-mfc-module-state-implementation.md)中的「管理 MFC 模組的狀態資料」。

### <a name="requirements"></a>規格需求

**標頭：** afxstat_。h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

在 MFC 擴充 DLL 中呼叫此函式 `DllMain` ，以初始化 DLL。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>參數

*state*<br/>
[AFX_EXTENSION_MODULE 結構](afx-extension-module-structure.md)結構的參考，該結構會在初始化之後包含 MFC 擴充 DLL 模組的狀態。 狀態包含一份由 MFC 擴充 DLL 初始化的執行時間類別物件，做為輸入之前執行之一般靜態物件結構的一部分 `DllMain` 。

*hModule*<br/>
MFC 延伸模組 DLL 模組的控制碼。

### <a name="return-value"></a>傳回值

如果 MFC 擴充 DLL 已成功初始化，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

例如：

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

`AfxInitExtensionModule` 製作 DLL HMODULE 的複本，並) 取得 DLL 的執行時間類別 (結構，以及 `CRuntimeClass` 其物件 factory (`COleObjectFactory` 物件，) 稍後在 `CDynLinkLibrary` 建立物件時使用。
MFC 擴充 Dll 需要在其函式中執行兩項 `DllMain` 工作：

- 呼叫 [AfxInitExtensionModule](#afxinitextensionmodule) 並檢查傳回值。

- `CDynLinkLibrary`如果 DLL 將匯出[CRuntimeClass 結構](cruntimeclass-structure.md)物件或擁有自己的自訂資源，請建立物件。

您可以呼叫 `AfxTermExtensionModule` ，以在每個進程卸離 mfc 擴充 dll 時，清除 mfc 擴充 dll (這會在進程結束時或 DLL 因為呼叫) 的結果而卸載時執行 `AfxFreeLibrary` 。

### <a name="requirements"></a>規格需求

**標頭：** afxdll_。h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a> AfxSetAmbientActCtx

使用這個函式來設定每個模組狀態旗標，這些旗標會影響 MFC 的 WinSxS 行為。

### <a name="syntax"></a>語法

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>參數

*bSet*<br/>
模組狀態旗標的新值。

### <a name="remarks"></a>備註

設定旗標時 (預設) ，而執行緒進入 MFC 模組 (請參閱 [AFX_MANAGE_STATE](#afx_manage_state)) ，模組的內容會啟用。
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

### <a name="requirements"></a>規格需求

**標頭：** >afxcomctl32.h>。h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a> AfxTermExtensionModule

呼叫此函式，可在每個進程卸離 DLL 時，讓 MFC 清除 MFC 擴充 DLL (這會發生在進程結束時，或 DLL 因為呼叫) 的結果而卸載時 `AfxFreeLibrary` 。

### <a name="syntax"></a>語法

```cpp
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>參數

*state*<br/>
[AFX_EXTENSION_MODULE](afx-extension-module-structure.md)結構的參考，其中包含 MFC 擴充 DLL 模組的狀態。

*球*<br/>
若為 TRUE，請清除所有 MFC 擴充 DLL 模組。 否則，請只清除目前的 DLL 模組。

### <a name="remarks"></a>備註

`AfxTermExtensionModule` 將會刪除任何附加至模組的本機儲存體，並從訊息對應快取中移除任何專案。 例如：

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

如果您的應用程式會以動態方式載入和釋放 MFC 擴充 Dll，請務必呼叫 `AfxTermExtensionModule` 。 因為大部分的 MFC 擴充 Dll 都不會以動態方式載入 (通常會透過其匯入程式庫連結) ，因此 `AfxTermExtensionModule` 通常不需要呼叫。

MFC 延伸模組 Dll 需要在其中呼叫 [AfxInitExtensionModule](#afxinitextensionmodule) `DllMain` 。 如果 DLL 將匯出 [CRuntimeClass](cruntimeclass-structure.md) 物件，或有自己的自訂資源，您也必須 `CDynLinkLibrary` 在中建立物件 `DllMain` 。

### <a name="requirements"></a>規格需求

**標頭：** afxdll_。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[管理 MFC 模組的狀態資料](../managing-the-state-data-of-mfc-modules.md)<br/>
