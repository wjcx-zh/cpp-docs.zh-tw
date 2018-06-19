---
title: CDialogImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4119daf89820de0a835bfbc572cdfbf38c99e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365135"
---
# <a name="cdialogimpl-class"></a>CDialogImpl 類別
這個類別會提供方法來建立強制回應或非強制回應對話方塊。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
 
template <class T,  
    class TBase = CWindow>  
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>  
 
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`CDialogImpl`。  
  
 *TBase*  
 您的新類別的基底類別。 預設基底類別是[CWindow](../../atl/reference/cwindow-class.md)。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[建立](#create)|建立非強制回應對話方塊。|  
|[DestroyWindow](#destroywindow)|終結強制回應對話方塊。|  
|[DoModal](#domodal)|建立強制回應對話方塊。|  
|[EndDialog](#enddialog)|終結強制回應對話方塊。|  
  
### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT 方法  
  
|||  
|-|-|  
|[GetDialogProc](#getdialogproc)|傳回目前對話方塊程序。|  
|[MapDialogRect](#mapdialogrect)|將指定的矩形的對話方塊單位對應至螢幕單位 （像素為單位）。|  
|[OnFinalMessage](#onfinalmessage)|通常接收的最後一個訊息之後, 呼叫`WM_NCDESTROY`。|  
  
### <a name="static-functions"></a>靜態函式  
  
|||  
|-|-|  
|[DialogProc](#dialogproc)|處理傳送至對話方塊中的訊息。|  
|[StartDialogProc](#startdialogproc)|當第一個訊息接收到處理訊息傳送至對話方塊時呼叫。|  
  
## <a name="remarks"></a>備註  
 與`CDialogImpl`您可以建立強制回應或非強制回應對話方塊。 `CDialogImpl` 提供對話方塊程序，會使用預設的訊息對應訊息導向適當的處理常式。  
  
 基底類別解構函式 **~ CWindowImplRoot**可確保視窗已終結物件之前消失。  
  
 `CDialogImpl` 衍生自**CDialogImplBaseT**，而後者又衍生自**CWindowImplRoot**。  
  
> [!NOTE]
>  您的類別必須定義**IDD**成員，可指定對話方塊範本資源識別碼。 比方說，ATL 專案精靈自動將下列行加入至您的類別：  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 其中`MyDlg`是**簡短名稱**進入精靈的**名稱**頁面。  
  
|如需詳細資訊|請參閱|  
|--------------------------------|---------|  
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 中的對話方塊|[ATL 視窗類別](../../atl/atl-window-classes.md)|  
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|  
|對話方塊|[對話方塊](http://msdn.microsoft.com/library/windows/desktop/ms632588)和後續 Windows SDK 中的主題|  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="create"></a>  CDialogImpl::Create  
 建立非強制回應對話方塊。  
  
```  
HWND Create(
    HWND hWndParent,  
    LPARAM dwInitParam = NULL );  

HWND Create(
    HWND hWndParent,  
    RECT&, 
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 [in]主控視窗控制代碼。  
  
 **RECT （&AMP; S)** `rect`  
 [in]A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定對話方塊的大小和位置。  
  
 `dwInitParam`  
 [in]指定要傳遞至對話方塊中的值**lParam**參數**WM_INITDIALOG**訊息。  
  
### <a name="return-value"></a>傳回值  
 新建立的對話方塊控制代碼。  
  
### <a name="remarks"></a>備註  
 這個對話方塊會自動附加至`CDialogImpl`物件。 若要建立強制回應對話方塊，請呼叫[DoModal](#domodal)。 上述的第二個覆寫僅適用於[CComControl](../../atl/reference/ccomcontrol-class.md)。  
  
##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow  
 終結強制回應對話方塊。  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果對話方塊已成功終結; 否則為**FALSE**。  
  
### <a name="remarks"></a>備註  
 傳回**TRUE**如果對話方塊已成功終結; 否則為**FALSE**。  
  
##  <a name="dialogproc"></a>  CDialogImpl::DialogProc  
 此靜態函式實作對話方塊程序。  
  
```  
 
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);

 
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]對話方塊控制代碼。  
  
 `uMsg`  
 [in]傳送至對話方塊中的訊息。  
  
 `wParam`  
 [in]其他訊息的特定資訊。  
  
 `lParam`  
 [in]其他訊息的特定資訊。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**訊息是否已處理，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 `DialogProc` 使用預設的訊息對應至訊息導向適當的處理常式。  
  
 您可以覆寫`DialogProc`提供不同的機制，來處理訊息。  
  
##  <a name="domodal"></a>  CDialogImpl::DoModal  
 建立強制回應對話方塊。  
  
```   
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 [in]主控視窗控制代碼。 預設值是傳回值的[GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) Win32 函式。  
  
 `dwInitParam`  
 [in]指定要傳遞至對話方塊中的值**lParam**參數**WM_INITDIALOG**訊息。  
  
### <a name="return-value"></a>傳回值  
 如果成功，值`nRetCode`呼叫中指定的參數[EndDialog](#enddialog)。 否則為-1。  
  
### <a name="remarks"></a>備註  
 這個對話方塊會自動附加至`CDialogImpl`物件。  
  
 若要建立非強制回應對話方塊，請呼叫[建立](#create)。  
  
##  <a name="enddialog"></a>  CDialogImpl::EndDialog  
 終結強制回應對話方塊。  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>參數  
 `nRetCode`  
 [in]要傳回之值[CDialogImpl::DoModal](#domodal)。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**終結; 否則對話方塊是否**FALSE**。  
  
### <a name="remarks"></a>備註  
 `EndDialog` 必須透過對話方塊程序呼叫。 對話方塊時終結後，Windows 會使用值`nRetCode`的傳回值為`DoModal`，建立所在的對話方塊。  
  
> [!NOTE]
>  請勿呼叫`EndDialog`終結強制回應對話方塊。 呼叫[CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow)改為。  
  
##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc  
 傳回`DialogProc`，目前對話方塊程序。  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>傳回值  
 目前對話方塊程序。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以取代您自己的對話方塊程序。  
  
##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect  
 將轉換 (maps) 對話方塊單位，指定矩形到畫面的單位 （像素為單位）。  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`CRect`物件或[RECT](../../mfc/reference/rect-structure1.md)結構，這是接收更新圍住更新區域的用戶端座標。  
  
### <a name="return-value"></a>傳回值  
 如果更新成功則為非零0，如果更新失敗。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。  
  
### <a name="remarks"></a>備註  
 函數會取代位於指定座標`RECT`結構和已轉換的座標，可讓要用來建立對話方塊或調整控制項的位置 對話方塊內的結構。  
  
##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage  
 收到的最後一個訊息後呼叫 (通常`WM_NCDESTROY`)。  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]終結視窗的控制代碼。  
  
### <a name="remarks"></a>備註  
 請注意，是否您想要自動刪除您的物件，在視窗解構時，您可以呼叫`delete this;`這裡。  
  
##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc  
 只能呼叫一次，當收到第一個訊息時，處理訊息傳送至對話方塊。  
  
```   
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam); 
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]對話方塊控制代碼。  
  
 `uMsg`  
 [in]傳送至對話方塊中的訊息。  
  
 `wParam`  
 [in]其他訊息的特定資訊。  
  
 `lParam`  
 [in]其他訊息的特定資訊。  
  
### <a name="return-value"></a>傳回值  
 視窗程序。  
  
### <a name="remarks"></a>備註  
 一次呼叫之後`StartDialogProc`，`DialogProc`為設定的對話方塊程序，並進一步呼叫前往該處。  
  
## <a name="see-also"></a>另請參閱  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [類別概觀](../../atl/atl-class-overview.md)