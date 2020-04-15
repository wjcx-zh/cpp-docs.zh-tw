---
title: 管理 DLL 的巨集和函式
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 6945dcc02423516e8d1cee5d8c828c4ed5069bef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365696"
---
# <a name="macros-and-functions-for-managing-dlls"></a>管理 DLL 的巨集和函式

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)||匯出類。|
|[AFX_MANAGE_STATE](#afx_manage_state)|保護 DLL 中的匯出函數。|
|[AfxOleInitModule](#afxoleinitmodule)|從動態連結到 MFC 的常規 MFC DLL 提供 OLE 支援。|
|[AfxNetInitModule](#afxnetinitmodule)|提供與 MFC 動態連結的常規 MFC DLL 的 MFC 插槽支援。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|獲取每個模組狀態標誌的當前狀態。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|在初始化和/或清理後還原以前的模組狀態之前設置模組狀態。|
|[AfxInitExtensionModule](#afxinitextensionmodule)|初始化 DLL。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|設置每個模組的狀態標誌,這會影響 MFC 的 WinSxS 行為。|
|[AfxTermExtensionModule](#afxtermextensionmodule)|允許 MFC 在每個行程從 DLL 分離時清理 MFC 擴展 DLL。|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a>AFX_EXT_CLASS

[MFC 擴展 DLL](../../build/extension-dlls.md)使用宏AFX_EXT_CLASS匯出類;連結到 MFC 擴展 DLL 的可執行檔使用巨集導入類。

### <a name="remarks"></a>備註

使用AFX_EXT_CLASS宏時,用於建構 MFC 擴展名 DLL 的相同標頭檔可用於連結到 DLL 的可執行檔。

在 DLL 的標頭檔中,將AFX_EXT_CLASS關鍵字添加到類的聲明中,如下所示:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

有關詳細資訊,請參閱使用[AFX_EXT_CLASS 匯出與匯入](../../build/exporting-and-importing-using-afx-ext-class.md)。

### <a name="requirements"></a>需求

**標題:** afxv_dll.h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a>AFX_MANAGE_STATE

呼叫此巨集以保護 DLL 中的匯出函數。

### <a name="syntax"></a>語法

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>參數

*pModuleState*<br/>
指向結構的`AFX_MODULE_STATE`指標。

### <a name="remarks"></a>備註

呼叫此巨集時 *,pModuleState*是直接包含作用域其餘部分的有效模組狀態。 離開作用域后,將自動還原以前的有效模塊狀態。
結構`AFX_MODULE_STATE`包含模組的全域數據,即推送或彈出的模組狀態部分。

根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果在 DLL 中具有匯出的函數(例如在 DLL 中啟動對話方塊的函數),則此範本實際上存儲在 DLL 模組中。 您需要切換模組狀態才能使用正確的句柄。 可以通過以下代碼加入函數的開頭來執行此操作:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

這將將當前模組狀態與從[AfxGetStaticModuleState](#afxgetstaticmodulestate)返回的狀態交換,直到當前作用域結束。

有關模組狀態和 MFC 的詳細資訊,請參閱[創建新文檔、Windows 和視圖](../creating-new-documents-windows-and-views.md)[和技術說明 58](../tn058-mfc-module-state-implementation.md)中的"管理 MFC 模組的狀態數據"

> [!NOTE]
> 當 MFC 為程式集創建啟動上下文時,它使用[AfxWinInit](application-information-and-management.md#afxwininit)創建上下文`AFX_MANAGE_STATE`並啟動和停用它。 另請注意,`AFX_MANAGE_STATE`為靜態 MFC 庫以及 MFC DLL 啟用,以便允許 MFC 代碼在使用者 DLL 選擇的正確啟動上下文中執行。 有關詳細資訊,請參閱[MFC 模組狀態中對啟動上下文的支援](../support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="requirements"></a>需求

**標題:** afxstat_.h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>阿FXOleinit模組

對於動態連結到 MFC 的常規 MFC DLL 的 OLE 支援,`CWinApp::InitInstance`請在常規 MFC DLL 函數中調用此功能以初始化 MFC OLE DLL。

### <a name="syntax"></a>語法

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>備註

MFC OLE DLL 是 MFC 擴展 DLL;為了使 MFC 擴展 DLL 連接到`CDynLinkLibrary`鏈中,它必須在`CDynLinkLibrary`將使用它的每個模組 的上下文中創建一個物件。 `AfxOleInitModule`在`CDynLinkLibrary`常規 MFC DLL 的上下文中創建物件,以便將其連接到常規`CDynLinkLibrary`MFC DLL 的物件鏈中。

如果要構建 OLE 控件`COleControlModule`並且正在 使用 ,則`AfxOleInitModule`不應`InitInstance``COleControlModule`調用`AfxOleInitModule`,因為調用的成員函數。

### <a name="requirements"></a>需求

**標題**\<: afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a>AfxNetInit 模組

對於動態連結到 MFC 的常規 MFC DLL 的 MFC 插槽支援,在常規 MFC`CWinApp::InitInstance`DLL 函數中添加對此函數 的調用,以初始化 MFC 插槽 DLL。

### <a name="syntax"></a>語法

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>備註

MFC 插槽 DLL 是 MFC 擴展 DLL;為了使 MFC 擴展 DLL 連接到`CDynLinkLibrary`鏈中,它必須在`CDynLinkLibrary`將使用它的每個模組 的上下文中創建一個物件。 `AfxNetInitModule`在`CDynLinkLibrary`常規 MFC DLL 的上下文中創建物件,以便將其連接到常規`CDynLinkLibrary`MFC DLL 的物件鏈中。

### <a name="requirements"></a>需求

**標題:** \<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a>AfxGet環境ActCtx

使用此函數獲取每個模組狀態標誌的當前狀態,這會影響 MFC 的 WinSxS 行為。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>傳回值

模組狀態標誌當前值。

### <a name="remarks"></a>備註

當標誌被設置(這是預設值)和線程進入 MFC 模組(請參閱[AFX_MANAGE_STATE),](#afx_manage_state)模組的上下文被啟動。

如果未設定旗標，就不會啟用模組的內容。

模組的內容是從其資訊清單來決定的，通常是內嵌在模組資源中。

### <a name="requirements"></a>需求

**標題:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a>AfxGet靜態模組狀態

調用此函數以在初始化之前設置模組狀態和/或在清理後還原以前的模塊狀態。

### <a name="syntax"></a>語法

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>傳回值

指向結構的`AFX_MODULE_STATE`指標。

### <a name="remarks"></a>備註

結構`AFX_MODULE_STATE`包含模組的全域數據,即推送或彈出的模組狀態部分。

根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果在 DLL 中具有匯出的函數(例如在 DLL 中啟動對話方塊的函數),則此範本實際上存儲在 DLL 模組中。 您需要切換模組狀態才能使用正確的句柄。 可以通過以下代碼加入函數的開頭來執行此操作:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

這將交換當前模組狀態,從當前作用域結束`AfxGetStaticModuleState`為止返回的狀態。

有關模組狀態和 MFC 的詳細資訊,請參閱[創建新文檔、Windows 和視圖](../creating-new-documents-windows-and-views.md)[和技術說明 58](../tn058-mfc-module-state-implementation.md)中的"管理 MFC 模組的狀態數據"

### <a name="requirements"></a>需求

**標題:** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

在 MFC 延伸 DLL`DllMain`中呼叫此函數以初始化 DLL。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>參數

*state*<br/>
對[AFX_EXTENSION_MODULE結構結構](afx-extension-module-structure.md)的引用,該結構將在初始化後包含 MFC 擴展 DLL 模組的狀態。 狀態包括 MFC 擴展 DLL 已初始化的運行時類物件的副本`DllMain`,作為輸入之前 執行的正常靜態物件構造的一部分。

*hModule*<br/>
MFC 擴展 DLL 模組的句柄。

### <a name="return-value"></a>傳回值

如果 MFC 擴展 DLL 已成功初始化,則為 TRUE;否則,FALSE。

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

`AfxInitExtensionModule`複製 DLL 的 HMODULE 並擷取 DLL`CRuntimeClass`的執行時類別(`COleObjectFactory`結構)及其物件工廠(`CDynLinkLibrary`物件),供以後創建 物件時使用。
MFC 延伸 DLL`DllMain`需要在其 功能中執行兩項操作:

- 調用[AfxInit 擴展模組](#afxinitextensionmodule)並檢查返回值。

- 如果`CDynLinkLibrary`DLL 將匯出[CRuntimeClass 結構](cruntimeclass-structure.md)物件或具有其自己的自訂資源,則創建物件。

當每個進程`AfxTermExtensionModule`從 MFC 分機 DLL 分離時(當行程`AfxFreeLibrary`退出時,或者由於調用而卸載 DLL 時),可以調用以清理 MFC 分機 DLL。

### <a name="requirements"></a>需求

**標題:** afxdll_.h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a>AfxSet環境ActCtx

使用這個函式來設定每個模組狀態旗標，這些旗標會影響 MFC 的 WinSxS 行為。

### <a name="syntax"></a>語法

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>參數

*bSet*<br/>
模組狀態旗標的新值。

### <a name="remarks"></a>備註

當標誌被設置(這是預設值)和線程進入 MFC 模組(請參閱[AFX_MANAGE_STATE),](#afx_manage_state)模組的上下文被啟動。
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

**標題:** afxcomctl32.h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a>AfxTerm延伸模組

呼叫此函數,允許 MFC 在每個行程從 DLL 分離時(當`AfxFreeLibrary`行程退出或由於呼叫而卸載 DLL 時)清理 MFC 分機 DLL。

### <a name="syntax"></a>語法

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>參數

*state*<br/>
對包含 MFC 擴展 DLL 模組狀態[AFX_EXTENSION_MODULE結構的](afx-extension-module-structure.md)引用。

*球*<br/>
如果為 TRUE,請清理所有 MFC 擴展 DLL 模組。 否則,請僅清理當前 DLL 模組。

### <a name="remarks"></a>備註

`AfxTermExtensionModule`將刪除附加到模組的任何本地存儲,並從消息映射快取中刪除任何條目。 例如：

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

如果應用程式動態載入並釋放 MFC 延伸 DLL,請務`AfxTermExtensionModule`必呼叫 。 由於大多數 MFC 擴展 DLL 不是動態載入的(通常,它們透過其匯入庫連結`AfxTermExtensionModule`),因此通常不需要呼叫 。

MFC 延伸 DLL`DllMain`需要在其 中呼叫[AfxInit 延伸模組](#afxinitextensionmodule)。 如果 DLL 將匯出[CRuntimeClass](cruntimeclass-structure.md)物件或有自己的自訂資源,`CDynLinkLibrary``DllMain`則還需要在 中 創建一個物件。

### <a name="requirements"></a>需求

**標題:** afxdll_.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[管理 MFC 模組的狀態資料](../managing-the-state-data-of-mfc-modules.md)<br/>
