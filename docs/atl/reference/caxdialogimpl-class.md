---
title: CAxDialogImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
dev_langs:
- C++
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd019112e846875bfa8e27faac5088fbcf1cdaef
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881983"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl 類別
這個類別會實作裝載 ActiveX 控制項對話方塊 （強制回應或非強制回應）。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class TBase = CWindow>  
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```  
  
#### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`CAxDialogImpl`。  
  
 *TBase*  
 基底的視窗類別`CDialogImplBaseT`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|呼叫這個方法來通知或取消通知在物件接收器對應事件對應中的所有項目。|  
|[CAxDialogImpl::Create](#create)|呼叫這個方法來建立非強制回應對話方塊。|  
|[CAxDialogImpl::DestroyWindow](#destroywindow)|呼叫這個方法來終結非強制回應對話方塊。|  
|[CAxDialogImpl::DoModal](#domodal)|呼叫這個方法來建立強制回應對話方塊。|  
|[CAxDialogImpl::EndDialog](#enddialog)|呼叫這個方法來終結強制回應對話方塊。|  
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|呼叫這個方法來取得變數的指標，`DialogProc`回呼函式。|  
|[CAxDialogImpl::GetIDD](#getidd)|呼叫這個方法來取得的對話方塊範本資源識別碼|  
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|呼叫這個方法來判斷訊息是否適用於此對話方塊中，如果是，處理訊息。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAxDialogImpl::m_bModal](#m_bmodal)|只存在於偵錯的變數建置，並會設為 true，如果強制回應對話方塊。|  
  
## <a name="remarks"></a>備註  
 `CAxDialogImpl` 可讓您建立強制回應或非強制回應對話方塊。 `CAxDialogImpl` 提供的對話方塊方塊程序，會使用預設的訊息對應將導向至適當的處理常式的訊息。  
  
 `CAxDialogImpl` 衍生自`CDialogImplBaseT`，而後者又衍生自*TBase* (預設`CWindow`) 和`CMessageMap`。  
  
 您的類別必須定義 IDD 成員，指定對話方塊範本資源識別碼。 例如，新增 ATL 對話方塊物件使用**加入類別**對話方塊會自動加入下面這一行至您的類別：  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]  
  
 何處`MyDialog`已**簡短名稱**ATL 對話方塊精靈中輸入。  
  
 請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)如需詳細資訊。  
  
 請注意，使用建立強制回應對話方塊上的 ActiveX 控制項`CAxDialogImpl`將不會支援快速鍵。 在對話方塊中，以建立支援快速鍵`CAxDialogImpl`，建立非強制回應對話方塊並使用您自己的訊息迴圈，使用[CAxDialogImpl::IsDialogMessage](#isdialogmessage)之後從要處理的佇列取得訊息快速鍵。  
  
 如需詳細資訊`CAxDialogImpl`，請參閱 < [ATL 控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="advisesinkmap"></a>  CAxDialogImpl::AdviseSinkMap  
 呼叫這個方法來通知或取消通知在物件接收器對應事件對應中的所有項目。  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>參數  
 *bAdvise*  
 如果接收的所有項目會接到;，設為 true如果是 all，則為 false。 接收項目是要 unadvised。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="create"></a>  CAxDialogImpl::Create  
 呼叫這個方法來建立非強制回應對話方塊。  
  
```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>參數  
 *hWndParent*  
 [in]主控視窗控制代碼。  
  
 *dwInitParam*  
 [in]指定要傳遞至對話方塊中的值*lParam* WM_INITDIALOG 訊息參數。  
  
 *RECT （&AMP; S)*  
 不使用這個參數。 此參數的傳入方式`CComControl`。  
  
### <a name="return-value"></a>傳回值  
 新建立的對話方塊中的控制代碼。  
  
### <a name="remarks"></a>備註  
 此對話方塊會自動附加至`CAxDialogImpl`物件。 若要建立強制回應對話方塊，請呼叫[DoModal](#domodal)。  
  
 只讓對話方塊可以搭配時，才提供第二個覆寫[CComControl](../../atl/reference/ccomcontrol-class.md)。  
  
##  <a name="destroywindow"></a>  CAxDialogImpl::DestroyWindow  
 呼叫這個方法來終結非強制回應對話方塊。  
  
```
BOOL DestroyWindow();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功終結視窗;，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 請勿呼叫`DestroyWindow`終結強制回應對話方塊。 呼叫[EndDialog](#enddialog)改。  
  
##  <a name="domodal"></a>  CAxDialogImpl::DoModal  
 呼叫這個方法來建立強制回應對話方塊。  
  
```
INT_PTR DoModal(
  HWND hWndParent = ::GetActiveWindow(), 
  LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>參數  
 *hWndParent*  
 [in]主控視窗控制代碼。 預設值是傳回值[GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) Win32 函式。  
  
 *dwInitParam*  
 [in]指定要傳遞至對話方塊中的值*lParam* WM_INITDIALOG 訊息參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功，值*nRetCode*呼叫中指定的參數[EndDialog](#enddialog)，否則為-1。  
  
### <a name="remarks"></a>備註  
 此對話方塊會自動附加至`CAxDialogImpl`物件。  
  
 若要建立非強制回應對話方塊，請呼叫[建立](#create)。  
  
##  <a name="enddialog"></a>  CAxDialogImpl::EndDialog  
 呼叫這個方法來終結強制回應對話方塊。  
  
```
BOOL EndDialog(int nRetCode);
```  
  
### <a name="parameters"></a>參數  
 *nRetCode*  
 [in]要傳回的值[DoModal](#domodal)。  
  
### <a name="return-value"></a>傳回值  
 如果對話方塊時終結;，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 `EndDialog` 必須透過對話方塊程序呼叫。 終結對話方塊之後，Windows 會使用值*nRetCode*的傳回值為`DoModal`，其中建立對話方塊。  
  
> [!NOTE]
>  請勿呼叫`EndDialog`終結非強制回應對話方塊。 呼叫[DestroyWindow](#destroywindow)改。  
  
##  <a name="getdialogproc"></a>  CAxDialogImpl::GetDialogProc  
 呼叫這個方法來取得變數的指標，`DialogProc`回呼函式。  
  
```
virtual DLGPROC GetDialogProc();
```  
  
### <a name="return-value"></a>傳回值  
 將指標傳回至`DialogProc`回呼函式。  
  
### <a name="remarks"></a>備註  
 `DialogProc`函式是應用程式定義的回呼函式。  
  
##  <a name="getidd"></a>  CAxDialogImpl::GetIDD  
 呼叫這個方法來取得對話方塊範本資源識別碼。  
  
```
int GetIDD();
```  
  
### <a name="return-value"></a>傳回值  
 傳回對話方塊範本資源識別碼。  
  
##  <a name="isdialogmessage"></a>  CAxDialogImpl::IsDialogMessage  
 呼叫這個方法來判斷訊息是否適用於此對話方塊中，如果是，處理訊息。  
  
```
BOOL IsDialogMessage(LPMSG pMsg);
```  
  
### <a name="parameters"></a>參數  
 *pMsg*  
 指標[MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958)結構，其中包含要檢查的訊息。  
  
### <a name="return-value"></a>傳回值  
 如果訊息已處理，否則為 FALSE 否則為 true，則傳回。  
  
### <a name="remarks"></a>備註  
 這個方法被要從訊息迴圈內呼叫。  
  
##  <a name="m_bmodal"></a>  CAxDialogImpl::m_bModal  
 只存在於偵錯的變數建置，並會設為 true，如果強制回應對話方塊。  
  
```
bool m_bModal;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDialogImpl 類別](../../atl/reference/cdialogimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
