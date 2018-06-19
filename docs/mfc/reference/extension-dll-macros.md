---
title: 巨集和函式管理 Dll |Microsoft 文件
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5e79556bf6e3ae92f7a8d4975dbd30f199e2ca8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376472"
---
# <a name="macros-and-functions-for-managing-dlls"></a>巨集和管理 Dll 函式

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|匯出類別。|
|[AFX_MANAGE_STATE](#afx_manage_state)|保護在 DLL 中匯出的函式。|
|[AfxOleInitModule](#afxoleinitmodule)|提供 OLE 支援從動態連結至 MFC 之標準 MFC DLL。|
|[AfxNetInitModule](#afxnetinitmodule)|提供 MFC 通訊端支援從動態連結至 MFC 之標準 MFC DLL。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|取得目前的每個模組狀態旗標的狀態。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|設定將模組狀態，初始化之前，及/或在清除之後還原先前的模組狀態。|
|[AfxInitExtensionModule]()#afxinitextensionmodule|初始化 DLL。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|設定每個模組狀態旗標，會影響 MFC 的 WinSxS 行為。|
|[AfxTermExtensionModule]()#afxtermextensionmodule)|可讓 MFC 清理 MFC 擴充 DLL 時從 DLL 卸離的每個處理序。|


## <a name="afx_ext_class"></a>  AFX_EXT_CLASS
[MFC 擴充 Dll](../../build/extension-dlls.md)使用巨集**AFX_EXT_CLASS**表示匯出的類別，則連結至 MFC 擴充 DLL 的可執行檔匯入類別使用巨集。  
   
### <a name="remarks"></a>備註  
 與**AFX_EXT_CLASS**巨集，用來建置 MFC 擴充 DLL 的檔案可以搭配連結至 DLL 的可執行檔相同的標頭。  
  
 在您的 DLL 的標頭檔，加入**AFX_EXT_CLASS**關鍵字加入類別的宣告，如下所示：  
  
```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
``` 
  
 如需詳細資訊，請參閱[匯出和匯入使用 AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md)。  
   
### <a name="requirements"></a>需求  
 標頭： **afxv_** dll.h  
   
## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE
呼叫此巨集，以保護匯出的 DLL 中函式。  
   
### <a name="syntax"></a>語法    
```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )  
```
### <a name="parameters"></a>參數  
 `pModuleState`  
 指標`AFX_MODULE_STATE`結構。  
   
### <a name="remarks"></a>備註  
 叫用此巨集時，`pModuleState`有效的模組狀態的其餘部分的立即包含範圍。 離開範圍時，將會自動還原先前的有效模組狀態。    
 `AFX_MODULE_STATE`結構包含全域模組，也就是推送入或快顯的模組狀態的部分資料。    
 根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果您有匯出函式在 DLL 中，例如啟動 DLL 中的對話方塊，這個範本實際上儲存在 DLL 模組。 您需要切換使用正確的控制代碼的模組狀態。 您可以將下列程式碼加入至函式開頭：    
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
 這會將目前的模組狀態與從傳回的狀態[AfxGetStaticModuleState](#afxgetstaticmodulestate)到目前的範圍結束為止。    
 模組狀態和 MFC 的詳細資訊，請參閱 「 管理資料的 MFC 模組狀態 」，在[建立新文件、 視窗和檢視](../creating-new-documents-windows-and-views.md)和[技術提示 58](../tn058-mfc-module-state-implementation.md)。    
> [!NOTE]
>  當 MFC 會為組件建立啟用內容時，它會使用[AfxWinInit](#afxwininit)以建立的內容和`AFX_MANAGE_STATE`啟用和停用它。 也請注意，`AFX_MANAGE_STATE`啟用靜態 MFC 程式庫以及 MFC Dll，為了讓 MFC 使用者 DLL 選取的適當啟用內容中執行的程式碼。 如需詳細資訊，請參閱[MFC 模組狀態的啟用內容支援](../support-for-activation-contexts-in-the-mfc-module-state.md)。     
### <a name="requirements"></a>需求  
 **標頭：** afxstat_.h  
   
### <a name="see-also"></a>另請參閱  
 [AfxGetStaticModuleState](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule
如需 OLE 支援從動態連結至 MFC 之標準 MFC DLL，呼叫此函式在一般的 MFC DLL 中`CWinApp::InitInstance`函式來初始化 MFC OLE DLL。  
   
### <a name="syntax"></a>語法    
```
void AFXAPI AfxOleInitModule( );  
```  
   
### <a name="remarks"></a>備註  
 MFC OLE DLL 是 MFC 擴充 DLL;為了讓 MFC 擴充 DLL 至**CDynLinkLibrary**鏈結，就必須建立**CDynLinkLibrary**將會使用每個模組的內容中的物件。 `AfxOleInitModule` 建立**CDynLinkLibrary**您標準 MFC DLL 的內容中的物件，讓它取得**CDynLinkLibrary**物件鏈結的標準 MFC DLL。  
  
 如果您要建立 OLE 控制項，並使用`COleControlModule`，您不應該呼叫**AfxOleInitModule**因為`InitInstance`成員函式`COleControlModule`呼叫`AfxOleInitModule`。  
   
### <a name="requirements"></a>需求  
 **標頭**: < afxdll_.h >  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>  AfxNetInitModule
MFC 通訊端支援從動態連結至 MFC 之標準 MFC DLL，會呼叫這個函式增益程式標準的 MFC DLL **Afxenablecontrolcontainer**函式來初始化 MFC 通訊端 DLL。  
   
### <a name="syntax"></a>語法    
```
void AFXAPI AfxNetInitModule( );  
```  
   
### <a name="remarks"></a>備註  
 MFC 通訊端 DLL 是一個 MFC 擴充 DLL;為了讓 MFC 擴充 DLL 至**CDynLinkLibrary**鏈結，就必須建立**CDynLinkLibrary**將會使用每個模組的內容中的物件。 `AfxNetInitModule` 建立**CDynLinkLibrary**您標準 MFC DLL 的內容中的物件，讓它取得**CDynLinkLibrary**物件鏈結的標準 MFC DLL。  
   
### <a name="requirements"></a>需求  
 **標頭：** < afxdll_.h >  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx
使用這個函數來取得每個模組狀態旗標，會影響 MFC 的 WinSxS 行為的目前狀態。  
   
### <a name="syntax"></a>語法    
```  
BOOL AFXAPI AfxGetAmbientActCtx();   
```  
   
### <a name="return-value"></a>傳回值  
 模組狀態旗標目前的值。  
   
### <a name="remarks"></a>備註  
 （這是預設值） 設定的旗標且在執行緒進入 MFC 模組時 (請參閱[AFX_MANAGE_STATE](#afx_manage_state))，就會啟動模組的內容。  
  
 如果未設定旗標，就不會啟用模組的內容。  
  
 模組的內容是從其資訊清單來決定的，通常是內嵌在模組資源中。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxcomctl32.h  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [管理 MFC 模組的狀態資料](../managing-the-state-data-of-mfc-modules.md)   
 [AfxSetAmbientActCtx](#setambientactctx)
 
## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState
呼叫此函式初始化之前將模組狀態設定及 （或） 在清除之後還原先前的模組狀態。  
   
### <a name="syntax"></a>語法    
```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );  
```  
   
### <a name="return-value"></a>傳回值  
 指標`AFX_MODULE_STATE`結構。  
   
### <a name="remarks"></a>備註  
 `AFX_MODULE_STATE`結構包含全域模組，也就是推送入或快顯的模組狀態的部分資料。  
  
 根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 如果您有匯出函式在 DLL 中，例如啟動 DLL 中的對話方塊，這個範本實際上儲存在 DLL 模組。 您需要切換使用正確的控制代碼的模組狀態。 您可以將下列程式碼加入至函式開頭：  
  
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
  
 這會將目前的模組狀態與從傳回的狀態`AfxGetStaticModuleState`到目前的範圍結束為止。  
  
 模組狀態和 MFC 的詳細資訊，請參閱 「 管理資料的 MFC 模組狀態 」，在[建立新文件、 視窗和檢視](../creating-new-documents-windows-and-views.md)和[技術提示 58](../tn058-mfc-module-state-implementation.md)。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxstat_.h  
   

## <a name="afxinitextensionmodule"></a> AfxInitExtensionModule
呼叫此函式中的 MFC 擴充 DLL 的`DllMain`初始化的 DLL。  
   
### <a name="syntax"></a>語法    
```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );  
```
### <a name="parameters"></a>參數  
 `state`  
 若要參考[AFX_EXTENSION_MODULE 結構](afx-extension-module-structure.md)結構將會在初始化之後包含 MFC 擴充 DLL 模組的狀態。 此狀態包含 MFC 擴充 DLL 初始化之前執行的一般靜態物件建構的一部分的執行階段類別物件的複本`DllMain`輸入。  
  
 `hModule`  
 MFC 擴充 DLL 模組控制代碼。  
   
### <a name="return-value"></a>傳回值  
 **TRUE** MFC 擴充 DLL 是否成功初始化，否則**FALSE**。  
   
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

```
  
 `AfxInitExtensionModule` 將 DLL 複製**HMODULE**並擷取 DLL 的執行階段類別 (`CRuntimeClass`結構) 以及其物件處理站 (`COleObjectFactory`物件) 使用更新版本時**CDynLinkLibrary**建立物件。    
 MFC 擴充 Dll 需要做兩件事中, 其`DllMain`函式：    
-   呼叫[AfxInitExtensionModule](#_mfc_afxinitextensionmodule)並檢查傳回的值。   
-   建立**CDynLinkLibrary**物件如果將匯出的 DLL [CRuntimeClass 結構](cruntimeclass-structure.md)物件，或有它自己的自訂資源。    
 您可以呼叫`AfxTermExtensionModule`清除 MFC 擴充 DLL，每個處理序中斷連結從 MFC 擴充 DLL 時 (也就是當處理序結束，或可能是卸載 DLL，`AfxFreeLibrary`呼叫)。     

### <a name="requirements"></a>需求  
 **標頭：** afxdll_.h     

### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [AfxTermExtensionModule](#afxtermextensionmodule)

 ## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx
使用這個函式來設定每個模組狀態旗標，這些旗標會影響 MFC 的 WinSxS 行為。  
   
### <a name="syntax"></a>語法  
  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet  
);  
```
### <a name="parameters"></a>參數  
 `bSet`  
 模組狀態旗標的新值。  
   
### <a name="remarks"></a>備註  
 （這是預設值） 設定的旗標且在執行緒進入 MFC 模組時 (請參閱[AFX_MANAGE_STATE](#afx_manage_state))，就會啟動模組的內容。    
 如果未設定旗標，就不會啟用模組的內容。    
 模組的內容是從其資訊清單來決定的，通常是內嵌在模組資源中。  
   
### <a name="example"></a>範例  
 ```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
```
   
### <a name="requirements"></a>需求  
 **標頭：** afxcomctl32.h  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [AfxGetAmbientActCtx](#afxgetambientactctx)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [管理 MFC 模組的狀態資料](../managing-the-state-data-of-mfc-modules.md) 

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

呼叫此函式可讓 MFC 清除 MFC 擴充 DLL 從 DLL 的每個處理序中斷連結時 (也就是當處理序結束，或可能是卸載 DLL，`AfxFreeLibrary`呼叫)。  
   
### <a name="syntax"></a>語法  
  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );  
```
### <a name="parameters"></a>參數  
 `state`  
 若要參考[AFX_EXTENSION_MODULE](afx-extension-module-structure.md)結構，其中包含 MFC 擴充 DLL 模組的狀態。  
  
 *球*  
 如果**TRUE**、 清除所有 MFC 擴充 DLL 模組。 否則，清除目前 DLL 模組。  
   
### <a name="remarks"></a>備註  
 `AfxTermExtensionModule` 將刪除附加至模組的任何本機儲存體，並移除訊息對應快取中的任何項目。 例如:   
  
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
  
 如果您的應用程式載入，而且會動態釋放 MFC 擴充 Dll，請務必呼叫`AfxTermExtensionModule`。 因為大部分的 MFC 擴充 Dll 不會以動態方式載入 （通常，這些連結透過其匯入程式庫），呼叫`AfxTermExtensionModule`通常並不需要。  
  
 MFC 擴充 Dll 需要呼叫[AfxInitExtensionModule](#afxinitextensionmodule)中其`DllMain`。 如果將匯出的 DLL [CRuntimeClass](cruntimeclass-structure.md)物件，或有它自己的自訂資源，您也必須建立**CDynLinkLibrary**物件存放至`DllMain`。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxdll_.h  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [AfxInitExtensionModule](#afxinitextensionmodule)
 




