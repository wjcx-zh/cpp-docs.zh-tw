---
title: "CComControlBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
dev_langs:
- C++
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 7ad253d42c916ec957ef1e6f5067027696103c79
ms.lasthandoff: 03/31/2017

---
# <a name="ccomcontrolbase-class"></a>CComControlBase 類別
這個類別會提供方法來建立及管理 ATL 的控制項。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class ATL_NO_VTABLE CComControlBase
```  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CComControlBase::AppearanceType](#appearancetype)|如果覆寫您`m_nAppearance`內建屬性的類型不`short`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComControlBase::CComControlBase](#ccomcontrolbase)|建構函式。|  
|[CComControlBase:: ~ CComControlBase](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|擷取所要求介面的指標。|  
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|檢查`iVerb`所使用的參數`IOleObjectImpl::DoVerb`是啟動控制項的使用者介面 (`iVerb`等於`OLEIVERB_UIACTIVATE`)，定義當使用者按兩下控制項時所採取的動作 (`iVerb`等於`OLEIVERB_PRIMARY`)，顯示控制項 (`iVerb`等於`OLEIVERB_SHOW`)，或啟動控制項 (`iVerb`等於**OLEIVERB_INPLACEACTIVATE**)。|  
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|檢查`iVerb`所使用的參數`IOleObjectImpl::DoVerb`會啟用控制項的使用者介面，並傳回**TRUE**。|  
|[CComControlBase::DoVerbProperties](#doverbproperties)|顯示控制項的屬性頁。|  
|[CComControlBase::FireViewChange](#fireviewchange)|呼叫此方法以告知容器來進行重繪控制項，或已變更控制項的檢視已註冊的通知接收的通知。|  
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|擷取**DISPID_AMBIENT_APPEARANCE**，目前設定控制項的外觀︰ 一般和 3d 1 0。|  
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|擷取**DISPID_AMBIENT_AUTOCLIP**、 旗標，指出容器是否支援自動裁剪控制項顯示區域。|  
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|擷取**DISPID_AMBIENT_BACKCOLOR**，容器所定義的所有控制項的環境背景色彩。|  
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|擷取**DISPID_AMBIENT_CHARSET**，該環境的字集容器所定義的所有控制項。|  
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|擷取**DISPID_AMBIENT_CODEPAGE**，該環境的字集容器所定義的所有控制項。|  
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|擷取**DISPID_AMBIENT_DISPLAYASDEFAULT**的旗標**TRUE**如果容器已標示為預設按鈕，此站台中的控制項，因此將按鈕控制項應該繪製本身具有較粗的框架。|  
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|擷取**DISPID_AMBIENT_DISPLAYNAME**，容器已提供給控制項的名稱。|  
|[CComControlBase::GetAmbientFont](#getambientfont)|擷取容器的指標的環境`IFont`介面。|  
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|擷取容器的指標的環境**IFontDisp**分派介面。|  
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|擷取**DISPID_AMBIENT_FORECOLOR**，容器所定義的所有控制項的前景色彩。|  
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|擷取**DISPID_AMBIENT_LOCALEID**，容器所使用的語言識別項。|  
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|擷取**DISPID_AMBIENT_MESSAGEREFLECT**、 旗標，指出容器是否要接收的視窗訊息 (例如`WM_DRAWITEM`) 做為事件。|  
|[CComControlBase::GetAmbientPalette](#getambientpalette)|擷取**DISPID_AMBIENT_PALETTE**，用來存取容器的`HPALETTE`。|  
|[CComControlBase::GetAmbientProperty](#getambientproperty)|擷取所指定的容器屬性`id`。|  
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|擷取**DISPID_AMBIENT_RIGHTTOLEFT**，容器所顯示內容的方向。|  
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|擷取**DISPID_AMBIENT_SCALEUNITS**，容器的環境單位 （例如英吋或公分為單位） 的標記顯示。|  
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|擷取**DISPID_AMBIENT_SHOWGRABHANDLES**、 旗標，指出容器是否允許控制項本身現用時顯示抓取控點。|  
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|擷取**DISPID_AMBIENT_SHOWHATCHING**、 旗標，指出容器是否允許控制項本身顯示影線圖樣，UI 是作用中時。|  
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|擷取**DISPID_AMBIENT_SUPPORTSMNEMONICS**、 旗標，指出容器是否支援鍵盤助憶鍵。|  
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|擷取**DISPID_AMBIENT_TEXTALIGN**，容器所慣用的文字對齊方式︰ 0 代表一般對齊 （數字右邊，文字靠左對齊），1 表示靠左對齊、 置中對齊的 2，3 靠右對齊。|  
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|擷取**DISPID_AMBIENT_TOPTOBOTTOM**，容器所顯示內容的方向。|  
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|擷取**DISPID_AMBIENT_UIDEAD**、 旗標，指出容器是否想要回應使用者介面動作的控制項。|  
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|擷取**DISPID_AMBIENT_USERMODE**、 旗標，指出容器是否處於執行模式 ( **TRUE**) 或設計模式 ( **FALSE**)。|  
|[CComControlBase::GetDirty](#getdirty)|傳回的資料成員值`m_bRequiresSave`。|  
|[CComControlBase::GetZoomInfo](#getzoominfo)|擷取的 x 和 y 分子和縮放因數的分母的值為控制項啟用就地編輯。|  
|[CComControlBase::InPlaceActivate](#inplaceactivate)|導致控制項從任何狀態中的動詞命令的非作用中狀態轉換`iVerb`表示。|  
|[CComControlBase::InternalGetSite](#internalgetsite)|呼叫這個方法來查詢所識別的介面指標的控制站台。|  
|[CComControlBase::OnDraw](#ondraw)|覆寫這個方法，以繪製您的控制項。|  
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|預設值**OnDrawAdvanced**準備進行繪圖，標準化的裝置內容，則會呼叫您的控制項類別`OnDraw`方法。|  
|[CComControlBase::OnKillFocus](#onkillfocus)|檢查控制項已就地啟用作用中且具有有效的控制站台，然後通知容器控制項已遺失焦點時。|  
|[CComControlBase::OnMouseActivate](#onmouseactivate)|檢查 UI 是以使用者模式，則啟動控制項。|  
|[CComControlBase::OnPaint](#onpaint)|準備容器以進行繪製，請取得控制項的工作區，然後會呼叫控制項類別`OnDraw`方法。|  
|[CComControlBase::OnSetFocus](#onsetfocus)|檢查控制項已就地啟用作用中且具有有效的控制站台，然後通知控制項的容器已取得焦點。|  
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|覆寫這個方法以提供您自己的鍵盤快速鍵對應處理常式。|  
|[CComControlBase::SendOnClose](#sendonclose)|通知控制項已關閉的通知持有者註冊的所有諮詢接收。|  
|[CComControlBase::SendOnDataChange](#sendondatachange)|通知控制項資料已變更的通知持有者註冊的所有諮詢接收。|  
|[CComControlBase::SendOnRename](#sendonrename)|通知控制項有新的 moniker advise 持有者註冊的所有諮詢接收。|  
|[CComControlBase::SendOnSave](#sendonsave)|通知註冊在儲存控制項的通知持有者的所有諮詢接收。|  
|[CComControlBase::SendOnViewChange](#sendonviewchange)|通知所有註冊的控制項的檢視已變更的諮詢接收。|  
|[CComControlBase::SetControlFocus](#setcontrolfocus)|設定或移除鍵盤焦點的控制項。|  
|[CComControlBase::SetDirty](#setdirty)|設定資料成員`m_bRequiresSave`值以`bDirty`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComControlBase::m_bAutoSize](#m_bautosize)|表示控制項的任何其他大小不能為旗標。|  
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|旗標指出`IDataObjectImpl::GetData`和`CComControlBase::GetZoomInfo`應該設定中的控制項大小`m_sizeNatural`而不是從`m_sizeExtent`。|  
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|旗標指出`IDataObjectImpl::GetData`應該使用 HIMETRIC 單位並不像素繪製時。|  
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|表示控制項就地啟用作用中的旗標。|  
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|旗標，指出此容器支援**IOleInPlaceSiteEx**介面和 OCX96 控制功能，例如無視窗和閃爍的控制項。|  
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|表示控制項有交涉與容器相關功能的支援 OCX96 控制項 （例如閃爍的及無視窗控制項），和視窗化或是無視窗控制項的是否旗標。|  
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|表示控制項想要重新撰寫其簡報，容器會變更控制項的顯示大小時旗標。|  
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|表示控制項在自上次儲存後已變更的旗標。|  
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|旗標，指出控制項要調整大小的自然範圍 （其未縮放的實體大小） 當容器會變更控制項的顯示大小。|  
|[CComControlBase::m_bUIActive](#m_buiactive)|旗標，指出控制項的使用者介面，例如功能表和工具列，才有作用。|  
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|旗標，指出控制項使用容器提供的視窗區域。|  
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|表示控制項已無視窗，但可能會或可能不是無視窗現在旗標。|  
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|表示控制項應該視窗，即使容器支援無視窗控制項旗標。|  
|[CComControlBase::m_bWndLess](#m_bwndless)|表示控制項無視窗旗標。|  
|[CComControlBase::m_hWndCD](#m_hwndcd)|包含與控制項關聯的視窗控制代碼的參考。|  
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|次數的計數容器有不含事件 （事件接受） 中介解除凍結凍結 （拒絕接受事件） 的事件。|  
|[CComControlBase::m_rcPos](#m_rcpos)|表示在容器座標中控制項的像素的位置。|  
|[CComControlBase::m_sizeExtent](#m_sizeextent)|以 himetric 為單位 （每一單位為 0.01 公釐為單位） 的特定顯示控制項的範圍。|  
|[CComControlBase::m_sizeNatural](#m_sizenatural)|實體控制項以 himetric 為單位 （每一單位為 0.01 公釐為單位） 的大小。|  
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|在容器上諮詢連接的直接指標 (在容器的[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513))。|  
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A`CComDispatchDriver`物件，可讓您擷取及設定容器的屬性，透過`IDispatch`指標。|  
|[CComControlBase::m_spClientSite](#m_spclientsite)|控制項的容器內的用戶端站台指標。|  
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|提供標準方式來保存資料物件之間的諮詢連接及接收的通知。|  
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|容器的指標[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)介面指標。|  
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|提供方式保存諮詢連接的標準實作。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供方法來建立及管理 ATL 的控制項。 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)衍生自`CComControlBase`。 當您建立標準控制項或 DHTML 控制項，使用 ATL 控制項精靈時，精靈會自動衍生您的類別，從`CComControlBase`。  
  
 如需建立控制項的詳細資訊，請參閱[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。 如需 ATL 專案精靈的詳細資訊，請參閱文章[ATL 專案建立](../../atl/reference/creating-an-atl-project.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="appearancetype"></a>CComControlBase::AppearanceType  
 如果覆寫您**m_nAppearance**內建屬性的類型不**簡短**。  
  
```
typedef short AppearanceType;
```  
  
### <a name="remarks"></a>備註  
 ATL 控制項精靈新增**m_nAppearance**內建類型的簡短的屬性。 覆寫`AppearanceType`如果您使用不同的資料類型。  
  
##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase  
 建構函式。  
  
```
CComControlBase(HWND& h);
```  
  
### <a name="parameters"></a>參數  
 `h`  
 與控制項關聯的視窗控制代碼。  
  
### <a name="remarks"></a>備註  
 初始化 5080 X 5080 himetric 為單位的控制項大小 (2x"2")，並初始化`CComControlBase`資料成員值來**NULL**或**FALSE**。  
  
##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase  
 解構函式。  
  
```
~CComControlBase();
```  
  
### <a name="remarks"></a>備註  
 如果控制項是視窗，`~CComControlBase`終結藉由呼叫[DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682)。  
  
##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface  
 擷取所要求介面的指標。  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 所要求介面的 GUID。  
  
 `ppv`  
 所識別的介面指標的指標`iid`，或**NULL**如果找不到介面。  
  
### <a name="remarks"></a>備註  
 只處理 COM 對應表格中的介面。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM #15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]  
  
##  <a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate  
 檢查`iVerb`所使用的參數`IOleObjectImpl::DoVerb`是啟動控制項的使用者介面 (`iVerb`等於`OLEIVERB_UIACTIVATE`)，定義當使用者按兩下控制項時所採取的動作 (`iVerb`等於`OLEIVERB_PRIMARY`)，顯示控制項 (`iVerb`等於`OLEIVERB_SHOW`)，或啟動控制項 (`iVerb`等於**OLEIVERB_INPLACEACTIVATE**)。  
  
```
BOOL DoesVerbActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>參數  
 `iVerb`  
 值，指出要執行的動作`DoVerb`。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果`iVerb`等於`OLEIVERB_UIACTIVATE`， `OLEIVERB_PRIMARY`， `OLEIVERB_SHOW`，或**OLEIVERB_INPLACEACTIVATE**; 否則傳回**FALSE**。  
  
### <a name="remarks"></a>備註  
 您可以覆寫這個方法，以定義您自己的啟用指令動詞。  
  
##  <a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate  
 檢查`iVerb`所使用的參數`IOleObjectImpl::DoVerb`會啟用控制項的使用者介面，並傳回**TRUE**。  
  
```
BOOL DoesVerbUIActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>參數  
 `iVerb`  
 值，指出要執行的動作`DoVerb`。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果`iVerb`等於`OLEIVERB_UIACTIVATE`， `OLEIVERB_PRIMARY`， `OLEIVERB_SHOW`，或**OLEIVERB_INPLACEACTIVATE**。 否則，方法會傳回**FALSE**。  
  
##  <a name="doverbproperties"></a>CComControlBase::DoVerbProperties  
 顯示控制項的屬性頁。  
  
```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 保留的。  
  
 *hwndParent*  
 包含控制項的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM #19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]  
  
 [!code-cpp[NVC_ATL_COM #20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]  
  
##  <a name="fireviewchange"></a>CComControlBase::FireViewChange  
 呼叫此方法以告知容器來進行重繪控制項，或已變更控制項的檢視已註冊的通知接收的通知。  
  
```
HRESULT FireViewChange();
```  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 控制是否在作用中 (控制項的類別資料成員[CComControlBase::m_bInPlaceActive](#m_binplaceactive)是**TRUE**)，通知您想要重新繪製整個控制項的容器。 如果控制項處於非使用中，會通知控制項的登錄通知接收 (透過控制項的類別資料成員[CComControlBase::m_spAdviseSink](#m_spadvisesink)) 控制項的檢視已變更。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM #21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]  
  
##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance  
 擷取**DISPID_AMBIENT_APPEARANCE**，目前設定控制項的外觀︰ 一般和 3d 1 0。  
  
```
HRESULT GetAmbientAppearance(short& nAppearance);
```  
  
### <a name="parameters"></a>參數  
 `nAppearance`  
 屬性**DISPID_AMBIENT_APPEARANCE**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM #22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]  
  
##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip  
 擷取**DISPID_AMBIENT_AUTOCLIP**、 旗標，指出容器是否支援自動裁剪控制項顯示區域。  
  
```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```  
  
### <a name="parameters"></a>參數  
 *bAutoClip*  
 屬性**DISPID_AMBIENT_AUTOCLIP**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor  
 擷取**DISPID_AMBIENT_BACKCOLOR**，容器所定義的所有控制項的環境背景色彩。  
  
```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```  
  
### <a name="parameters"></a>參數  
 *背景色彩*  
 屬性**DISPID_AMBIENT_BACKCOLOR**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet  
 擷取**DISPID_AMBIENT_CHARSET**，該環境的字集容器所定義的所有控制項。  
  
```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```  
  
### <a name="parameters"></a>參數  
 *bstrCharSet*  
 屬性**DISPID_AMBIENT_CHARSET**。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage  
 擷取**DISPID_AMBIENT_CODEPAGE**，容器所定義的所有控制項的環境的字碼頁。  
  
```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```  
  
### <a name="parameters"></a>參數  
 *ulCodePage*  
 屬性**DISPID_AMBIENT_CODEPAGE**。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault  
 擷取**DISPID_AMBIENT_DISPLAYASDEFAULT**的旗標**TRUE**如果容器已標示為預設按鈕，此站台中的控制項，因此將按鈕控制項應該繪製本身具有較粗的框架。  
  
```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```  
  
### <a name="parameters"></a>參數  
 `bDisplayAsDefault`  
 屬性**DISPID_AMBIENT_DISPLAYASDEFAULT**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName  
 擷取**DISPID_AMBIENT_DISPLAYNAME**，容器已提供給控制項的名稱。  
  
```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```  
  
### <a name="parameters"></a>參數  
 *bstrDisplayName*  
 屬性**DISPID_AMBIENT_DISPLAYNAME**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont  
 擷取容器的指標的環境`IFont`介面。  
  
```
HRESULT GetAmbientFont(IFont** ppFont);
```  
  
### <a name="parameters"></a>參數  
 `ppFont`  
 容器的指標的環境[IFont](http://msdn.microsoft.com/library/windows/desktop/ms680673)介面。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 如果屬性是**NULL**，指標**NULL**。 如果指標不是**NULL**，呼叫端必須釋放指標。  
  
##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp  
 擷取容器的指標的環境**IFontDisp**分派介面。  
  
```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>參數  
 `ppFont`  
 容器的指標的環境[IFontDisp](http://msdn.microsoft.com/library/windows/desktop/ms692695)分派介面。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 如果屬性是**NULL**，指標**NULL**。 如果指標不是**NULL**，呼叫端必須釋放指標。  
  
##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor  
 擷取**DISPID_AMBIENT_FORECOLOR**，容器所定義的所有控制項的前景色彩。  
  
```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```  
  
### <a name="parameters"></a>參數  
 *前景色彩*  
 屬性**DISPID_AMBIENT_FORECOLOR**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID  
 擷取**DISPID_AMBIENT_LOCALEID**，容器所使用的語言識別項。  
  
```
HRESULT GetAmbientLocaleID(LCID& lcid);
```  
  
### <a name="parameters"></a>參數  
 `lcid`  
 屬性**DISPID_AMBIENT_LOCALEID**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 控制項可以使用這個識別碼，來調整其使用者介面，以不同的語言。  
  
##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect  
 擷取**DISPID_AMBIENT_MESSAGEREFLECT**、 旗標，指出容器是否要接收的視窗訊息 (例如`WM_DRAWITEM`) 做為事件。  
  
```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```  
  
### <a name="parameters"></a>參數  
 `bMessageReflect`  
 屬性**DISPID_AMBIENT_MESSAGEREFLECT**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette  
 擷取**DISPID_AMBIENT_PALETTE**，用來存取容器的`HPALETTE`。  
  
```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```  
  
### <a name="parameters"></a>參數  
 `hPalette`  
 屬性**DISPID_AMBIENT_PALETTE**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty  
 擷取所指定的容器屬性`dispid`。  
  
```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 要擷取之容器屬性的識別項。  
  
 `var`  
 用來接收屬性變數。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 ATL 提供 helper 函式來擷取特定屬性，例如，一組[CComControlBase::GetAmbientBackColor](#getambientbackcolor)。 如果沒有任何合適的方法，使用`GetAmbientProperty`。  
  
##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft  
 擷取**DISPID_AMBIENT_RIGHTTOLEFT**，容器所顯示內容的方向。  
  
```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```  
  
### <a name="parameters"></a>參數  
 *bRightToLeft*  
 屬性**DISPID_AMBIENT_RIGHTTOLEFT**。 設定為**TRUE**內容會顯示由右至左，如果**FALSE**如果它會顯示向左到右。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits  
 擷取**DISPID_AMBIENT_SCALEUNITS**，容器的環境單位 （例如英吋或公分為單位） 的標記顯示。  
  
```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```  
  
### <a name="parameters"></a>參數  
 *bstrScaleUnits*  
 屬性**DISPID_AMBIENT_SCALEUNITS**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles  
 擷取**DISPID_AMBIENT_SHOWGRABHANDLES**、 旗標，指出容器是否允許控制項本身現用時顯示抓取控點。  
  
```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```  
  
### <a name="parameters"></a>參數  
 *bShowGrabHandles*  
 屬性**DISPID_AMBIENT_SHOWGRABHANDLES**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching  
 擷取**DISPID_AMBIENT_SHOWHATCHING**、 旗標，指出容器是否允許控制項本身顯示影線圖樣，當控制項的使用者介面在使用中。  
  
```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```  
  
### <a name="parameters"></a>參數  
 *bShowHatching*  
 屬性**DISPID_AMBIENT_SHOWHATCHING**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics  
 擷取**DISPID_AMBIENT_SUPPORTSMNEMONICS**、 旗標，指出容器是否支援鍵盤助憶鍵。  
  
```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```  
  
### <a name="parameters"></a>參數  
 *bSupportsMnemonics*  
 屬性**DISPID_AMBIENT_SUPPORTSMNEMONICS**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign  
 擷取**DISPID_AMBIENT_TEXTALIGN**，容器所慣用的文字對齊方式︰ 0 代表一般對齊 （數字右邊，文字靠左對齊），1 表示靠左對齊、 置中對齊的 2，3 靠右對齊。  
  
```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```  
  
### <a name="parameters"></a>參數  
 *nTextAlign*  
 屬性**DISPID_AMBIENT_TEXTALIGN**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom  
 擷取**DISPID_AMBIENT_TOPTOBOTTOM**，容器所顯示內容的方向。  
  
```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```  
  
### <a name="parameters"></a>參數  
 *bTopToBottom*  
 屬性**DISPID_AMBIENT_TOPTOBOTTOM**。 設定為**TRUE**如果文字會顯示從上到下， **FALSE**如果它顯示往上的。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead  
 擷取**DISPID_AMBIENT_UIDEAD**、 旗標，指出容器是否想要回應使用者介面動作的控制項。  
  
```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```  
  
### <a name="parameters"></a>參數  
 *bUIDead*  
 屬性**DISPID_AMBIENT_UIDEAD**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 如果**TRUE**，不應回應控制項。 這個旗標適用於不論**DISPID_AMBIENT_USERMODE**旗標。 請參閱[CComControlBase::GetAmbientUserMode](#getambientusermode)。  
  
##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode  
 擷取**DISPID_AMBIENT_USERMODE**、 旗標，指出容器是否處於執行模式 ( **TRUE**) 或設計模式 ( **FALSE**)。  
  
```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```  
  
### <a name="parameters"></a>參數  
 `bUserMode`  
 屬性**DISPID_AMBIENT_USERMODE**。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
##  <a name="getdirty"></a>CComControlBase::GetDirty  
 傳回的資料成員值`m_bRequiresSave`。  
  
```
BOOL GetDirty();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的資料成員值[m_bRequiresSave](#m_brequiressave)。  
  
### <a name="remarks"></a>備註  
 這個值會設定使用[CComControlBase::SetDirty](#setdirty)。  
  
##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo  
 擷取的 x 和 y 分子和縮放因數的分母的值為控制項啟用就地編輯。  
  
```
void GetZoomInfo(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>參數  
 `di`  
 結構，用以保存縮放因數分子，分母。 如需詳細資訊，請參閱[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。  
  
### <a name="remarks"></a>備註  
 縮放因數是其目前的範圍內的控制項的原始大小的比例。  
  
##  <a name="inplaceactivate"></a>CComControlBase::InPlaceActivate  
 導致控制項從任何狀態中的動詞命令的非作用中狀態轉換`iVerb`表示。  
  
```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 `iVerb`  
 值，指出要執行的動作[IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)。  
  
 *prcPosRect*  
 在就地控制項的位置指標。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 之前啟動，這個方法會檢查控制項具有用戶端站台、 檢查多少控制項是可見的並取得父視窗中控制項的位置。 啟用控制項之後，這個方法會啟用控制項的使用者介面，並告知容器將控制項設為可見。  
  
 這個方法也會擷取`IOleInPlaceSite`， **IOleInPlaceSiteEx**，或**IOleInPlaceSiteWindowless**控制項的介面指標並將它儲存在控制項類別的資料成員[CComControlBase::m_spInPlaceSite](#m_spinplacesite)。 控制項類別資料成員[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)， [CComControlBase::m_bWndLess](#m_bwndless)， [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)，和[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)設為 true，則依適當情況。  
  
##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite  
 呼叫這個方法來查詢所識別的介面指標的控制站台。  
  
```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```  
  
### <a name="parameters"></a>參數  
 `riid`  
 應該在傳回的介面指標的 IID `ppUnkSite`。  
  
 `ppUnkSite`  
 接收要求中的介面指標的指標變數的位址`riid`。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 如果站台支援所要求的介面`riid`，藉由傳回的指標`ppUnkSite`。 否則，`ppUnkSite`設為 NULL。  
  
##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize  
 表示控制項的任何其他大小不能為旗標。  
  
```
unsigned m_bAutoSize:1;
```  
  
### <a name="remarks"></a>備註  
 這個旗標會檢查`IOleObjectImpl::SetExtent`而如果**TRUE**，會導致此函數傳回**E_FAIL**。  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 如果您將加入**自動調整大小的**選項[內建屬性](../../atl/reference/stock-properties-atl-control-wizard.md) 索引標籤的 ATL 控制項精靈，精靈會自動在您的控制項類別中建立此資料成員、 建立放入並取得屬性，以及支援的方法[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)屬性變更時自動通知容器。  
  
##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural  
 旗標指出`IDataObjectImpl::GetData`和`CComControlBase::GetZoomInfo`應該設定中的控制項大小`m_sizeNatural`而不是從`m_sizeExtent`。  
  
```
unsigned m_bDrawFromNatural:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric  
 旗標指出`IDataObjectImpl::GetData`應該使用 HIMETRIC 單位並不像素繪製時。  
  
```
unsigned m_bDrawGetDataInHimetric:1;
```  
  
### <a name="remarks"></a>備註  
 每個邏輯 HIMETRIC 單位為 0.01 公釐。  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive  
 表示控制項就地啟用作用中的旗標。  
  
```
unsigned m_bInPlaceActive:1;
```  
  
### <a name="remarks"></a>備註  
 這表示此控制項是可見和其視窗中，如果有的話，會顯示，但其功能表與工具列可能不在作用中。 `m_bUIActive`旗標，指出控制項的使用者介面，例如功能表，也是使用中。  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx  
 旗標，指出此容器支援**IOleInPlaceSiteEx**介面和 OCX96 控制功能，例如無視窗和閃爍的控制項。  
  
```
unsigned m_bInPlaceSiteEx:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 資料成員`m_spInPlaceSite`指向[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)介面，根據的值`m_bWndLess`和`m_bInPlaceSiteEx`旗標。 (資料成員`m_bNegotiatedWnd`必須**TRUE**如`m_spInPlaceSite`為有效的指標。)  
  
 如果`m_bWndLess`是**FALSE**和`m_bInPlaceSiteEx`是**TRUE**，`m_spInPlaceSite`是**IOleInPlaceSiteEx**介面指標。 請參閱[m_spInPlaceSite](#m_spinplacesite)顯示這些三個資料成員之間的關聯性的資料表。  
  
##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd  
 表示控制項有交涉與容器相關功能的支援 OCX96 控制項 （例如閃爍的及無視窗控制項），和視窗化或是無視窗控制項的是否旗標。  
  
```
unsigned m_bNegotiatedWnd:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 `m_bNegotiatedWnd`旗標必須是**TRUE**如`m_spInPlaceSite`為有效的指標。  
  
##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize  
 表示控制項想要重新撰寫其簡報，容器會變更控制項的顯示大小時旗標。  
  
```
unsigned m_bRecomposeOnResize:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 這個旗標會檢查[IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent)而如果**TRUE**，`SetExtent`告知容器的檢視變更。 如果設定此旗標， **OLEMISC_RECOMPOSEONRESIZE**位元[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)也應該設定列舉型別。  
  
##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave  
 表示控制項在自上次儲存後已變更的旗標。  
  
```
unsigned m_bRequiresSave:1;
```  
  
### <a name="remarks"></a>備註  
 值`m_bRequiresSave`可以透過設定[CComControlBase::SetDirty](#setdirty)和擷取與[CComControlBase::GetDirty](#getdirty)。  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural  
 旗標，指出控制項要調整大小的自然範圍 （其未縮放的實體大小） 當容器會變更控制項的顯示大小。  
  
```
unsigned m_bResizeNatural:1;
```  
  
### <a name="remarks"></a>備註  
 這個旗標會檢查`IOleObjectImpl::SetExtent`而如果**TRUE**，大小傳入`SetExtent`指派給`m_sizeNatural`。  
  
 大小傳入`SetExtent`一定會指派給`m_sizeExtent`，不論值的`m_bResizeNatural`。  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive  
 旗標，指出控制項的使用者介面，例如功能表和工具列，才有作用。  
  
```
unsigned m_bUIActive:1;
```  
  
### <a name="remarks"></a>備註  
 `m_bInPlaceActive`旗標指出此控制項是作用中，但不是會其使用者介面為作用中。  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn  
 旗標，指出控制項使用容器提供的視窗區域。  
  
```
unsigned m_bUsingWindowRgn:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless  
 表示控制項已無視窗，但可能會或可能不是無視窗現在旗標。  
  
```
unsigned m_bWasOnceWindowless:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly  
 表示控制項應該視窗，即使容器支援無視窗控制項旗標。  
  
```
unsigned m_bWindowOnly:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess  
 表示控制項無視窗旗標。  
  
```
unsigned m_bWndLess:1;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 資料成員`m_spInPlaceSite`指向[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)介面，根據的值`m_bWndLess`和[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)旗標。 (資料成員[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)必須**TRUE**如[CComControlBase::m_spInPlaceSite](#m_spinplacesite)為有效的指標。)  
  
 如果`m_bWndLess`是**TRUE**，`m_spInPlaceSite`是**IOleInPlaceSiteWindowless**介面指標。 請參閱[CComControlBase::m_spInPlaceSite](#m_spinplacesite)顯示這些資料成員之間的完整關聯性的資料表。  
  
##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD  
 包含與控制項關聯的視窗控制代碼的參考。  
  
```
HWND& m_hWndCD;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents  
 次數的計數容器有不含事件 （事件接受） 中介解除凍結凍結 （拒絕接受事件） 的事件。  
  
```
short m_nFreezeEvents;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_rcpos"></a>CComControlBase::m_rcPos  
 表示在容器座標中控制項的像素的位置。  
  
```
RECT m_rcPos;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent  
 以 himetric 為單位 （每一單位為 0.01 公釐為單位） 的特定顯示控制項的範圍。  
  
```
SIZE m_sizeExtent;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 此大小會調整的顯示。 控制項的實體大小以指定`m_sizeNatural`資料成員和固定的。  
  
 您可以將大小轉換成與全域函式的像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。  
  
##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural  
 實體控制項以 himetric 為單位 （每一單位為 0.01 公釐為單位） 的大小。  
  
```
SIZE m_sizeNatural;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 此大小固定的同時在大小`m_sizeExtent`調整所顯示。  
  
 您可以將大小轉換成與全域函式的像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。  
  
##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink  
 在容器上諮詢連接的直接指標 (在容器的[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513))。  
  
```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```     
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch  
 A`CComDispatchDriver`物件，可讓您擷取和設定物件的屬性，透過`IDispatch`指標。  
  
```
CComDispatchDriver m_spAmbientDispatch;
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite  
 控制項的容器內的用戶端站台指標。  
  
```
CComPtr<IOleClientSite>
    m_spClientSite;
```     
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder  
 提供標準方式來保存資料物件之間的諮詢連接及接收的通知。  
  
```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```     
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 資料物件是的控制項，可將資料傳送，以及實作[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)，其方法指定的資料格式和傳送媒體。  
  
 介面`m_spDataAdviseHolder`實作[IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579)和[IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448)方法來建立和刪除諮詢連接的容器。 控制項的容器必須實作通知接收支援[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)介面。  
  
##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite  
 容器的指標[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)介面指標。  
  
```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```     
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 `m_spInPlaceSite`指標無效才[m_bNegotiatedWnd](#m_bnegotiatedwnd)旗標是**TRUE**。  
  
 下表顯示如何`m_spInPlaceSite`指標類型取決於[m_bWndLess](#m_bwndless)和[m_bInPlaceSiteEx](#m_binplacesiteex)資料成員的旗標︰  
  
|m_spInPlaceSite 類型|m_bWndLess 值|m_bInPlaceSiteEx 值|  
|---------------------------|-----------------------|-----------------------------|  
|**IOleInPlaceSiteWindowless**|**為 TRUE**|**TRUE**或**FALSE**|  
|**IOleInPlaceSiteEx**|**FALSE**|**為 TRUE**|  
|`IOleInPlaceSite`|**FALSE**|**FALSE**|  
  
##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder  
 提供方式保存諮詢連接的標準實作。  
  
```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```     
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  若要使用此控制類別內的資料成員，您必須將它宣告為資料成員在控制項類別中。 因為它宣告為基底類別中的等位內控制項類別不會從基底類別繼承此資料成員。  
  
 介面`m_spOleAdviseHolder`實作[IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573)和[IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749)方法來建立和刪除諮詢連接的容器。 控制項的容器必須實作通知接收支援[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)介面。  
  
##  <a name="ondraw"></a>CComControlBase::OnDraw  
 覆寫這個方法，以繪製您的控制項。  
  
```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>參數  
 `di`  
 參考[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)結構，其中包含繪圖的資訊，例如繪圖外觀，控制項界限內，而且是否繪圖已最佳化或沒有。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 預設值`OnDraw`刪除或還原裝置內容或不做任何動作，根據設定旗標[CComControlBase::OnDrawAdvanced](#ondrawadvanced)。  
  
 `OnDraw`方法會自動加入至您的控制項類別的 ATL 控制項精靈建立您的控制項時。 精靈的預設`OnDraw`繪製的矩形"ATL 8.0"的標籤。  
  
### <a name="example"></a>範例  
 請參閱範例的[CComControlBase::GetAmbientAppearance](#getambientappearance)。  
  
##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced  
 預設值`OnDrawAdvanced`準備進行繪圖，標準化的裝置內容，則會呼叫您的控制項類別`OnDraw`方法。  
  
```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>參數  
 `di`  
 參考[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)結構，其中包含繪圖的資訊，例如繪圖外觀，控制項界限內，而且是否繪圖已最佳化或沒有。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果您想要接受由容器通過卻未標準化的裝置內容，請覆寫這個方法。  
  
 請參閱[CComControlBase::OnDraw](#ondraw)如需詳細資訊。  
  
##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus  
 檢查控制項已就地啟用作用中且具有有效的控制站台，然後通知容器控制項已遺失焦點時。  
  
```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>參數  
 `nMsg`  
 保留的。  
  
 `wParam`  
 保留的。  
  
 `lParam`  
 保留的。  
  
 `bHandled`  
 旗標，指出是否已成功處理的視窗訊息。 預設為 `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 一定會傳回 1。  
  
##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate  
 檢查 UI 是以使用者模式，則啟動控制項。  
  
```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>參數  
 `nMsg`  
 保留的。  
  
 `wParam`  
 保留的。  
  
 `lParam`  
 保留的。  
  
 `bHandled`  
 旗標，指出是否已成功處理的視窗訊息。 預設為 `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 一定會傳回 1。  
  
##  <a name="onpaint"></a>CComControlBase::OnPaint  
 準備容器以進行繪製，請取得控制項的工作區，然後會呼叫控制項類別`OnDrawAdvanced`方法。  
  
```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```  
  
### <a name="parameters"></a>參數  
 `nMsg`  
 保留的。  
  
 `wParam`  
 現有的 HDC。  
  
 `lParam`  
 保留的。  
  
 `lResult`  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 一律會傳回零。  
  
### <a name="remarks"></a>備註  
 如果`wParam`不是 NULL，`OnPaint`假設它包含有效的 HDC，並使用它，而不要[CComControlBase::m_hWndCD](#m_hwndcd)。  
  
##  <a name="onsetfocus"></a>CComControlBase::OnSetFocus  
 檢查控制項已就地啟用作用中且具有有效的控制站台，然後通知控制項的容器已取得焦點。  
  
```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>參數  
 `nMsg`  
 保留的。  
  
 `wParam`  
 保留的。  
  
 `lParam`  
 保留的。  
  
 `bHandled`  
 旗標，指出是否已成功處理的視窗訊息。 預設為 `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 一定會傳回 1。  
  
### <a name="remarks"></a>備註  
 傳送通知到容器控制項已收到焦點。  
  
##  <a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator  
 覆寫這個方法以提供您自己的鍵盤快速鍵對應處理常式。  
  
```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```  
  
### <a name="parameters"></a>參數  
 `pMsg`  
 保留的。  
  
 *hRet*  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 根據預設會傳回**FALSE**。  
  
##  <a name="sendonclose"></a>CComControlBase::SendOnClose  
 通知控制項已關閉的通知持有者註冊的所有諮詢接收。  
  
```
HRESULT SendOnClose();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 傳送控制項已關閉其諮詢接收通知。  
  
##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange  
 通知控制項資料已變更的通知持有者註冊的所有諮詢接收。  
  
```
HRESULT SendOnDataChange(DWORD advf = 0);
```  
  
### <a name="parameters"></a>參數  
 *advf*  
 通知旗標，指定如何對呼叫[IAdviseSink::OnDataChange](http://msdn.microsoft.com/library/windows/desktop/ms687283)進行。 值是從[ADVF](http://msdn.microsoft.com/library/windows/desktop/ms693742)列舉型別。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="sendonrename"></a>CComControlBase::SendOnRename  
 通知控制項有新的 moniker advise 持有者註冊的所有諮詢接收。  
  
```
HRESULT SendOnRename(IMoniker* pmk);
```  
  
### <a name="parameters"></a>參數  
 *pmk*  
 新的 moniker 控制項的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 傳送通知控制項 moniker 已變更。  
  
##  <a name="sendonsave"></a>CComControlBase::SendOnSave  
 通知註冊在儲存控制項的通知持有者的所有諮詢接收。  
  
```
HRESULT SendOnSave();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 傳送通知控制項只具有儲存其資料。  
  
##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange  
 通知所有註冊的控制項的檢視已變更的諮詢接收。  
  
```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```  
  
### <a name="parameters"></a>參數  
 `dwAspect`  
 外觀或控制項檢視。  
  
 *lindex*  
 檢視已變更的部分。 只能為-1 是有效的。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 `SendOnViewChange`呼叫[IAdviseSink::OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337)。 唯一值的*lindex*目前支援為-1，這表示感興趣的是整個檢視。  
  
##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus  
 設定或移除鍵盤焦點的控制項。  
  
```
BOOL SetControlFocus(BOOL bGrab);
```  
  
### <a name="parameters"></a>參數  
 *bGrab*  
 如果**TRUE**，將鍵盤焦點設定為呼叫控制項。 如果**FALSE**，從呼叫控制項，移除鍵盤焦點，提供有焦點。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果控制項已成功接收焦點; 否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 針對視窗型控制項，而 Windows API 函式[SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms646312)呼叫。 無視窗控制項， [IOleInPlaceSiteWindowless::SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms679745)呼叫。 透過此呼叫，將無視窗控制項取得鍵盤焦點，以及可以回應的視窗訊息。  
  
##  <a name="setdirty"></a>CComControlBase::SetDirty  
 設定資料成員`m_bRequiresSave`值以`bDirty`。  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>參數  
 `bDirty`  
 資料成員的值[CComControlBase::m_bRequiresSave](#m_brequiressave)。  
  
### <a name="remarks"></a>備註  
 **SetDirty(TRUE)**應該加上旗標已變更的控制項，自上次儲存後呼叫。 值`m_bRequiresSave`擷取與[CComControlBase::GetDirty](#getdirty)。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

