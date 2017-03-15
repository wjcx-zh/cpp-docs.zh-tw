---
title: "COleControl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleControl
dev_langs:
- C++
helpviewer_keywords:
- OLE controls, MFC
- windowless controls, MFC
- windowless controls
- controls [MFC], OLE
- controls [MFC], windowless
- COleControl class
ms.assetid: 53e95299-38e8-447b-9c5f-a381d27f5123
caps.latest.revision: 25
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7ef5621aaf940be3ebe2806971dfc65d06972a5a
ms.lasthandoff: 02/24/2017

---
# <a name="colecontrol-class"></a>COleControl 類別
開發 OLE 控制項的強大基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class COleControl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleControl::COleControl](#colecontrol)|建立 `COleControl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleControl::AmbientAppearance](#ambientappearance)|擷取目前控制項的外觀。|  
|[COleControl::AmbientBackColor](#ambientbackcolor)|傳回環境的背景色彩屬性的值。|  
|[COleControl::AmbientDisplayName](#ambientdisplayname)|傳回指定控制項的名稱，容器。|  
|[COleControl::AmbientFont](#ambientfont)|傳回環境的字型屬性的值。|  
|[COleControl::AmbientForeColor](#ambientforecolor)|傳回環境的前景色彩屬性的值。|  
|[Colecontrol:: Ambientlocaleid](#ambientlocaleid)|傳回容器的地區設定識別碼。|  
|[COleControl::AmbientScaleUnits](#ambientscaleunits)|傳回容器所使用的單位類型。|  
|[COleControl::AmbientShowGrabHandles](#ambientshowgrabhandles)|決定是否應該顯示抓取控點。|  
|[COleControl::AmbientShowHatching](#ambientshowhatching)|決定是否應該顯示影線。|  
|[COleControl::AmbientTextAlign](#ambienttextalign)|傳回容器所指定的文字對齊類型。|  
|[COleControl::AmbientUIDead](#ambientuidead)|決定控制項應該回應使用者介面動作。|  
|[COleControl::AmbientUserMode](#ambientusermode)|決定容器的模式。|  
|[COleControl::BoundPropertyChanged](#boundpropertychanged)|通知容器繫結的屬性已變更。|  
|[COleControl::BoundPropertyRequestEdit](#boundpropertyrequestedit)|若要編輯屬性值要求權限。|  
|[COleControl::ClientToParent](#clienttoparent)|將轉譯的點，相對於控制項的原點的點，相對於其容器的原點。|  
|[COleControl::ClipCaretRect](#clipcaretrect)|如果它由控制項重疊，請調整插入號矩形。|  
|[COleControl::ControlInfoChanged](#controlinfochanged)|由控制項的助憶鍵的集合變更後，請呼叫此函式。|  
|[COleControl::DisplayError](#displayerror)|顯示使用者控制項的內建的錯誤事件。|  
|[COleControl::DoClick](#doclick)|實作的股票`DoClick`方法。|  
|[COleControl::DoPropExchange](#dopropexchange)|序列化的屬性`COleControl`物件。|  
|[COleControl::DoSuperclassPaint](#dosuperclasspaint)|OLE 控制項已子類別化 Windows 控制項來重新繪製。|  
|[COleControl::EnableSimpleFrame](#enablesimpleframe)|啟用控制項的簡單框架支援。|  
|[COleControl::ExchangeExtent](#exchangeextent)|將序列化控制項的寬度和高度。|  
|[COleControl::ExchangeStockProps](#exchangestockprops)|將控制項的內建屬性序列化。|  
|[COleControl::ExchangeVersion](#exchangeversion)|將序列化控制的版本號碼。|  
|[COleControl::FireClick](#fireclick)|股票圖，就會引發`Click`事件。|  
|[COleControl::FireDblClick](#firedblclick)|股票圖，就會引發`DblClick`事件。|  
|[Colecontrol:: Fireerror](#fireerror)|股票圖，就會引發`Error`事件。|  
|[COleControl::FireEvent](#fireevent)|引發自訂事件。|  
|[COleControl::FireKeyDown](#firekeydown)|股票圖，就會引發`KeyDown`事件。|  
|[COleControl::FireKeyPress](#firekeypress)|股票圖，就會引發`KeyPress`事件。|  
|[COleControl::FireKeyUp](#firekeyup)|股票圖，就會引發`KeyUp`事件。|  
|[COleControl::FireMouseDown](#firemousedown)|股票圖，就會引發`MouseDown`事件。|  
|[COleControl::FireMouseMove](#firemousemove)|股票圖，就會引發`MouseMove`事件。|  
|[COleControl::FireMouseUp](#firemouseup)|股票圖，就會引發`MouseUp`事件。|  
|[COleControl::FireReadyStateChange](#firereadystatechange)|引發事件的控制項就緒狀態變更時。|  
|[COleControl::GetActivationPolicy](#getactivationpolicy)|支援的控制項的預設啟動行為會改變`IPointerInactive`介面。|  
|[COleControl::GetAmbientProperty](#getambientproperty)|傳回指定的環境屬性的值。|  
|[COleControl::GetAppearance](#getappearance)|傳回內建的外觀屬性的值。|  
|[COleControl::GetBackColor](#getbackcolor)|傳回內建的背景色彩屬性的值。|  
|[COleControl::GetBorderStyle](#getborderstyle)|傳回內建的框線樣式屬性的值。|  
|[COleControl::GetCapture](#getcapture)|決定是否啟用中，無視窗控制項物件有滑鼠捕捉。|  
|[COleControl::GetClassID](#getclassid)|擷取控制項的 OLE 類別 ID。|  
|[COleControl::GetClientOffset](#getclientoffset)|擷取控制項的矩形區域的左上的角和其工作區的左上的角之間的差異。|  
|[COleControl::GetClientRect](#getclientrect)|擷取控制項的工作區的大小。|  
|[COleControl::GetClientSite](#getclientsite)|查詢的物件，其目前的用戶端站台容器中的指標。|  
|[Clippaintdc](#getcontrolflags)|擷取控制項旗標設定。|  
|[COleControl::GetControlSize](#getcontrolsize)|傳回 OLE 控制項的大小與位置。|  
|[COleControl::GetDC](#getdc)|提供一種來取得其容器的裝置內容的無視窗控制項的方法。|  
|[COleControl::GetEnabled](#getenabled)|會傳回股票 Enabled 屬性的值。|  
|[COleControl::GetExtendedControl](#getextendedcontrol)|擷取屬於容器的擴充的控制項物件的指標。|  
|[COleControl::GetFocus](#getfocus)|判斷控制項是否有焦點。|  
|[COleControl::GetFont](#getfont)|傳回內建字型屬性值。|  
|[COleControl::GetFontTextMetrics](#getfonttextmetrics)|傳回的標準`CFontHolder`物件。|  
|[COleControl::GetForeColor](#getforecolor)|傳回內建的前景色彩屬性的值。|  
|[COleControl::GetHwnd](#gethwnd)|傳回內建的 hWnd 屬性的值。|  
|[COleControl::GetMessageString](#getmessagestring)|提供功能表項目的狀態列文字。|  
|[Colecontrol:: Getnotsupported](#getnotsupported)|將控制項的屬性值，使用者無法存取。|  
|[COleControl::GetReadyState](#getreadystate)|傳回控制項的整備狀態。|  
|[COleControl::GetRectInContainer](#getrectincontainer)|傳回相對於其容器控制項的矩形。|  
|[COleControl::GetStockTextMetrics](#getstocktextmetrics)|傳回度量的內建字型屬性。|  
|[COleControl::GetText](#gettext)|傳回內建的 Text 或 Caption 屬性的值。|  
|[Colecontrol:: Getwindowlessdroptarget](#getwindowlessdroptarget)|覆寫，以允許無視窗控制項的拖放到目標拖放作業。|  
|[COleControl::InitializeIIDs](#initializeiids)|通知控制項將會使用與 Iid 的基底類別。|  
|[COleControl::InternalGetFont](#internalgetfont)|傳回`CFontHolder`物件的內建字型屬性。|  
|[COleControl::InternalGetText](#internalgettext)|擷取內建的標題或文字屬性。|  
|[Colecontrol:: Internalsetreadystate](#internalsetreadystate)|設定控制項的整備狀態並引發已備妥狀態變更事件。|  
|[COleControl::InvalidateControl](#invalidatecontrol)|失效的區域顯示的控制項，使其重新繪製。|  
|[COleControl::InvalidateRgn](#invalidatergn)|使容器視窗的用戶端區域內的指定區域失效。 可用來進行無視窗控制項重繪區域中。|  
|[COleControl::IsConvertingVBX](#isconvertingvbx)|可讓 OLE 控制項的特製化的載入。|  
|[COleControl::IsModified](#ismodified)|判斷是否已變更的控制項狀態。|  
|[Colecontrol:: Isoptimizeddraw](#isoptimizeddraw)|指出容器是否支援目前的繪圖作業最佳化的繪圖。|  
|[COleControl::IsSubclassedControl](#issubclassedcontrol)|呼叫以判斷是否控制項子類別化 Windows 控制項。|  
|[COleControl::Load](#load)|重設任何先前的非同步資料，並啟動新的負載，控制項的非同步屬性。|  
|[COleControl::LockInPlaceActive](#lockinplaceactive)|決定是否控制項可以停用的容器。|  
|[COleControl::OnAmbientPropertyChange](#onambientpropertychange)|變更環境的屬性時呼叫。|  
|[COleControl::OnAppearanceChanged](#onappearancechanged)|變更內建的外觀屬性時呼叫。|  
|[COleControl::OnBackColorChanged](#onbackcolorchanged)|內建 BackColor 屬性變更時呼叫。|  
|[COleControl::OnBorderStyleChanged](#onborderstylechanged)|變更內建的框線樣式屬性時呼叫。|  
|[COleControl::OnClick](#onclick)|呼叫以引發內建 Click 事件。|  
|[COleControl::OnClose](#onclose)|通知控制項，`IOleControl::Close`被呼叫。|  
|[COleControl::OnDoVerb](#ondoverb)|執行控制動詞後呼叫。|  
|[COleControl::OnDraw](#ondraw)|當控制項被要求重繪其本身時呼叫。|  
|[Colecontrol:: Ondrawmetafile](#ondrawmetafile)|容器控制項重繪本身使用中繼檔裝置內容要求時呼叫。|  
|[COleControl::OnEdit](#onedit)|若要啟用的 UI 容器 OLE 控制項呼叫。|  
|[COleControl::OnEnabledChanged](#onenabledchanged)|股票圖 Enabled 屬性已變更時呼叫。|  
|[COleControl::OnEnumVerbs](#onenumverbs)|列舉控制動詞容器呼叫。|  
|[COleControl::OnEventAdvise](#oneventadvise)|連接或中斷連線的控制項事件處理常式時呼叫。|  
|[COleControl::OnFontChanged](#onfontchanged)|變更內建字型屬性時呼叫。|  
|[COleControl::OnForeColorChanged](#onforecolorchanged)|變更內建的前景色彩屬性時呼叫。|  
|[COleControl::OnFreezeEvents](#onfreezeevents)|凍結或解除凍結但控制項的事件時呼叫。|  
|[COleControl::OnGetColorSet](#ongetcolorset)|通知控制項，`IOleObject::GetColorSet`被呼叫。|  
|[COleControl::OnGetControlInfo](#ongetcontrolinfo)|提供容器的助憶鍵資訊。|  
|[COleControl::OnGetDisplayString](#ongetdisplaystring)|呼叫以取得一個字串，代表屬性值。|  
|[COleControl::OnGetInPlaceMenu](#ongetinplacemenu)|要求會合併與 [容器] 功能表的控制項的功能表中的控制代碼。|  
|[COleControl::OnGetNaturalExtent](#ongetnaturalextent)|覆寫，以擷取建議的大小和範圍模式最接近的控制項的顯示大小。|  
|[COleControl::OnGetPredefinedStrings](#ongetpredefinedstrings)|傳回代表屬性的可能值的字串。|  
|[COleControl::OnGetPredefinedValue](#ongetpredefinedvalue)|傳回對應至預先定義的字串值。|  
|[COleControl::OnGetViewExtent](#ongetviewextent)|覆寫，以擷取 （可以用來啟用兩次繪圖） 控制項的顯示區域的大小。|  
|[COleControl::OnGetViewRect](#ongetviewrect)|覆寫，以將控制項的大小轉換成特定的位置開始的矩形。|  
|[COleControl::OnGetViewStatus](#ongetviewstatus)|覆寫，以擷取控制項的檢視狀態。|  
|[COleControl::OnHideToolBars](#onhidetoolbars)|容器控制項的 UI 停用時呼叫。|  
|[COleControl::OnInactiveMouseMove](#oninactivemousemove)|將滑鼠指標分派在非作用中的控制項容器的覆寫`WM_MOUSEMOVE`訊息至控制項。|  
|[COleControl::OnInactiveSetCursor](#oninactivesetcursor)|將滑鼠指標分派在非作用中的控制項容器的覆寫`WM_SETCURSOR`訊息至控制項。|  
|[COleControl::OnKeyDownEvent](#onkeydownevent)|內建的 KeyDown 事件已經引發後呼叫。|  
|[COleControl::OnKeyPressEvent](#onkeypressevent)|內建 KeyPress 事件已經引發後呼叫。|  
|[COleControl::OnKeyUpEvent](#onkeyupevent)|內建的 KeyUp 事件已經引發後呼叫。|  
|[COleControl::OnMapPropertyToPage](#onmappropertytopage)|表示用來編輯屬性的屬性頁。|  
|[COleControl::OnMnemonic](#onmnemonic)|已按下控制項的助憶鍵時呼叫。|  
|[COleControl::OnProperties](#onproperties)|已叫用控制項的 「 屬性 」 動詞命令時呼叫。|  
|[COleControl::OnQueryHitPoint](#onqueryhitpoint)|控制項的顯示與指定的點是否覆寫查詢。|  
|[COleControl::OnQueryHitRect](#onqueryhitrect)|控制項的顯示重疊在指定的矩形中的任何時間點是否覆寫查詢。|  
|[COleControl::OnRenderData](#onrenderdata)|擷取指定之格式的資料架構所呼叫。|  
|[COleControl::OnRenderFileData](#onrenderfiledata)|擷取指定之格式的檔案中的資料架構所呼叫。|  
|[COleControl::OnRenderGlobalData](#onrenderglobaldata)|從指定的格式中的全域記憶體擷取資料的架構所呼叫。|  
|[COleControl::OnResetState](#onresetstate)|將控制項的屬性重設為預設值。|  
|[Colecontrol:: Onsetclientsite](#onsetclientsite)|通知控制項，`IOleControl::SetClientSite`被呼叫。|  
|[COleControl::OnSetData](#onsetdata)|取代控制項的資料與另一個值。|  
|[COleControl::OnSetExtent](#onsetextent)|控制項的寬度變更後呼叫。|  
|[COleControl::OnSetObjectRects](#onsetobjectrects)|控制項的維度已變更之後呼叫。|  
|[COleControl::OnShowToolBars](#onshowtoolbars)|當控制項已經 UI 啟動時呼叫。|  
|[COleControl::OnTextChanged](#ontextchanged)|股票圖 Text 或 Caption 屬性變更時呼叫。|  
|[COleControl::OnWindowlessMessage](#onwindowlessmessage)|無視窗控制項的處理 （除了滑鼠和鍵盤訊息） 的視窗訊息。|  
|[COleControl::ParentToClient](#parenttoclient)|將轉譯的點，相對於容器的原點的點，相對於控制項的原點。|  
|[COleControl::PostModalDialog](#postmodaldialog)|告知容器已關閉強制回應對話方塊。|  
|[COleControl::PreModalDialog](#premodaldialog)|通知即將顯示強制回應對話方塊的容器。|  
|[COleControl::RecreateControlWindow](#recreatecontrolwindow)|終結並重新建立控制項的視窗。|  
|[COleControl::Refresh](#refresh)|強制重新繪製的控制項的外觀。|  
|[COleControl::ReleaseCapture](#releasecapture)|釋放滑鼠捕捉。|  
|[COleControl::ReleaseDC](#releasedc)|釋放容器將無視窗控制項的顯示裝置內容。|  
|[COleControl::ReparentControlWindow](#reparentcontrolwindow)|重設控制項視窗的父代。|  
|[COleControl::ResetStockProps](#resetstockprops)|初始化`COleControl`內建屬性設為預設值。|  
|[COleControl::ResetVersion](#resetversion)|初始化為特定值的版本號碼。|  
|[COleControl::ScrollWindow](#scrollwindow)|允許無視窗控制項來捲動區域內顯示其就地使用中映像。|  
|[COleControl::SelectFontObject](#selectfontobject)|放入裝置內容中選取自訂的字型屬性。|  
|[COleControl::SelectStockFont](#selectstockfont)|選取放入裝置內容中的內建字型屬性。|  
|[COleControl::SerializeExtent](#serializeextent)|序列化或初始化控制項的顯示空間。|  
|[COleControl::SerializeStockProps](#serializestockprops)|序列化或初始化`COleControl`內建屬性。|  
|[COleControl::SerializeVersion](#serializeversion)|序列化或初始化控制項的版本資訊。|  
|[COleControl::SetAppearance](#setappearance)|設定內建的外觀屬性的值。|  
|[COleControl::SetBackColor](#setbackcolor)|設定內建的背景色彩屬性的值。|  
|[COleControl::SetBorderStyle](#setborderstyle)|設定內建的框線樣式屬性的值。|  
|[COleControl::SetCapture](#setcapture)|會使控制項的容器視窗才能代替控制項的滑鼠捕捉的所有權。|  
|[COleControl::SetControlSize](#setcontrolsize)|設定位置與 OLE 控制項的大小。|  
|[COleControl::SetEnabled](#setenabled)|設定內建 Enabled 屬性值。|  
|[COleControl::SetFocus](#setfocus)|會使控制項的容器視窗，才能擁有輸入焦點的控制項的代表。|  
|[COleControl::SetFont](#setfont)|設定內建字型屬性值。|  
|[COleControl::SetForeColor](#setforecolor)|設定內建的前景色彩屬性的值。|  
|[COleControl::SetInitialSize](#setinitialsize)|設定 OLE 控制項容器中第一次顯示時的大小。|  
|[COleControl::SetModifiedFlag](#setmodifiedflag)|變更控制項的已修改的狀態。|  
|[Colecontrol:: Setnotpermitted](#setnotpermitted)|表示編輯要求已失敗。|  
|[Colecontrol:: Setnotsupported](#setnotsupported)|防止使用者控制項的屬性值的修改。|  
|[COleControl::SetRectInContainer](#setrectincontainer)|設定控制項的矩形相對於其容器。|  
|[COleControl::SetText](#settext)|設定內建的 Text 或 Caption 屬性值。|  
|[Colecontrol:: Throwerror](#throwerror)|OLE 控制項中發生錯誤時，發出訊號。|  
|[COleControl::TransformCoords](#transformcoords)|轉換座標容器和控制項之間的值。|  
|[COleControl::TranslateColor](#translatecolor)|將轉換**OLE_COLOR**值**COLORREF**值。|  
|[COleControl::WillAmbientsBeValidDuringLoad](#willambientsbevalidduringload)|決定是否環境屬性可以使用下一次載入控制項。|  
|[COleControl::WindowProc](#windowproc)|提供的 Windows 處理程序`COleControl`物件。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleControl::DrawContent](#drawcontent)|當控制項的外觀需要更新時，由架構呼叫。|  
|[COleControl::DrawMetafile](#drawmetafile)|使用中繼檔裝置內容時，由架構呼叫。|  
|[COleControl::IsInvokeAllowed](#isinvokeallowed)|可讓自動化方法引動過程。|  
|[COleControl::SetInitialDataFormats](#setinitialdataformats)|初始化控制項支援的資料格式的清單架構呼叫。|  
  
## <a name="remarks"></a>備註  
 衍生自`CWnd`，此類別會繼承 Windows 視窗物件的所有功能以及特定至 OLE，例如事件引發以及支援方法和屬性的其他功能。  
  
 OLE 控制項可以插入 OLE 容器應用程式，並使用引發事件和公開方法與屬性，以容器的雙向系統與容器通訊。 請注意，標準的 OLE 容器只支援 OLE 控制項的基本功能。 它們是不支援 OLE 控制項的擴充的功能。 引發事件發生於事件傳送至的容器控制項中發生特定動作的結果。 接著，容器與其通訊的控制項使用的方法和屬性的成員函式類似公開的集和 c + + 類別的資料成員。 這個方法可讓開發人員控制控制項的外觀，並告知容器，當發生特定的動作。  
  
## <a name="windowless-controls"></a>無視窗控制項  
 OLE 控制項可以使用的就地啟用作用中沒有視窗。 無視窗控制項有很大的好處︰  
  
-   無視窗控制項可以透明及非矩形  
  
-   無視窗控制項減少之物件的執行個體大小和建立時間  
  
 控制項不需要的視窗。 透過單一共用的視窗 （通常是容器的） 和分派的程式碼可以輕鬆地提供視窗所提供服務。 視窗是大部分不需要複雜的物件上。  
  
 使用無視窗啟用時，容器 （具有視窗） 會負責提供服務，會提供控制項自己的視窗。 例如，如果您的控制項需要查詢鍵盤焦點，或查詢滑鼠捕捉，取得裝置內容，這些作業是由容器管理。 `COleControl`[無視窗作業的成員函式](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df)叫用這些容器上的作業。  
  
 啟用無視窗啟用之後，容器委派輸入訊息到控制項的`IOleInPlaceObjectWindowless`介面 (副檔名為[IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646)支援無視窗)。 `COleControl`適當調整滑鼠座標之後，這個介面的實作會分派透過您控制項的訊息對應，這些訊息。 您可以將對應的項目加入至訊息對應處理一般視窗訊息，這些訊息。  
  
 在無視窗控制項中，您應該一律使用`COleControl`成員函式，而不要使用對應`CWnd`成員函式或其相關的 Windows API 函式。  
  
 只有當它們變成作用中，但會為非作用中現用轉換所需的工作量，而且轉換速度中斷時，OLE 控制項物件也可以建立視窗。 這問題時，有一些情況︰ 做為範例，請考慮在文字方塊中的方格。 當向上或向下的對照指標透過資料行，每個控制項必須是就地啟動，然後停用。 非作用中/主動轉換的速度會直接影響捲動的速度。  
  
 如需有關如何開發 OLE 控制項架構的詳細資訊，請參閱文章[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)和[概觀︰ 建立 MFC ActiveX 控制項程式](../../mfc/reference/mfc-activex-control-wizard.md)。 如需最佳化 OLE 控制項，包括無視窗和閃爍的控制項，請參閱[MFC ActiveX 控制項︰ 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `COleControl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxctl.h  
  
##  <a name="a-nameambientbackcolora--colecontrolambientbackcolor"></a><a name="ambientbackcolor"></a>COleControl::AmbientBackColor  
 傳回環境的背景色彩屬性的值。  
  
```  
OLE_COLOR AmbientBackColor();
```  
  
### <a name="return-value"></a>傳回值  
 容器的環境背景色彩屬性，如果有任何目前的值。 如果不支援屬性，此函數會傳回系統定義的 Windows 背景色彩。  
  
### <a name="remarks"></a>備註  
 環境的背景色彩屬性使用的所有控制項，由容器所定義。 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientdisplaynamea--colecontrolambientdisplayname"></a><a name="ambientdisplayname"></a>COleControl::AmbientDisplayName  
 對使用者顯示錯誤訊息中可用的容器已指派給控制項的名稱。  
  
```  
CString AmbientDisplayName();
```  
  
### <a name="return-value"></a>傳回值  
 OLE 控制項的名稱。 預設值為零長度字串。  
  
### <a name="remarks"></a>備註  
 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientfonta--colecontrolambientfont"></a><a name="ambientfont"></a>COleControl::AmbientFont  
 傳回環境的字型屬性的值。  
  
```  
LPFONTDISP AmbientFont();
```  
  
### <a name="return-value"></a>傳回值  
 容器的環境字型分派介面的指標。 預設值是**NULL**。 如果傳回值不等於**NULL**，您必須負責釋放字型藉由呼叫其[Iunknown](http://msdn.microsoft.com/library/windows/desktop/ms682317)成員函式。  
  
### <a name="remarks"></a>備註  
 環境字型屬性是由容器定義，並可供所有控制項。請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientforecolora--colecontrolambientforecolor"></a><a name="ambientforecolor"></a>COleControl::AmbientForeColor  
 傳回環境的前景色彩屬性的值。  
  
```  
OLE_COLOR AmbientForeColor();
```  
  
### <a name="return-value"></a>傳回值  
 容器的環境前景色彩屬性，如果有任何目前的值。 如果不支援，此函數會傳回 Windows 系統定義的文字色彩。  
  
### <a name="remarks"></a>備註  
 環境的前景色彩屬性使用的所有控制項，由容器所定義。 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientlocaleida--colecontrolambientlocaleid"></a><a name="ambientlocaleid"></a>Colecontrol:: Ambientlocaleid  
 傳回容器的地區設定識別碼。  
  
```  
LCID AmbientLocaleID();
```  
  
### <a name="return-value"></a>傳回值  
 容器的地區設定識別碼屬性 （如果有的話） 的值。 如果不支援這個屬性，此函數會傳回 0。  
  
### <a name="remarks"></a>備註  
 控制項可以使用地區設定識別碼，來調整它的特定地區設定的使用者介面。 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientappearancea--colecontrolambientappearance"></a><a name="ambientappearance"></a>COleControl::AmbientAppearance  
 擷取控制項物件目前的外觀設定。  
  
```  
short AmbientAppearance();
```  
  
### <a name="return-value"></a>傳回值  
 控制項的外觀︰  
  
- **0**一般外觀  
  
- **1** 3D 外觀  
  
### <a name="remarks"></a>備註  
 呼叫此函式來擷取目前的值**DISPID_AMBIENT_APPEARANCE**控制項的屬性。  
  
##  <a name="a-nameambientscaleunitsa--colecontrolambientscaleunits"></a><a name="ambientscaleunits"></a>COleControl::AmbientScaleUnits  
 傳回容器所使用的單位類型。  
  
```  
CString AmbientScaleUnits();
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含容器的環境的 ScaleUnits。 如果不支援這個屬性，此函數會傳回零長度字串。  
  
### <a name="remarks"></a>備註  
 容器的環境 ScaleUnits 屬性可以用來顯示位置或維度，標示為與所選的單位，例如二分之一或公分為單位。 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientshowgrabhandlesa--colecontrolambientshowgrabhandles"></a><a name="ambientshowgrabhandles"></a>COleControl::AmbientShowGrabHandles  
 判斷容器是否允許控制項本身使用時顯示抓取控點。  
  
```  
BOOL AmbientShowGrabHandles();
```  
  
### <a name="return-value"></a>傳回值  
 抓取控點應該會顯示; 如果為非零否則為 0。 如果不支援這個屬性，此函式會傳回非零值。  
  
### <a name="remarks"></a>備註  
 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientshowhatchinga--colecontrolambientshowhatching"></a><a name="ambientshowhatching"></a>COleControl::AmbientShowHatching  
 判斷容器是否允許控制項來顯示本身與規劃模式 UI 作用。  
  
```  
BOOL AmbientShowHatching();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果應該顯示影線的圖樣。否則為 0。 如果不支援這個屬性，此函式會傳回非零值。  
  
### <a name="remarks"></a>備註  
 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambienttextaligna--colecontrolambienttextalign"></a><a name="ambienttextalign"></a>COleControl::AmbientTextAlign  
 判斷慣用的控制項容器的環境的文字對齊方式。  
  
```  
short AmbientTextAlign();
```  
  
### <a name="return-value"></a>傳回值  
 容器的環境的文字對齊屬性的狀態。 如果不支援這個屬性，此函數會傳回 0。  
  
 以下是有效的傳回值的清單︰  
  
|傳回值|意義|  
|------------------|-------------|  
|0|一般的對齊方式 （靠右文字左邊的數字）。|  
|1|靠左對齊|  
|2|置中|  
|3|靠右對齊|  
  
### <a name="remarks"></a>備註  
 這個屬性可用於所有內嵌控制項，而且由容器所定義。 請注意，容器不需要可支援此屬性。  
  
##  <a name="a-nameambientuideada--colecontrolambientuidead"></a><a name="ambientuidead"></a>COleControl::AmbientUIDead  
 判斷容器是否要回應使用者介面動作的控制項。  
  
```  
BOOL AmbientUIDead();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果控制項應回應使用者介面動作;否則為 0。 如果不支援這個屬性，此函數會傳回 0。  
  
### <a name="remarks"></a>備註  
 例如，容器可能設為**TRUE**在設計模式。  
  
##  <a name="a-nameambientusermodea--colecontrolambientusermode"></a><a name="ambientusermode"></a>COleControl::AmbientUserMode  
 決定是否在設計模式或使用者模式中的容器。  
  
```  
BOOL AmbientUserMode();
```  
  
### <a name="return-value"></a>傳回值  
 如果容器是使用者模式中，為非零否則為 0 （位於設計模式）。 如果不支援這個屬性，此函數會傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 例如，容器可能設為**FALSE**在設計模式。  
  
##  <a name="a-nameboundpropertychangeda--colecontrolboundpropertychanged"></a><a name="boundpropertychanged"></a>COleControl::BoundPropertyChanged  
 繫結的屬性值變更時，發出訊號。  
  
```  
void BoundPropertyChanged(DISPID dispid);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 繫結控制項屬性的分派 ID。  
  
### <a name="remarks"></a>備註  
 這必須在每次屬性變更，即使在不透過屬性進行變更的情況下的值設定方法呼叫。 請特別注意的繫結會對應至成員變數的屬性。 這類成員變數的變更，每當`BoundPropertyChanged`必須呼叫。  
  
##  <a name="a-nameboundpropertyrequestedita--colecontrolboundpropertyrequestedit"></a><a name="boundpropertyrequestedit"></a>COleControl::BoundPropertyRequestEdit  
 要求權限從`IPropertyNotifySink`介面來變更控制項所提供的繫結的屬性值。  
  
```  
BOOL BoundPropertyRequestEdit(DISPID dispid);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 繫結控制項屬性的分派 ID。  
  
### <a name="return-value"></a>傳回值  
 非零，如果允許變更。否則為 0。 預設值為非零值。  
  
### <a name="remarks"></a>備註  
 如果權限遭到拒絕，控制項必須禁止屬性變更的值。 這可以經由略過或失敗的動作，嘗試變更屬性值。  
  
##  <a name="a-nameclienttoparenta--colecontrolclienttoparent"></a><a name="clienttoparent"></a>COleControl::ClientToParent  
 將轉譯的座標`pPoint`為父座標。  
  
```  
virtual void ClientToParent(
    LPCRECT lprcBounds, 
    LPPOINT pPoint) const;  
```  
  
### <a name="parameters"></a>參數  
 `lprcBounds`  
 OLE 控制項容器中的界限的指標。 非工作區，但整個控制項包括框線和捲軸的區域。  
  
 `pPoint`  
 要轉譯為父系 （容器） 的座標的 OLE 用戶端區域點的指標。  
  
### <a name="remarks"></a>備註  
 在輸入`pPoint`相對於來源的 OLE 控制項 （左上角之控制項的工作區） 的工作區。 在輸出`pPoint`相對於父系 （左上角的容器） 的原點。  
  
##  <a name="a-nameclipcaretrecta--colecontrolclipcaretrect"></a><a name="clipcaretrect"></a>COleControl::ClipCaretRect  
 如果它完全或部分所涵蓋的重疊、 不透明的物件，請調整插入號矩形。  
  
```  
BOOL ClipCaretRect(LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 在輸入變數的指標， [RECT](../../mfc/reference/rect-structure1.md)包含插入號區域調整的結構。 在輸出時，已調整的游標 區域中，或**NULL**如果插入號矩形完全涵蓋。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 插入號是閃爍的線條、 區塊或點陣圖，通常表示，將會插入文字或圖形。  
  
 無視窗物件無法安全地顯示插入號，而不先檢查是否有插入號部分或全部隱藏重疊物件。 為了達到這個境界，物件可以使用`ClipCaretRect`取得調整插入號 （精簡） 以確保它符合的裁剪區域。  
  
 建立插入號的物件應該提交的插入號矩形`ClipCaretRect`插入號以用於調整的矩形。 如果將會完全隱藏插入號，這個方法會傳回**FALSE**和插入號不應該顯示在此情況下。  
  
##  <a name="a-namecolecontrola--colecontrolcolecontrol"></a><a name="colecontrol"></a>COleControl::COleControl  
 建構 `COleControl` 物件。  
  
```  
COleControl();
```  
  
### <a name="remarks"></a>備註  
 通常不會直接呼叫此函式。 而是 OLE 控制項通常會建立其類別處理站。  
  
##  <a name="a-namecontrolinfochangeda--colecontrolcontrolinfochanged"></a><a name="controlinfochanged"></a>COleControl::ControlInfoChanged  
 支援的控制項的助憶鍵的集合變更時呼叫此函式。  
  
```  
void ControlInfoChanged();
```  
  
### <a name="remarks"></a>備註  
 在收到此通知時，控制項的容器會取得一組新的助憶鍵藉由呼叫[IOleControl::GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730)。 請注意，容器並不需要回應此通知。  
  
##  <a name="a-namedisplayerrora--colecontroldisplayerror"></a><a name="displayerror"></a>COleControl::DisplayError  
 （除非事件處理常式已抑制顯示的錯誤），內建的錯誤事件已處理之後，由架構呼叫。  
  
```  
virtual void DisplayError(
    SCODE scode,  
    LPCTSTR lpszDescription,  
    LPCTSTR lpszSource,  
    LPCTSTR lpszHelpFile,  
    UINT nHelpID);
```  
  
### <a name="parameters"></a>參數  
 *scode*  
 要報告的狀態碼值。 如需可能的程式碼的完整清單，請參閱文章[ActiveX 控制項︰ 進階主題](../../mfc/mfc-activex-controls-advanced-topics.md)。  
  
 `lpszDescription`  
 報告錯誤的描述。  
  
 *lpszSource*  
 產生錯誤 （通常 OLE 控制項模組的名稱） 的模組名稱。  
  
 `lpszHelpFile`  
 包含描述錯誤的說明檔的名稱。  
  
 `nHelpID`  
 說明內容識別碼所報告的錯誤。  
  
### <a name="remarks"></a>備註  
 預設行為的描述中包含錯誤的訊息方塊顯示`lpszDescription`。  
  
 覆寫這個函式來自訂顯示錯誤的方式。  
  
##  <a name="a-namedoclicka--colecontroldoclick"></a><a name="doclick"></a>COleControl::DoClick  
 模擬滑鼠按一下控制項上的動作。  
  
```  
void DoClick();
```  
  
### <a name="remarks"></a>備註  
 可覆寫`COleControl::OnClick`會呼叫成員函式，以及內建 Click 事件引發之後，如果控制項支援。  
  
 此函式支援`COleControl`做為內建的方法，稱為 DoClick 基底類別。 如需詳細資訊，請參閱文章[ActiveX 控制項︰ 方法](../../mfc/mfc-activex-controls-methods.md)。  
  
##  <a name="a-namedopropexchangea--colecontroldopropexchange"></a><a name="dopropexchange"></a>COleControl::DoPropExchange  
 載入或儲存永續性儲存體表示法，例如資料流或屬性集的控制項時，架構呼叫。  
  
```  
virtual void DoPropExchange(CPropExchange* pPX);
```  
  
### <a name="parameters"></a>參數  
 `pPX`  
 指標`CPropExchange`物件。 架構會提供此物件來建立交換的內容屬性，包括其方向。  
  
### <a name="remarks"></a>備註  
 此函式通常會呼叫**PX_**系列的函式來載入或儲存的 OLE 控制項的特定使用者定義屬性。  
  
 如果控制項精靈 」 來建立 OLE 控制項的專案，此函式的覆寫的版本將會序列化所支援的內建屬性`COleControl`基底類別函式呼叫`COleControl::DoPropExchange`。 當您新增至您的 OLE 控制項的使用者定義的屬性，您必須修改此函式以序列化您的新屬性。 如需序列化的詳細資訊，請參閱文章[ActiveX 控制項︰ 序列化](../../mfc/mfc-activex-controls-serializing.md)。  
  
##  <a name="a-namedosuperclasspainta--colecontroldosuperclasspaint"></a><a name="dosuperclasspaint"></a>COleControl::DoSuperclassPaint  
 OLE 控制項已子類別化 Windows 控制項來重新繪製。  
  
```  
void DoSuperclassPaint(
    CDC* pDC,  
    const CRect& rcBounds);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 控制項容器的裝置內容的指標。  
  
 `rcBounds`  
 控制項可繪製區域。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可正確處理非使用中的 OLE 控制項的繪製。 此函式應該只用於如果 OLE 控制項子類別化 Windows 控制項，而且應該會呼叫`OnDraw`函式的控制項。  
  
 如需有關這個函式和子類別化 Windows 控制項的詳細資訊，請參閱文章[ActiveX 控制項︰ 子類別化 Windows 控制項](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
##  <a name="a-namedrawcontenta--colecontroldrawcontent"></a><a name="drawcontent"></a>COleControl::DrawContent  
 當控制項的外觀需要更新時，由架構呼叫。  
  
```  
void DrawContent(
    CDC* pDC,  
    CRect& rc);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容指標。  
  
 `rc`  
 在中繪製的矩形區域。  
  
### <a name="remarks"></a>備註  
 此函式直接呼叫可覆寫`OnDraw`函式。  
  
##  <a name="a-namedrawmetafilea--colecontroldrawmetafile"></a><a name="drawmetafile"></a>COleControl::DrawMetafile  
 使用中繼檔裝置內容時，由架構呼叫。  
  
```  
void DrawMetafile(
    CDC* pDC,  
    CRect& rc);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 中繼檔裝置內容指標。  
  
 `rc`  
 在中繪製的矩形區域。  
  
##  <a name="a-nameenablesimpleframea--colecontrolenablesimpleframe"></a><a name="enablesimpleframe"></a>COleControl::EnableSimpleFrame  
 可讓 OLE 控制項的簡單框架特性。  
  
```  
void EnableSimpleFrame();
```  
  
### <a name="remarks"></a>備註  
 這項特性可讓控制項以支援其他控制項的視覺內含項目，但不是正確的 OLE 內含項目。 範例會使用數個控制項內的群組方塊。 這些控制項不是 OLE 所包含，但它們位於相同的群組方塊。  
  
##  <a name="a-nameexchangeextenta--colecontrolexchangeextent"></a><a name="exchangeextent"></a>COleControl::ExchangeExtent  
 序列化或初始化的控制項範圍的狀態 (在其維度**HIMETRIC**單位)。  
  
```  
BOOL ExchangeExtent(CPropExchange* pPX);
```  
  
### <a name="parameters"></a>參數  
 `pPX`  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件。 架構會提供此物件來建立交換的內容屬性，包括其方向。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式通常會呼叫的預設實作`COleControl::DoPropExchange`。  
  
##  <a name="a-nameexchangestockpropsa--colecontrolexchangestockprops"></a><a name="exchangestockprops"></a>COleControl::ExchangeStockProps  
 序列化或初始化控制項的內建屬性的狀態。  
  
```  
void ExchangeStockProps(CPropExchange* pPX);
```  
  
### <a name="parameters"></a>參數  
 `pPX`  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件。 架構會提供此物件來建立交換的內容屬性，包括其方向。  
  
### <a name="remarks"></a>備註  
 此函式通常會呼叫的預設實作`COleControl::DoPropExchange`。  
  
##  <a name="a-nameexchangeversiona--colecontrolexchangeversion"></a><a name="exchangeversion"></a>COleControl::ExchangeVersion  
 序列化或初始化控制項的版本資訊的狀態。  
  
```  
BOOL ExchangeVersion(
    CPropExchange* pPX,  
    DWORD dwVersionDefault,  
    BOOL bConvert = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pPX`  
 指標`CPropExchange`物件。 架構會提供此物件來建立交換的內容屬性，包括其方向。  
  
 `dwVersionDefault`  
 控制項的目前版本號碼。  
  
 `bConvert`  
 表示持續性資料是否應該轉換成最新的格式儲存，或保留在相同的格式載入時。  
  
### <a name="return-value"></a>傳回值  
 函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 一般來說，這會是第一個函數呼叫的控制項的覆寫`COleControl::DoPropExchange`。 載入時，此函式讀取永續性資料的版本號碼，並設定的版本屬性[CPropExchange](../../mfc/reference/cpropexchange-class.md)據此物件。 在儲存時，此函數會寫入持續性資料的版本號碼。  
  
 如需持續性和版本控制的詳細資訊，請參閱文章[ActiveX 控制項︰ 序列化](../../mfc/mfc-activex-controls-serializing.md)。  
  
##  <a name="a-namefireclicka--colecontrolfireclick"></a><a name="fireclick"></a>COleControl::FireClick  
 作用中的控制項上按一下滑鼠時，由架構呼叫。  
  
```  
void FireClick();
```  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 自動引發 Click 事件發生，控制項的事件對應必須有內建 Click 事件定義。  
  
##  <a name="a-namefiredblclicka--colecontrolfiredblclick"></a><a name="firedblclick"></a>COleControl::FireDblClick  
 當使用中的控制項上按兩下滑鼠時，由架構呼叫。  
  
```  
void FireDblClick();
```  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 DblClick 事件發生的自動引發，控制項的事件對應必須有定義的內建 DblClick 事件。  
  
##  <a name="a-namefireerrora--colecontrolfireerror"></a><a name="fireerror"></a>Colecontrol:: Fireerror  
 內建的錯誤事件，就會引發。  
  
```  
void FireError(
    SCODE scode,  
    LPCTSTR lpszDescription,  
    UINT nHelpID = 0);
```  
  
### <a name="parameters"></a>參數  
 *scode*  
 要報告的狀態碼值。 如需可能的程式碼的完整清單，請參閱文章[ActiveX 控制項︰ 進階主題](../../mfc/mfc-activex-controls-advanced-topics.md)。  
  
 `lpszDescription`  
 報告錯誤的描述。  
  
 `nHelpID`  
 所報告的錯誤說明 ID。  
  
### <a name="remarks"></a>備註  
 這個事件會提供一種發出訊號，會在 您的程式碼中的適當位置，在控制項中發生錯誤。 不同於其他內建事件，例如 Click 或 MouseMove 架構永遠不會引發錯誤。  
  
 若要報告屬性 get 函式、 屬性集函式或 automation 方法期間發生的錯誤，請呼叫[colecontrol:: Throwerror](#throwerror)。  
  
 實作 OLE 控制項的內建錯誤事件使用`SCODE`值。 如果您的控制項使用這個事件，而且適用於 Visual Basic 4.0 中，您會收到錯誤，因為`SCODE`在 Visual Basic 中不支援值。  
  
 若要修正此問題，以手動方式變更`SCODE`中控制項的參數。ODL 檔案**長**。 此外，任何自訂事件、 方法或屬性，會使用`SCODE`參數也會導致相同的問題。  
  
##  <a name="a-namefireeventa--colecontrolfireevent"></a><a name="fireevent"></a>COleControl::FireEvent  
 使用者定義的事件，從您的控制項與任意數目的選擇性引數，就會引發。  
  
```  
void AFX_CDECL FireEvent(
    DISPID dispid,  
    BYTE* pbParams,  
 ...);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 引發事件的分派 ID。  
  
 `pbParams`  
 事件的參數型別描述項。  
  
### <a name="remarks"></a>備註  
 通常這個函式應該不直接呼叫。 而是您會呼叫事件引發函式位於您的控制項類別宣告事件對應部分。  
  
 `pbParams`引數是以空格分隔的清單**VTS_**。 其中的一或多個值 (以空格分隔，而非逗號) 會指定函式的參數清單。 可能的值如下：  
  
|符號|參數類型|  
|------------|--------------------|  
|**VTS_COLOR**|**OLE_COLOR**|  
|**VTS_FONT**|**IFontDisp\***|  
|**VTS_HANDLE**|`HWND`|  
|**VTS_PICTURE**|**IPictureDisp\***|  
|**VTS_OPTEXCLUSIVE**|**OLE_OPTEXCLUSIVE\***|  
|**VTS_TRISTATE**|**OLE_TRISTATE**|  
|**VTS_XPOS_HIMETRIC**|**OLE_XPOS_HIMETRIC**|  
|**VTS_YPOS_HIMETRIC**|**OLE_YPOS_HIMETRIC**|  
|**VTS_XPOS_PIXELS**|**OLE_XPOS_PIXELS**|  
|**VTS_YPOS_PIXELS**|**OLE_YPOS_PIXELS**|  
|**VTS_XSIZE_PIXELS**|**OLE_XSIZE_PIXELS**|  
|**VTS_YSIZE_PIXELS**|**OLE_XSIZE_PIXELS**|  
|**VTS_XSIZE_HIMETRIC**|**OLE_XSIZE_HIMETRIC**|  
|**VTS_YSIZE_HIMETRIC**|**OLE_XSIZE_HIMETRIC**|  
  
> [!NOTE]
>  所有的 variant 型別已定義其他的 variant 常數的**VTS_FONT**和**VTS_PICTURE**，可提供變異資料常數的指標。 這些常數會使用名為**VTS_P** `constantname`慣例。 例如， **VTS_PCOLOR**是指向**VTS_COLOR**常數。  
  
##  <a name="a-namefirekeydowna--colecontrolfirekeydown"></a><a name="firekeydown"></a>COleControl::FireKeyDown  
 控制項的 UI 使用中時按下按鍵時呼叫架構。  
  
```  
void FireKeyDown(
    USHORT* pnChar,  
    short nShiftState);
```  
  
### <a name="parameters"></a>參數  
 `pnChar`  
 已按下的機碼的虛擬按鍵碼值的指標。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.  
  
 `nShiftState`  
 包含下列旗標的組合︰  
  
- **SHIFT_MASK**動作期間按下 SHIFT 鍵。  
  
- **CTRL_MASK**動作期間按下 CTRL 鍵。  
  
- **ALT_MASK**動作期間按下 ALT 鍵。  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 KeyDown 事件發生的自動引發，控制項的事件對應必須有定義的內建 KeyDown 事件。  
  
##  <a name="a-namefirekeypressa--colecontrolfirekeypress"></a><a name="firekeypress"></a>COleControl::FireKeyPress  
 當按下並放開自訂控制項處於使用中的 UI 容器內的索引鍵時，由架構呼叫。  
  
```  
void FireKeyPress(USHORT* pnChar);
```  
  
### <a name="parameters"></a>參數  
 `pnChar`  
 按下按鍵的字元值的指標。  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 事件的收件者可能會修改`pnChar`，例如，將所有小寫字元轉換成大寫。 如果您想要檢查已修改的字元，會覆寫`OnKeyPressEvent`。  
  
 自動引發 KeyPress 事件發生，控制項的事件對應必須有定義的內建 KeyPress 事件。  
  
##  <a name="a-namefirekeyupa--colecontrolfirekeyup"></a><a name="firekeyup"></a>COleControl::FireKeyUp  
 自訂控制項容器內處於作用中的 UI，且釋放按鍵時呼叫架構。  
  
```  
void FireKeyUp(
    USHORT* pnChar,  
    short nShiftState);
```  
  
### <a name="parameters"></a>參數  
 `pnChar`  
 發行的機碼的虛擬按鍵碼值的指標。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.  
  
 `nShiftState`  
 包含下列旗標的組合︰  
  
- **SHIFT_MASK**動作期間按下 SHIFT 鍵。  
  
- **CTRL_MASK**動作期間按下 CTRL 鍵。  
  
- **ALT_MASK**動作期間按下 ALT 鍵。  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 KeyUp 事件發生的自動引發，控制項的事件對應必須有定義的內建 KeyUp 事件。  
  
##  <a name="a-namefiremousedowna--colecontrolfiremousedown"></a><a name="firemousedown"></a>COleControl::FireMouseDown  
 在使用中的自訂控制項上按下滑鼠按鈕時呼叫架構。  
  
```  
void FireMouseDown(
    short nButton,  
    short nShiftState,  
    OLE_XPOS_PIXELS x,  
    OLE_YPOS_PIXELS y);
```  
  
### <a name="parameters"></a>參數  
 `nButton`  
 按下滑鼠按鈕的數字值。 它可以包含下列值之一︰  
  
- **LEFT_BUTTON**左邊的滑鼠按鈕已按下。  
  
- **MIDDLE_BUTTON**滑鼠按鈕已按下。  
  
- **RIGHT_BUTTON**滑鼠按鈕已按下。  
  
 `nShiftState`  
 包含下列旗標的組合︰  
  
- **SHIFT_MASK**動作期間按下 SHIFT 鍵。  
  
- **CTRL_MASK**動作期間按下 CTRL 鍵。  
  
- **ALT_MASK**動作期間按下 ALT 鍵。  
  
 *x*  
 滑鼠按鈕已按下時資料指標的 x 座標。 座標是相對於控制項視窗的左上角。  
  
 *y*  
 滑鼠按鈕已按下時資料指標的 y 座標。 座標是相對於控制項視窗的左上角。  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 MouseDown 事件發生的自動引發，控制項的事件對應必須有定義的內建 MouseDown 事件。  
  
##  <a name="a-namefiremousemovea--colecontrolfiremousemove"></a><a name="firemousemove"></a>COleControl::FireMouseMove  
 將游標移至作用中的自訂控制項時，由架構呼叫。  
  
```  
void FireMouseMove(
    short nButton,  
    short nShiftState,  
    OLE_XPOS_PIXELS x,  
    OLE_YPOS_PIXELS y);
```  
  
### <a name="parameters"></a>參數  
 `nButton`  
 按下滑鼠按鈕的數字值。 包含下列值的組合︰  
  
- **LEFT_BUTTON**左邊的滑鼠按鈕已按下動作期間。  
  
- **MIDDLE_BUTTON**滑鼠按鈕已按下動作期間。  
  
- **RIGHT_BUTTON**滑鼠按鈕已按下動作期間。  
  
 `nShiftState`  
 包含下列旗標的組合︰  
  
- **SHIFT_MASK**動作期間按下 SHIFT 鍵。  
  
- **CTRL_MASK**動作期間按下 CTRL 鍵。  
  
- **ALT_MASK**動作期間按下 ALT 鍵。  
  
 *x*  
 資料指標的 x 座標。 座標是相對於控制項視窗的左上角。  
  
 *y*  
 資料指標的 y 座標。 座標是相對於控制項視窗的左上角。  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 MouseMove 事件發生的自動引發，控制項的事件對應必須有定義的內建 MouseMove 事件。  
  
##  <a name="a-namefiremouseupa--colecontrolfiremouseup"></a><a name="firemouseup"></a>COleControl::FireMouseUp  
 作用中的自訂控制項上放開滑鼠按鈕時，由架構呼叫。  
  
```  
void FireMouseUp(
    short nButton,  
    short nShiftState,  
    OLE_XPOS_PIXELS x,  
    OLE_YPOS_PIXELS y);
```  
  
### <a name="parameters"></a>參數  
 `nButton`  
 放開滑鼠按鈕的數值。 它可以包含下列值之一︰  
  
- **LEFT_BUTTON**左邊的滑鼠按鈕已釋放。  
  
- **MIDDLE_BUTTON**放開滑鼠按鈕。  
  
- **RIGHT_BUTTON**放開滑鼠按鈕。  
  
 `nShiftState`  
 包含下列旗標的組合︰  
  
- **SHIFT_MASK**動作期間按下 SHIFT 鍵。  
  
- **CTRL_MASK**動作期間按下 CTRL 鍵。  
  
- **ALT_MASK**動作期間按下 ALT 鍵。  
  
 *x*  
 放開滑鼠按鈕時，資料指標的 x 座標。 座標是相對於控制項視窗的左上角。  
  
 *y*  
 放開滑鼠按鈕時，資料指標的 y 座標。 座標是相對於控制項視窗的左上角。  
  
### <a name="remarks"></a>備註  
 如果此事件定義為自訂的事件，您可以決定引發事件時。  
  
 MouseUp 事件發生的自動引發，控制項的事件對應必須有定義的內建 MouseUp 事件。  
  
##  <a name="a-namefirereadystatechangea--colecontrolfirereadystatechange"></a><a name="firereadystatechange"></a>COleControl::FireReadyStateChange  
 引發事件的目前值的控制項就緒狀態。  
  
```  
void FireReadyStateChange();
```  
  
### <a name="remarks"></a>備註  
 就緒狀態可以是下列值之一︰  
  
 **READYSTATE_UNINITIALIZED**  
 預設的初始化狀態  
  
 **READYSTATE_LOADING**  
 控制項正在載入其屬性  
  
 **READYSTATE_LOADED**  
 初始化控制項  
  
 **READYSTATE_INTERACTIVE**  
 控制項有足夠的資料進行互動，但尚未載入未全部是非同步的資料  
  
 `READYSTATE_COMPLETE`  
 控制項具有所有資料  
  
 使用[GetReadyState](#getreadystate)來判斷控制項的目前就緒程度。  
  
 [InternalSetReadyState](#internalsetreadystate)就緒狀態變更提供的值，則會呼叫`FireReadyStateChange`。  
  
##  <a name="a-namegetactivationpolicya--colecontrolgetactivationpolicy"></a><a name="getactivationpolicy"></a>COleControl::GetActivationPolicy  
 支援的控制項的預設啟動行為會改變`IPointerInactive`介面。  
  
```  
virtual DWORD GetActivationPolicy();
```  
  
### <a name="return-value"></a>傳回值  
 從旗標的組合**POINTERINACTIVE**列舉型別。 可能的旗標如下︰  
  
 **POINTERINACTIVE_ACTIVATEONENTRY**  
 物件也會就地啟動當滑鼠進入它滑鼠移動操作過程中。  
  
 **POINTERINACTIVE_DEACTIVATEONLEAVE**  
 物件應該停用，當滑鼠離開滑鼠移動操作過程中的物件。  
  
 **POINTERINACTIVE_ACTIVATEONDRAG**  
 物件應該是就地啟動時在拖曳期間拖曳滑鼠游標拖放作業。  
  
### <a name="remarks"></a>備註  
 當`IPointerInactive`介面已啟用，容器會將委派`WM_SETCURSOR`和`WM_MOUSEMOVE`給它的訊息。 `COleControl`適當調整滑鼠座標之後，這個介面的實作會分派透過您控制項的訊息對應，這些訊息。  
  
 當容器接收`WM_SETCURSOR`或`WM_MOUSEMOVE`滑鼠指標置於非作用中的物件支援訊息`IPointerInactive`，它應該呼叫`GetActivationPolicy`介面與從傳回的旗標上**POINTERINACTIVE**列舉型別。  
  
 您可以將對應的項目加入至訊息對應處理這些訊息就像一般視窗訊息一樣。 在您的處理常式，請避免使用`m_hWnd`成員變數 （或任何它所使用的成員函式） 但未先檢查其值為非**NULL**。  
  
 任何物件要執行多個設定滑鼠游標和 （或） 引發滑鼠移動事件，例如提供特殊的視覺化回饋，應該會傳回**POINTERINACTIVE_ACTIVATEONENTRY**旗標，然後繪製作用時的意見反應。 如果物件傳回此旗標，應該立即加以就地啟動容器，並再轉寄觸發呼叫相同訊息`GetActivationPolicy`。  
  
 如果兩個**POINTERINACTIVE_ACTIVATEONENTRY**和**POINTERINACTIVE_DEACTIVATEONLEAVE**傳回旗標，然後當滑鼠移到物件時，只會啟用物件。 如果只有**POINTERINACTIVE_ACTIVATEONENTRY**傳回旗標，然後當滑鼠初次進入物件之後，只會啟用物件。  
  
 您也可以作為目標的 OLE 拖曳和卸除作業非現用控制項。 這需要在使用者拖曳物件時，啟動控制項，使控制項的視窗可以登錄為置放目標。 若要使發生在拖曳期間啟動，傳回**POINTERINACTIVE_ACTIVATEONDRAG**旗標︰  
  
 [!code-cpp[NVC_MFCAxCtl #&1;](../../mfc/reference/codesnippet/cpp/colecontrol-class_1.cpp)]  
  
 藉由進行通訊的資訊`GetActivationPolicy`不會快取由容器。 相反地，每次滑鼠進入非作用中的物件，應該呼叫這個方法。  
  
 如果非作用中的物件不是就地啟動當滑鼠進入該要求，其容器應該分派後續`WM_SETCURSOR`藉由呼叫此物件的訊息[OnInactiveSetCursor](#oninactivesetcursor) ，只要將滑鼠指標停留在物件上。  
  
 啟用`IPointerInactive`介面通常表示您想要能夠隨時處理滑鼠訊息的控制項。 若要取得此行為，不支援的容器中`IPointerInactive`必須能夠自動啟動時顯示，控制項的介面，這表示控制項應該具有**OLEMISC_ACTIVATEWHENVISIBLE**之間的其他旗標的旗標。 不過，若要避免這個旗標從生效的容器中，支援`IPointerInactive`，您也可以指定**OLEMISC_IGNOREACTIVATEWHENVISIBLE**旗標︰  
  
 [!code-cpp[NVC_MFCAxCtl #&10;](../../mfc/reference/codesnippet/cpp/colecontrol-class_2.cpp)]  
  
##  <a name="a-namegetambientpropertya--colecontrolgetambientproperty"></a><a name="getambientproperty"></a>COleControl::GetAmbientProperty  
 取得容器的環境屬性的值。  
  
```  
BOOL GetAmbientProperty(
    DISPID dispid,  
    VARTYPE vtProp,  
    void* pvProp);
```  
  
### <a name="parameters"></a>參數  
 *dwDispid*  
 所需的環境屬性的分派 ID。  
  
 `vtProp`  
 指定要傳回之值的類型的變數類型標記`pvProp`。  
  
 `pvProp`  
 變數會接收屬性值或傳回值的位址指標。 This 指標的實際型別必須符合所指定之類型`vtProp`。  
  
|vtProp|PvProp 的型別|  
|------------|--------------------|  
|`VT_BOOL`|**BOOL\***|  
|`VT_BSTR`|**CString\***|  
|`VT_I2`|**簡短\***|  
|`VT_I4`|**長\***|  
|`VT_R4`|**浮點數\***|  
|`VT_R8`|**double\***|  
|`VT_CY`|**CY\***|  
|**VT_COLOR**|**OLE_COLOR\***|  
|**VT_DISPATCH**|**LPDISPATCH\***|  
|**VT_FONT**|**LPFONTDISP\***|  
  
### <a name="return-value"></a>傳回值  
 支援環境的屬性，則為非零值否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您使用`GetAmbientProperty`來擷取環境的 DisplayName 和 ScaleUnits 屬性，設定`vtProp`至`VT_BSTR`和`pvProp`至**CString\***。 如果您要擷取環境的字型屬性，設定`vtProp`至**VT_FONT**和`pvProp`至**LPFONTDISP\***。  
  
 請注意，函式都已經有提供常見的環境屬性，例如[AmbientBackColor](#ambientbackcolor)和[AmbientFont](#ambientfont)。  
  
##  <a name="a-namegetappearancea--colecontrolgetappearance"></a><a name="getappearance"></a>COleControl::GetAppearance  
 實作控制項的內建外觀屬性的 Get 函式。  
  
```  
short GetAppearance ();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值指定為目前的外觀設定**簡短**( `VT_I2`) 值，如果成功。 如果控制項的外觀，而且一般 1 3D 控制項的外觀時，這個值會是零。  
  
##  <a name="a-namegetbackcolora--colecontrolgetbackcolor"></a><a name="getbackcolor"></a>COleControl::GetBackColor  
 實作控制項的內建的背景色彩屬性的 Get 函式。  
  
```  
OLE_COLOR GetBackColor();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值指定為目前的背景色彩**OLE_COLOR**如果成功，則值。 這個值可以轉譯成**COLORREF**值呼叫`TranslateColor`。  
  
##  <a name="a-namegetborderstylea--colecontrolgetborderstyle"></a><a name="getborderstyle"></a>COleControl::GetBorderStyle  
 實作控制項的內建的框線樣式屬性的 Get 函式。  
  
```  
short GetBorderStyle();
```  
  
### <a name="return-value"></a>傳回值  
 如果控制項具有標準框線，，1如果控制項具有無框線，0。  
  
##  <a name="a-namegetcapturea--colecontrolgetcapture"></a><a name="getcapture"></a>COleControl::GetCapture  
 決定是否`COleControl`物件都有滑鼠捕捉。  
  
```  
CWnd* GetCapture();
```  
  
### <a name="return-value"></a>傳回值  
 如果已啟動並無視窗控制項，會傳回**這**如果控制項目前具有滑鼠捕捉 （依控制項的容器來判定），或**NULL**如果沒有擷取。  
  
 否則，會傳回`CWnd`滑鼠捕捉的物件 (與相同`CWnd::GetCapture`)。  
  
### <a name="remarks"></a>備註  
 已啟動的無視窗控制項接收滑鼠捕捉時[SetCapture](#setcapture)呼叫。  
  
##  <a name="a-namegetclassida--colecontrolgetclassid"></a><a name="getclassid"></a>COleControl::GetClassID  
 若要擷取之控制項的 OLE 類別 ID 架構呼叫。  
  
```  
virtual HRESULT GetClassID(LPCLSID pclsid) = 0;  
```  
  
### <a name="parameters"></a>參數  
 *pclsid*  
 指標位置的類別識別碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果呼叫失敗。否則為 0。  
  
### <a name="remarks"></a>備註  
 通常是由實作[IMPLEMENT_OLECREATE_EX](class-factories-and-licensing.md#implement_olecreate_ex)。  
  
##  <a name="a-namegetclientoffseta--colecontrolgetclientoffset"></a><a name="getclientoffset"></a>COleControl::GetClientOffset  
 擷取控制項的矩形區域的左上的角和其工作區的左上的角之間的差異。  
  
```  
virtual void GetClientOffset(long* pdxOffset, long* pdyOffset) const;  
```  
  
### <a name="parameters"></a>參數  
 *pdxOffset*  
 OLE 控制項的用戶端區域的水平位移的指標。  
  
 *pdyOffset*  
 OLE 控制項的用戶端區域的垂直位移的指標。  
  
### <a name="remarks"></a>備註  
 OLE 控制項都有其容器內的矩形區域。 控制項的工作區是不包括框線和捲軸的控制項區域。 擷取位移`GetClientOffset`是控制項的矩形區域的左上的角和其工作區的左上的角之間的差異。 如果您的控制項具有非用戶端項目，而非標準的框線和捲軸，覆寫此成員函式指定位移。  
  
##  <a name="a-namegetclientrecta--colecontrolgetclientrect"></a><a name="getclientrect"></a>COleControl::GetClientRect  
 擷取控制項的工作區的大小。  
  
```  
virtual void GetClientRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指標`RECT`結構，其中包含無視窗控制項的用戶端區域的維度，也就是控制項的大小減去視窗框線、 框架、 捲軸列等等。 `lpRect`參數指出大小的控制項的用戶端矩形，不是它的位置。  
  
##  <a name="a-namegetclientsitea--colecontrolgetclientsite"></a><a name="getclientsite"></a>COleControl::GetClientSite  
 查詢的物件，其目前的用戶端站台容器中的指標。  
  
```  
LPOLECLIENTSITE GetClientSite();
```  
  
### <a name="return-value"></a>傳回值  
 控制項的目前用戶端的站台在其容器中的指標。  
  
### <a name="remarks"></a>備註  
 傳回的指標指向的執行個體`IOleClientSite`。 `IOleClientSite`由容器所實作的介面是物件的檢視，其內容的︰ 它已錨定在文件，它可在此取得其存放裝置、 使用者介面和其他資源。  
  
##  <a name="a-namegetcontrolflagsa--colecontrolgetcontrolflags"></a><a name="getcontrolflags"></a>Clippaintdc  
 擷取控制項旗標設定。  
  
```  
virtual DWORD GetControlFlags();
```  
  
### <a name="return-value"></a>傳回值  
 ControlFlags 列舉中的旗標 ORed 組合︰  
  
 `enum ControlFlags {`  
  
 `fastBeginPaint = 0x0001,`  
  
 `clipPaintDC = 0x0002,`  
  
 `pointerInactive = 0x0004,`  
  
 `noFlickerActivate = 0x0008,`  
  
 `windowlessActivate = 0x0010,`  
  
 `canOptimizeDraw = 0x0020,`  
  
 `};`  
  
### <a name="remarks"></a>備註  
 根據預設，`GetControlFlags`傳回`fastBeginPaint | clipPaintDC`。  
  
 `fastBeginPaint`  
 如果設定，請使用 begin 小畫家函式專供 OLE 控制項，而不是[BeginPaint](http://msdn.microsoft.com/library/windows/desktop/dd183362) API （預設設定）。  
  
 `clipPaintDC`  
 如果沒有設定，會停用來呼叫`IntersectClipRect`由`COleControl`取得小型速度上的優勢。 如果您使用無視窗啟用，旗標會有任何作用。  
  
 `pointerInactive`  
 如果設定，您的控制項是藉由啟用非作用中時提供滑鼠互動`COleControl`的實作`IPointerInactive`介面，預設會停用。  
  
 `noFlickerActivate`  
 如果設定，它會消除額外繪製作業和視覺重繪。 當您的控制項繪製本身中的作用與作用中狀態時使用。 如果您使用無視窗啟用，旗標會有任何作用。  
  
 `windowlessActivate`  
 如果設定，表示您的控制項使用無視窗啟用。  
  
 `canOptimizeDraw`  
 如果設定，表示控制項將會執行最佳化的繪圖，如果容器支援它。  
  
 如需詳細資訊`GetControlFlags`和其他最佳化的 OLE 控制項，請參閱[ActiveX 控制項︰ 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
##  <a name="a-namegetcontrolsizea--colecontrolgetcontrolsize"></a><a name="getcontrolsize"></a>COleControl::GetControlSize  
 擷取 OLE 控制項視窗的大小。  
  
```  
void GetControlSize(
    int* pcx,  
    int* pcy);
```  
  
### <a name="parameters"></a>參數  
 *pcx*  
 指定控制項的寬度，單位為像素。  
  
 *pcy*  
 指定控制項的高度，單位為像素。  
  
### <a name="remarks"></a>備註  
 請注意，用於控制 windows 的所有座標都是相對於控制項的左上角。  
  
##  <a name="a-namegetdca--colecontrolgetdc"></a><a name="getdc"></a>COleControl::GetDC  
 從其容器提供無視窗物件取得檢測 （或相容） 的裝置內容。  
  
```  
CDC* GetDC(
    LPCRECT lprcRect = NULL,
    DWORD dwFlags = OLEDC_PAINTBKGND);
```  
  
### <a name="parameters"></a>參數  
 *lprcRect*  
 無視窗控制項的矩形的指標會想要在工作區座標的控制項重繪。 **NULL**表示完整的物件範圍。  
  
 `dwFlags`  
 繪圖裝置內容的屬性。 選擇如下︰  
  
- **OLEDC_NODRAW**表示物件不會使用裝置內容，以執行任何繪圖，但只以取得顯示裝置的相關資訊。 容器只應該傳遞視窗的 DC，而不需進一步處理。  
  
- **OLEDC_PAINTBKGND**要求容器繪製背景，再傳回 DC。 如果它所要求的 DC 重繪具有透明背景的區域物件應該使用這個旗標。  
  
- **OLEDC_OFFSCREEN**通知物件想要呈現到幕外的點陣圖，然後複製到螢幕的容器。 當它是執行繪圖作業會產生大量的重繪閃動物件應該使用這個旗標。 容器是免費或不接受此要求。 不過，如果未設定此旗標，容器必須交回螢幕上的 DC。 這可讓執行直接從螢幕作業，例如顯示選取的物件 (透過**XOR**作業)。  
  
### <a name="return-value"></a>傳回值  
 容器的顯示裝置內容指標`CWnd`工作區如果成功，否則傳回值就會是**NULL**。 顯示裝置內容可以用於後續的 GDI 函式，來繪製容器的視窗工作區中。  
  
### <a name="remarks"></a>備註  
 [ReleaseDC](#releasedc)必須呼叫成員函式，以繪製之後釋出的內容。 當呼叫`GetDC`，物件會傳遞他們想要在自己的用戶端座標中繪製的矩形。 `GetDC`將這些檔案的容器工作區座標來轉譯。 不應在物件要求大於它自己的用戶端區域矩形，其大小可以用來擷取所要繪製矩形[GetClientRect](#getclientrect)。 這可防止不慎繪圖，但不應該以物件。  
  
##  <a name="a-namegetenableda--colecontrolgetenabled"></a><a name="getenabled"></a>COleControl::GetEnabled  
 實作控制項的內建 Enabled 屬性的 Get 函式。  
  
```  
BOOL GetEnabled();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果已啟用控制項。否則為 0。  
  
##  <a name="a-namegetextendedcontrola--colecontrolgetextendedcontrol"></a><a name="getextendedcontrol"></a>COleControl::GetExtendedControl  
 取得表示一組延伸的屬性與控制項之容器所維護的物件的指標。  
  
```  
LPDISPATCH GetExtendedControl();
```  
  
### <a name="return-value"></a>傳回值  
 容器的指標的擴充控制項物件。 如果沒有可用的物件，則值是**NULL**。  
  
 此物件可能會透過管理其`IDispatch`介面。 您也可以使用`QueryInterface`來取得物件提供的其他可用的介面。 不過，物件不需要支援一組特定的介面。 請注意，依賴特定功能的容器的擴充的控制項物件會限制其他任意容器控制項的可攜性。  
  
### <a name="remarks"></a>備註  
 呼叫此函式的函式會負責釋放指標的物件完成時。 請注意，不需要支援此物件的容器。  
  
##  <a name="a-namegetfocusa--colecontrolgetfocus"></a><a name="getfocus"></a>COleControl::GetFocus  
 決定是否`COleControl`物件具有焦點。  
  
```  
CWnd* GetFocus();
```  
  
### <a name="return-value"></a>傳回值  
 如果已啟動並無視窗控制項，會傳回**這**如果控制項目前具有鍵盤焦點 （依控制項的容器來判定） 或**NULL**不具有焦點時。  
  
 否則，會傳回`CWnd`具有焦點的物件 (與相同`CWnd::GetFocus`)。  
  
### <a name="remarks"></a>備註  
 已啟動的無視窗控制項取得焦點時[SetFocus](#setfocus)呼叫。  
  
##  <a name="a-namegetfonta--colecontrolgetfont"></a><a name="getfont"></a>COleControl::GetFont  
 實作 Get 函式的內建字型屬性。  
  
```  
LPFONTDISP GetFont();
```  
  
### <a name="return-value"></a>傳回值  
 控制項的內建字型屬性的字型分派介面指標。  
  
### <a name="remarks"></a>備註  
 請注意，呼叫端必須釋放物件時完成。 在控制項的實作，使用`InternalGetFont`存取控制項的內建字型物件。 如需有關如何在您的控制項中使用字型的詳細資訊，請參閱文章[ActiveX 控制項︰ 使用 ActiveX 控制項的字型](../../mfc/mfc-activex-controls-using-fonts.md)。  
  
##  <a name="a-namegetfonttextmetricsa--colecontrolgetfonttextmetrics"></a><a name="getfonttextmetrics"></a>COleControl::GetFontTextMetrics  
 任何測量的文字度量`CFontHolder`所擁有的物件。  
  
```  
void GetFontTextMetrics(
    LPTEXTMETRIC lptm,  
    CFontHolder& fontHolder);
```  
  
### <a name="parameters"></a>參數  
 `lptm`  
 指標[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)結構。  
  
 `fontHolder`  
 若要參考[CFontHolder](../../mfc/reference/cfontholder-class.md)物件。  
  
### <a name="remarks"></a>備註  
 這種字型可以選取與[COleControl::SelectFontObject](#selectfontobject)函式。 `GetFontTextMetrics`將會初始化`TEXTMETRIC`指向結構`lptm`有效的度量資訊`fontHolder`的字型，如果成功，或以零填滿結構，如果不成功。 您應該使用此函式，而不是[GetTextMetrics](http://msdn.microsoft.com/library/windows/desktop/dd144941)時繪製控制項，因為控制項，如同任何內嵌 OLE 物件，可能需要將自己轉譯為中繼檔。  
  
 `TEXTMETRIC`結構的預設字型是重新整理時[SelectFontObject](#selectfontobject)函式呼叫。 您應該呼叫`GetFontTextMetrics`唯一之後選取內建字型屬性，以確保它所提供的資訊無效。  
  
##  <a name="a-namegetforecolora--colecontrolgetforecolor"></a><a name="getforecolor"></a>COleControl::GetForeColor  
 實作內建的前景色彩屬性的 Get 函式。  
  
```  
OLE_COLOR GetForeColor();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值指定為目前的前景色彩**OLE_COLOR**如果成功，則值。 這個值可以轉譯成[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值呼叫`TranslateColor`。  
  
##  <a name="a-namegethwnda--colecontrolgethwnd"></a><a name="gethwnd"></a>COleControl::GetHwnd  
 實作內建的 hWnd 屬性的 Get 函式。  
  
```  
OLE_HANDLE GetHwnd();
```  
  
### <a name="return-value"></a>傳回值  
 OLE 控制項的視窗控制代碼，如果有的話。否則**NULL**。  
  
##  <a name="a-namegetmessagestringa--colecontrolgetmessagestring"></a><a name="getmessagestring"></a>COleControl::GetMessageString  
 若要取得描述所識別的功能表項目的用途的簡短字串架構呼叫`nID`。  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 功能表項目 id。  
  
 `rMessage`  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)透過將傳回的字串物件。  
  
### <a name="remarks"></a>備註  
 這可用來取得在狀態列中顯示訊息，在反白顯示的功能表項目。 預設實作會嘗試載入所識別的字串資源`nID`。  
  
##  <a name="a-namegetnotsupporteda--colecontrolgetnotsupported"></a><a name="getnotsupported"></a>Colecontrol:: Getnotsupported  
 將控制項的屬性值，使用者無法存取。  
  
```  
void GetNotSupported();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個函式取代任何屬性的 Get 函式擷取由使用者控制項的屬性不支援的位置。 一個範例是唯寫屬性。  
  
##  <a name="a-namegetreadystatea--colecontrolgetreadystate"></a><a name="getreadystate"></a>COleControl::GetReadyState  
 傳回控制項的整備狀態。  
  
```  
long GetReadyState();
```  
  
### <a name="return-value"></a>傳回值  
 整備控制項的狀態，下列值之一︰  
  
 **READYSTATE_UNINITIALIZED**  
 預設的初始化狀態  
  
 **READYSTATE_LOADING**  
 控制項正在載入其屬性  
  
 **READYSTATE_LOADED**  
 初始化控制項  
  
 **READYSTATE_INTERACTIVE**  
 控制項有足夠的資料進行互動，但尚未載入未全部是非同步的資料  
  
 `READYSTATE_COMPLETE`  
 控制項具有所有資料  
  
### <a name="remarks"></a>備註  
 大部分的簡單控制項永遠都不需要區分**LOADED**和`INTERACTIVE`。 不過，支援資料路徑屬性的控制項可能無法準備進行互動，直到至少部分資料都以非同步方式接收。 控制項應儘速成為互動式。  
  
##  <a name="a-namegetrectincontainera--colecontrolgetrectincontainer"></a><a name="getrectincontainer"></a>COleControl::GetRectInContainer  
 取得相對於容器，以裝置單位來表示控制項的矩形的座標。  
  
```  
BOOL GetRectInContainer(LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 控制項的座標複製矩形結構的指標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果控制項是就地啟用作用中。否則為 0。  
  
### <a name="remarks"></a>備註  
 矩形才有效，如果控制項是就地啟用作用中。  
  
##  <a name="a-namegetstocktextmetricsa--colecontrolgetstocktextmetrics"></a><a name="getstocktextmetrics"></a>COleControl::GetStockTextMetrics  
 控制項的內建字型屬性，可以使用所選取的文字度量會測量[SelectStockFont](#selectstockfont)函式。  
  
```  
void GetStockTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>參數  
 `lptm`  
 指標[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)結構。  
  
### <a name="remarks"></a>備註  
 `GetStockTextMetrics`函式會初始化`TEXTMETRIC`指向結構`lptm`有效的度量資訊，如果成功，或填入零，如果不成功的結構。 使用此函式，而不是[GetTextMetrics](http://msdn.microsoft.com/library/windows/desktop/dd144941)時繪製控制項，因為控制項，如同任何內嵌 OLE 物件，可能需要將自己轉譯為中繼檔。  
  
 `TEXTMETRIC`結構的預設字型是重新整理時`SelectStockFont`函式呼叫。 之後，才選取內建的字型，才能確保它所提供的資訊正確，您應該呼叫此函式。  
  
##  <a name="a-namegettexta--colecontrolgettext"></a><a name="gettext"></a>COleControl::GetText  
 實作內建的 Text 或 Caption 屬性的 Get 函式。  
  
```  
BSTR GetText();
```  
  
### <a name="return-value"></a>傳回值  
 控制文字字串或長度為零的字串如果字串不存在於目前的值。  
  
> [!NOTE]
>  如需有關`BSTR`資料類型，請參閱[資料型別](../../mfc/reference/data-types-mfc.md)巨集和全域變數一節。  
  
### <a name="remarks"></a>備註  
 請注意，呼叫此函式的呼叫端必須`SysFreeString`字串傳回以免費資源。 在控制項的實作，使用`InternalGetText`存取控制項的內建的 Text 或 Caption 屬性。  
  
##  <a name="a-namegetwindowlessdroptargeta--colecontrolgetwindowlessdroptarget"></a><a name="getwindowlessdroptarget"></a>Colecontrol:: Getwindowlessdroptarget  
 覆寫`GetWindowlessDropTarget`當您想將無視窗控制項作為目標的 OLE 拖放作業。  
  
```  
virtual IDropTarget* GetWindowlessDropTarget();
```  
  
### <a name="return-value"></a>傳回值  
 物件的指標`IDropTarget`介面。 因為它並沒有視窗，無視窗物件無法註冊`IDropTarget`介面。 不過，若要加入功能，無視窗物件仍可以實作介面及傳回在`GetWindowlessDropTarget`。  
  
### <a name="remarks"></a>備註  
 通常這會需要將控制項的視窗登錄為置放目標。 但是由於控制項沒有自己的視窗，因此容器會使用自己的視窗做為置放目標。 控制項只需要提供的實作`IDropTarget`介面的容器可以在適當時委派呼叫。 例如:   
  
 [!code-cpp[NVC_MFCAxCtl #&2;](../../mfc/reference/codesnippet/cpp/colecontrol-class_3.cpp)]  
  
##  <a name="a-nameinitializeiidsa--colecontrolinitializeiids"></a><a name="initializeiids"></a>COleControl::InitializeIIDs  
 通知控制項將會使用與 Iid 的基底類別。  
  
```  
void InitializeIIDs(
    const IID* piidPrimary,
    const IID* piidEvents);
```  
  
### <a name="parameters"></a>參數  
 *piidPrimary*  
 控制項的主要分派介面的介面 ID 的指標。  
  
 *piidEvents*  
 控制項的事件介面的介面 ID 的指標。  
  
### <a name="remarks"></a>備註  
 控制項的建構函式以通知的介面識別碼將會使用您的控制項的基底類別中呼叫此函式。  
  
##  <a name="a-nameinternalgetfonta--colecontrolinternalgetfont"></a><a name="internalgetfont"></a>COleControl::InternalGetFont  
 存取您的控制項的內建字型屬性  
  
```  
CFontHolder& InternalGetFont();
```  
  
### <a name="return-value"></a>傳回值  
 參考[CFontHolder](../../mfc/reference/cfontholder-class.md)物件，其中包含內建字型物件。  
  
##  <a name="a-nameinternalgettexta--colecontrolinternalgettext"></a><a name="internalgettext"></a>COleControl::InternalGetText  
 存取控制項的內建的 Text 或 Caption 屬性。  
  
```  
const CString& InternalGetText();
```  
  
### <a name="return-value"></a>傳回值  
 控制項的文字字串的參考。  
  
##  <a name="a-nameinternalsetreadystatea--colecontrolinternalsetreadystate"></a><a name="internalsetreadystate"></a>Colecontrol:: Internalsetreadystate  
 設定控制項的整備狀態。  
  
```  
void InternalSetReadyState(long lNewReadyState);
```  
  
### <a name="parameters"></a>參數  
 *lNewReadyState*  
 若要設定下列值之一的控制項整備狀態︰  
  
 **READYSTATE_UNINITIALIZED**  
 預設的初始化狀態  
  
 **READYSTATE_LOADING**  
 控制項正在載入其屬性  
  
 **READYSTATE_LOADED**  
 初始化控制項  
  
 **READYSTATE_INTERACTIVE**  
 控制項有足夠的資料進行互動，但尚未載入未全部是非同步的資料  
  
 `READYSTATE_COMPLETE`  
 控制項具有所有資料  
  
### <a name="remarks"></a>備註  
 大部分的簡單控制項永遠都不需要區分**LOADED**和`INTERACTIVE`。 不過，支援資料路徑屬性的控制項可能無法準備進行互動，直到至少部分資料都以非同步方式接收。 控制項應儘速成為互動式。  
  
##  <a name="a-nameinvalidatecontrola--colecontrolinvalidatecontrol"></a><a name="invalidatecontrol"></a>COleControl::InvalidateControl  
 強制重新繪製控制項。  
  
```  
void InvalidateControl(
    LPCRECT lpRect = NULL,  
    BOOL bErase = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 控制項是即將失效的區域的指標。  
  
 `bErase`  
 指定是否要處理的更新區域時清除的背景更新區域內。  
  
### <a name="remarks"></a>備註  
 如果`lpRect`有**NULL**值，將會重新繪製整個控制項。 如果`lpRect`不**NULL**，這表示要失效的控制項的矩形部分。 控制項沒有視窗，或不在目前作用中，矩形會被忽略，而且呼叫用戶端站台的[IAdviseSink::OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337)成員函式。 使用此函式，而不是`CWnd::InvalidateRect`或`InvalidateRect`。  
  
##  <a name="a-nameinvalidatergna--colecontrolinvalidatergn"></a><a name="invalidatergn"></a>COleControl::InvalidateRgn  
 使容器視窗的用戶端區域內的指定區域失效。  
  
```  
void InvalidateRgn(CRgn* pRgn, BOOL bErase = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pRgn`  
 指標[CRgn](../../mfc/reference/crgn-class.md)物件，可識別要使其失效，包含視窗的用戶端座標中的 OLE 物件的顯示區域。 如果這個參數是**NULL**，範圍是整個物件。  
  
 `bErase`  
 指定是否要清除失效的區域內的背景。 如果**TRUE**，背景會清除。 如果**FALSE**，背景會維持不變。  
  
### <a name="remarks"></a>備註  
 這可以用來重繪其容器內的無視窗控制項。 失效的區域，以及所有其他區域中更新區域中，標示為進行繪製時的下一步[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)傳送訊息。  
  
 如果`bErase`是**TRUE**更新區域的任何部分，會清除整個區域，不只是在指定的組件中的背景。  
  
##  <a name="a-nameisconvertingvbxa--colecontrolisconvertingvbx"></a><a name="isconvertingvbx"></a>COleControl::IsConvertingVBX  
 可讓 OLE 控制項的特製化的載入。  
  
```  
BOOL IsConvertingVBX();
```  
  
### <a name="return-value"></a>傳回值  
 要轉換的控制項; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 當轉換使用 VBX 的表單控制項使用 OLE 控制項的其中一個時，則可能需要特殊載入 OLE 控制項的程式碼。 例如，如果您正在載入您的 OLE 控制項的執行個體，您可能必須呼叫[PX_Font](persistence-of-ole-controls.md#px_font)中您`DoPropExchange`:  
  
 [!code-cpp[NVC_MFCAxCtl #&3;](../../mfc/reference/codesnippet/cpp/colecontrol-class_4.cpp)]  
  
 不過，VBX 控制項沒有 Font 物件。已分別儲存每個字型屬性。 在此情況下，您會使用`IsConvertingVBX`來區別這兩個案例︰  
  
 [!code-cpp[NVC_MFCAxCtl #&4;](../../mfc/reference/codesnippet/cpp/colecontrol-class_5.cpp)]  
  
 另一種情況是如果 VBX 控制項儲存專用的二進位資料 (在其**VBM_SAVEPROPERTY**訊息處理常式)，以及 OLE 控制項將二進位資料儲存在不同的格式。 如果您想要您的 OLE 控制項回溯相容 VBX 控制項，您可以閱讀這兩種舊的和新格式使用`IsConvertingVBX`函式，以利是否載入 VBX 控制項或 OLE 控制項。  
  
 在控制項的`DoPropExchange`函式，您可以檢查這個條件並如果為 true，執行這項轉換 （例如上述範例中） 特定的載入程式碼。 如果控制項不會進行轉換，您可以執行的程式碼正常負載。 這項功能僅適用於 VBX 對應項目要轉換的控制項。  
  
##  <a name="a-nameisinvokealloweda--colecontrolisinvokeallowed"></a><a name="isinvokeallowed"></a>COleControl::IsInvokeAllowed  
 可讓自動化方法引動過程。  
  
```  
BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果控制項已初始化。否則為 0。  
  
### <a name="remarks"></a>備註  
 架構的實作**Excepinfo**呼叫**IsInvokeAllowed**來判斷指定的函式 (由`dispid`) 可能會叫用。 OLE 控制項的預設行為是讓自動化方法，來初始化的控制項; 時，才會叫用不過， **IsInvokeAllowed**是虛擬函式，而且可能會覆寫必要 （例如，當控制項當作 「 自動化 」 伺服器）。 如需詳細資訊，請參閱知識庫文件 Q166472，「 如何︰ 使用 OLE 控制項為 Automation 伺服器。 」 知識庫文件可在 MSDN Library 中的 Visual Studio 文件或[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="a-nameismodifieda--colecontrolismodified"></a><a name="ismodified"></a>COleControl::IsModified  
 決定是否已修改控制項的狀態。  
  
```  
BOOL IsModified();
```  
  
### <a name="return-value"></a>傳回值  
 如果自上次儲存; 已修改控制項的狀態為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 屬性值變更時，會修改控制項的狀態。  
  
##  <a name="a-nameisoptimizeddrawa--colecontrolisoptimizeddraw"></a><a name="isoptimizeddraw"></a>Colecontrol:: Isoptimizeddraw  
 判斷容器是否支援目前的繪圖作業最佳化的繪圖。  
  
```  
BOOL IsOptimizedDraw();
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**容器支援最佳化繪製目前的繪製作業，否則如果**FALSE**。  
  
### <a name="remarks"></a>備註  
 如果支援最佳化的繪圖，然後控制項需要選取舊物件 （畫筆、 筆刷、 字型、 等等） 放入裝置內容完成繪圖。  
  
##  <a name="a-nameissubclassedcontrola--colecontrolissubclassedcontrol"></a><a name="issubclassedcontrol"></a>COleControl::IsSubclassedControl  
 若要判斷是否控制項子類別化 Windows 控制項架構呼叫。  
  
```  
virtual BOOL IsSubclassedControl();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果控制項子類別化。否則為 0。  
  
### <a name="remarks"></a>備註  
 您必須覆寫這個函式，並傳回**TRUE**如果您的 OLE 控制項的子類別化 Windows 控制項。  
  
##  <a name="a-nameloada--colecontrolload"></a><a name="load"></a>COleControl::Load  
 重設任何先前的資料，以非同步方式載入，並起始新載入的控制項的非同步屬性。  
  
```  
void Load(LPCTSTR strNewPath, CDataPathProperty& prop);
```  
  
### <a name="parameters"></a>參數  
 *strNewPath*  
 包含參考的非同步控制項屬性的絕對位置路徑的字串指標。  
  
 *屬性*  
 A [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)實作非同步控制項屬性的物件。  
  
##  <a name="a-namelockinplaceactivea--colecontrollockinplaceactive"></a><a name="lockinplaceactive"></a>COleControl::LockInPlaceActive  
 防止停用您的控制項容器。  
  
```  
BOOL LockInPlaceActive(BOOL bLock);
```  
  
### <a name="parameters"></a>參數  
 `bLock`  
 **TRUE**就地作用中狀態的控制項是否被鎖定。**FALSE**是否要解除鎖定。  
  
### <a name="return-value"></a>傳回值  
 非零，如果鎖定成功。否則為 0。  
  
### <a name="remarks"></a>備註  
 請注意，每個控制項的鎖定必須搭配控制項完成後解除鎖定。 您應該只鎖定您的控制項短的時間，例如時引發事件。  
  
##  <a name="a-nameonambientpropertychangea--colecontrolonambientpropertychange"></a><a name="onambientpropertychange"></a>COleControl::OnAmbientPropertyChange  
 架構容器的環境屬性值變更時呼叫。  
  
```  
virtual void OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>參數  
 *dispID*  
 變更的環境屬性的分派 ID 或**DISPID_UNKNOWN**如果多個屬性已變更。  
  
##  <a name="a-nameonappearancechangeda--colecontrolonappearancechanged"></a><a name="onappearancechanged"></a>COleControl::OnAppearanceChanged  
 內建的外觀屬性值變更時，由架構呼叫。  
  
```  
virtual void OnAppearanceChanged ();
```  
  
### <a name="remarks"></a>備註  
 如果您要通知之後，這個屬性會變更，請覆寫這個函式。 預設實作會呼叫`InvalidateControl`。  
  
##  <a name="a-nameonbackcolorchangeda--colecontrolonbackcolorchanged"></a><a name="onbackcolorchanged"></a>COleControl::OnBackColorChanged  
 內建的背景色彩屬性值變更時，由架構呼叫。  
  
```  
virtual void OnBackColorChanged();
```  
  
### <a name="remarks"></a>備註  
 如果您要通知之後，這個屬性會變更，請覆寫這個函式。 預設實作會呼叫`InvalidateControl`。  
  
##  <a name="a-nameonborderstylechangeda--colecontrolonborderstylechanged"></a><a name="onborderstylechanged"></a>COleControl::OnBorderStyleChanged  
 內建的框線樣式屬性值變更時，由架構呼叫。  
  
```  
virtual void OnBorderStyleChanged();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`InvalidateControl`。  
  
 如果您要通知之後，這個屬性會變更，請覆寫這個函式。  
  
##  <a name="a-nameonclicka--colecontrolonclick"></a><a name="onclick"></a>COleControl::OnClick  
 在按一下滑鼠按鈕，或已叫用 DoClick 內建方法時，由架構呼叫。  
  
```  
virtual void OnClick(USHORT iButton);
```  
  
### <a name="parameters"></a>參數  
 *iButton*  
 滑鼠按鈕的索引。 可以有下列值之一︰  
  
- **LEFT_BUTTON**按下滑鼠左鍵。  
  
- **MIDDLE_BUTTON**按下滑鼠中間鍵。  
  
- **RIGHT_BUTTON**滑鼠按鈕。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`COleControl::FireClick`。  
  
 覆寫此成員函式，來修改或擴充預設的處理。  
  
##  <a name="a-nameonclosea--colecontrolonclose"></a><a name="onclose"></a>COleControl::OnClose  
 容器控制項的呼叫時，由框架呼叫**IOleControl::Close**函式。  
  
```  
virtual void OnClose(DWORD dwSaveOption);
```  
  
### <a name="parameters"></a>參數  
 `dwSaveOption`  
 旗標，指出是否應該載入之前儲存物件。 有效值為：  
  
- `OLECLOSE_SAVEIFDIRTY`  
  
- `OLECLOSE_NOSAVE`  
  
- `OLECLOSE_PROMPTSAVE`  
  
### <a name="remarks"></a>備註  
 根據預設，`OnClose`儲存控制項物件，如果已修改和`dwSaveOption`是`OLECLOSE_SAVEIFDIRTY`或`OLECLOSE_PROMPTSAVE`。  
  
##  <a name="a-nameondoverba--colecontrolondoverb"></a><a name="ondoverb"></a>COleControl::OnDoVerb  
 當容器呼叫由架構呼叫**IOleObject::DoVerb**成員函式。  
  
```  
virtual BOOL OnDoVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `iVerb`  
 要叫用該控制動詞索引。  
  
 `lpMsg`  
 因為要叫用動詞命令的 Windows 訊息指標。  
  
 `hWndParent`  
 控制項的父視窗控制代碼。 如果動詞命令的執行會建立視窗 （或 windows），`hWndParent`應該當做父代。  
  
 `lpRect`  
 座標相對於容器的控制項複製 RECT 結構的指標。  
  
### <a name="return-value"></a>傳回值  
 如果呼叫成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會使用`ON_OLEVERB`和`ON_STDOLEVERB`訊息對應項目，以判斷要叫用適當的函式。  
  
 覆寫這個函式來變更預設的動詞命令的處理。  
  
##  <a name="a-nameondrawa--colecontrolondraw"></a><a name="ondraw"></a>COleControl::OnDraw  
 使用指定的裝置內容之週框矩形內繪製 OLE 控制項架構呼叫。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rcBounds,  
    const CRect& rcInvalid);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 發生在繪製的裝置內容。  
  
 `rcBounds`  
 控制項，包括框線的矩形區域。  
  
 `rcInvalid`  
 無效的控制項矩形區域。  
  
### <a name="remarks"></a>備註  
 `OnDraw`通常會呼叫傳遞做為螢幕裝置內容的螢幕上的`pDC`。 `rcBounds`參數會識別在目標裝置內容 （相對於其目前的對應模式） 的矩形。 `rcInvalid`參數是無效的實際矩形。 在某些情況下，這會是較小的區域，比`rcBounds`。  
  
##  <a name="a-nameondrawmetafilea--colecontrolondrawmetafile"></a><a name="ondrawmetafile"></a>Colecontrol:: Ondrawmetafile  
 使用指定的中繼檔裝置內容之週框矩形內繪製 OLE 控制項架構呼叫。  
  
```  
virtual void OnDrawMetafile(
    CDC* pDC,  
    const CRect& rcBounds);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 發生在繪製的裝置內容。  
  
 `rcBounds`  
 控制項，包括框線的矩形區域。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[OnDraw](#ondraw)函式。  
  
##  <a name="a-nameonedita--colecontrolonedit"></a><a name="onedit"></a>COleControl::OnEdit  
 會使要啟用的 UI 控制項。  
  
```  
virtual BOOL OnEdit(
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpMsg`  
 指標，叫用動詞命令的 Windows 訊息。  
  
 `hWndParent`  
 控制項的父視窗控制代碼。  
  
 `lpRect`  
 矩形容器中控制項所使用的指標。  
  
### <a name="return-value"></a>傳回值  
 如果呼叫成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這有相同的效果，叫用控制項的`OLEIVERB_UIACTIVATE`動詞命令。  
  
 此函式通常是為處理常式函式`ON_OLEVERB`訊息對應項目。 讓 [編輯] 動詞命令功能表控制項的 「 物件 」。 例如：  
  
 [!code-cpp[NVC_MFCAxCtl #&5;](../../mfc/reference/codesnippet/cpp/colecontrol-class_6.cpp)]  
  
##  <a name="a-nameonenabledchangeda--colecontrolonenabledchanged"></a><a name="onenabledchanged"></a>COleControl::OnEnabledChanged  
 股票圖 Enabled 屬性值變更時，由架構呼叫。  
  
```  
virtual void OnEnabledChanged();
```  
  
### <a name="remarks"></a>備註  
 如果您要通知之後，這個屬性會變更，請覆寫這個函式。 預設實作會呼叫[InvalidateControl](#invalidatecontrol)。  
  
##  <a name="a-nameonenumverbsa--colecontrolonenumverbs"></a><a name="onenumverbs"></a>COleControl::OnEnumVerbs  
 當容器呼叫由架構呼叫**IOleObject::EnumVerbs**成員函式。  
  
```  
virtual BOOL OnEnumVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>參數  
 `ppenumOleVerb`  
 指標**IEnumOLEVERB**列舉控制項的動詞命令的物件。  
  
### <a name="return-value"></a>傳回值  
 動詞命令是可使用; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會列舉`ON_OLEVERB`訊息對應中的項目。  
  
 覆寫這個函式來變更預設的建立方式的列舉動詞命令。  
  
##  <a name="a-nameoneventadvisea--colecontroloneventadvise"></a><a name="oneventadvise"></a>COleControl::OnEventAdvise  
 當連接或中斷連線的 OLE 控制項的事件處理常式時，由架構呼叫。  
  
```  
virtual void OnEventAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>參數  
 `bAdvise`  
 **TRUE**表示控制項中已連接的事件處理常式。 **FALSE**表示事件處理常式已中斷連接控制項。  
  
##  <a name="a-nameonfontchangeda--colecontrolonfontchanged"></a><a name="onfontchanged"></a>COleControl::OnFontChanged  
 架構的內建字型屬性值變更時呼叫。  
  
```  
virtual void OnFontChanged();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`COleControl::InvalidateControl`。 如果控制項子類別化 Windows 控制項，也會傳送的預設實作**WM_SETFONT**訊息至控制項的視窗。  
  
 如果您要通知之後，這個屬性會變更，請覆寫這個函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAxCtl #&6;](../../mfc/reference/codesnippet/cpp/colecontrol-class_7.cpp)]  
  
##  <a name="a-nameonforecolorchangeda--colecontrolonforecolorchanged"></a><a name="onforecolorchanged"></a>COleControl::OnForeColorChanged  
 內建的前景色彩屬性值變更時，由架構呼叫。  
  
```  
virtual void OnForeColorChanged();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`InvalidateControl`。  
  
 如果您要通知之後，這個屬性會變更，請覆寫這個函式。  
  
##  <a name="a-nameonfreezeeventsa--colecontrolonfreezeevents"></a><a name="onfreezeevents"></a>COleControl::OnFreezeEvents  
 容器會呼叫後，由框架呼叫**IOleControl::FreezeEvents**。  
  
```  
virtual void OnFreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>參數  
 `bFreeze`  
 **TRUE**如果控制項的事件處理就會凍結，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。  
  
 如果您想要其他的行為，當您凍結或解除凍結但事件處理時，請覆寫這個函式。  
  
##  <a name="a-nameongetcolorseta--colecontrolongetcolorset"></a><a name="ongetcolorset"></a>COleControl::OnGetColorSet  
 當容器呼叫由架構呼叫**IViewObject::GetColorSet**成員函式。  
  
```  
virtual BOOL OnGetColorSet(
    DVTARGETDEVICE* ptd,  
    HDC hicTargetDev,  
    LPLOGPALETTE* ppColorSet);
```  
  
### <a name="parameters"></a>參數  
 `ptd`  
 指向圖片應該轉譯為其目標裝置。 如果這個值是**NULL**，圖片應該呈現的預設目標裝置，通常是顯示裝置。  
  
 `hicTargetDev`  
 指定的資訊內容所指示的目標裝置上`ptd`。 這個參數可以是裝置內容，但是不一定。 If `ptd` is **NULL**, `hicTargetDev` should also be **NULL**.  
  
 *ppColorSet*  
 色彩，會使用一組應該複製到其中的位置指標。 如果函式不會傳回的色彩設定， **NULL**傳回。  
  
### <a name="return-value"></a>傳回值  
 非零，如果傳回有效的色彩集。否則為 0。  
  
### <a name="remarks"></a>備註  
 容器會呼叫此函式來取得繪製 OLE 控制項所需的所有色彩。 容器可以使用取得搭配必須設定整體的色彩調色盤的色彩的色彩集。 預設實作會傳回**FALSE**。  
  
 覆寫這個函式來執行這項要求的任何特殊處理。  
  
##  <a name="a-nameongetcontrolinfoa--colecontrolongetcontrolinfo"></a><a name="ongetcontrolinfo"></a>COleControl::OnGetControlInfo  
 當控制項的容器已要求控制項的相關資訊，由架構呼叫。  
  
```  
virtual void OnGetControlInfo(LPCONTROLINFO pControlInfo);
```  
  
### <a name="parameters"></a>參數  
 `pControlInfo`  
 指標[之 CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734)結構，以進行填寫。  
  
### <a name="remarks"></a>備註  
 這項資訊主要是包含控制項的助憶鍵的描述。 預設實作填滿`pControlInfo`預設資訊。  
  
 如果您的控制項需要處理助憶鍵會覆寫這個函式。  
  
##  <a name="a-nameongetdisplaystringa--colecontrolongetdisplaystring"></a><a name="ongetdisplaystring"></a>COleControl::OnGetDisplayString  
 若要取得字串，表示所識別之屬性的目前值架構呼叫`dispid`。  
  
```  
virtual BOOL OnGetDisplayString(
    DISPID dispid,  
    CString& strValue);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 控制項屬性的分派識別碼。  
  
 `strValue`  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)透過將傳回的字串物件。  
  
### <a name="return-value"></a>傳回值  
 如果字串中傳回非零*strValue;*否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您的控制項具有的屬性，其值不能直接轉換為字串，而且您想要在容器提供屬性瀏覽器中顯示的屬性值會覆寫這個函式。  
  
##  <a name="a-nameongetinplacemenua--colecontrolongetinplacemenu"></a><a name="ongetinplacemenu"></a>COleControl::OnGetInPlaceMenu  
 取得合併到現有的容器的功能表的功能表啟動的 UI 控制項時，由架構呼叫。  
  
```  
virtual HMENU OnGetInPlaceMenu();
```  
  
### <a name="return-value"></a>傳回值  
 控制項的功能表的控制代碼或**NULL**控制項有無。 預設實作會傳回**NULL**。  
  
### <a name="remarks"></a>備註  
 如需有關合併 OLE 資源的詳細資訊，請參閱文章[功能表和資源 (OLE)](../../mfc/menus-and-resources-ole.md)。  
  
##  <a name="a-nameongetnaturalextenta--colecontrolongetnaturalextent"></a><a name="ongetnaturalextent"></a>COleControl::OnGetNaturalExtent  
 以回應容器的架構呼叫**IViewObjectEx::GetNaturalExtent**要求。  
  
```  
virtual BOOL OnGetNaturalExtent(
    DWORD dwAspect,
    LONG lindex,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```  
  
### <a name="parameters"></a>參數  
 `dwAspect`  
 指定物件要進行表示的方式。 表示包含內容、 圖示、 縮圖或列印的文件。 有效的值取自列舉[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)或**DVASPECT2**。  
  
 *lindex*  
 感興趣的物件部分。 目前只支援-1 是有效的。  
  
 `ptd`  
 指向[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)結構定義傳回的物件大小的目標裝置。  
  
 `hicTargetDev`  
 指定所指示的目標裝置的資訊內容`ptd`參數物件可以從中擷取裝置度量資訊，並測試裝置的功能。 如果`ptd`是**NULL**，該物件應該忽略中的值`hicTargetDev`參數。  
  
 *pExtentInfo*  
 指向**DVEXTENTINFO**指定調整大小資料結構。 **DVEXTENTINFO**結構是︰  
  
 `typedef struct  tagExtentInfo`  
  
 `{`  
  
 `UINT cb;`  
  
 `DWORD dwExtentMode;`  
  
 `SIZEL sizelProposed;`  
  
 `}   DVEXTENTINFO;`  
  
 結構成員`dwExtentMode`可以接受兩個值之一︰  
  
- **DVEXTENT_CONTENT**看看是否有多大控制項應該以完全符合內容 （嵌入式管理單元的大小）  
  
- **DVEXTENT_INTEGRAL**在調整大小時，將建議的大小傳遞至控制項  
  
 `psizel`  
 若要調整控制項所傳回的資料點。 傳回的調整大小資料設定為-1 代表任何維度皆不進行調整。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功傳回，或調整大小;否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來傳回物件的顯示大小的建議的大小和範圍模式中最接近**DVEXTENTINFO**結構。 預設實作會傳回**FALSE**並不會調整大小。  
  
##  <a name="a-nameongetpredefinedstringsa--colecontrolongetpredefinedstrings"></a><a name="ongetpredefinedstrings"></a>COleControl::OnGetPredefinedStrings  
 取得一組預先定義的字串，代表屬性的可能值的架構所呼叫。  
  
```  
virtual BOOL OnGetPredefinedStrings(
    DISPID dispid,  
    CStringArray* pStringArray,  
    CDWordArray* pCookieArray);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 控制項屬性的分派識別碼。  
  
 `pStringArray`  
 若要在以填滿的字串陣列傳回的值。  
  
 `pCookieArray`  
 A`DWORD`以填入傳回值的陣列。  
  
### <a name="return-value"></a>傳回值  
 如果已加入項目為非零`pStringArray`和`pCookieArray`。  
  
### <a name="remarks"></a>備註  
 如果您的控制項具有一組可以用字串來表示的可能值的屬性會覆寫這個函式。 每個項目加入至`pStringArray`，您應該加入至對應的 「 cookie 」 項目*pCookieArray。* 這些 「 cookie 」 值稍後可以由架構傳遞`COleControl::OnGetPredefinedValue`函式。  
  
##  <a name="a-nameongetpredefinedvaluea--colecontrolongetpredefinedvalue"></a><a name="ongetpredefinedvalue"></a>COleControl::OnGetPredefinedValue  
 若要取得對應至其中一個預先定義的覆寫先前傳回的字串值架構呼叫`COleControl::OnGetPredefinedStrings`。  
  
```  
virtual BOOL OnGetPredefinedValue(
    DISPID dispid,  
    DWORD dwCookie,  
    VARIANT* lpvarOut);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 控制項屬性的分派識別碼。  
  
 `dwCookie`  
 先前的覆寫所傳回的 cookie 值`COleControl::OnGetPredefinedStrings`。  
  
 `lpvarOut`  
 指標**VARIANT**結構透過屬性值傳回。  
  
### <a name="return-value"></a>傳回值  
 如果有傳回值為非零`lpvarOut`，否則為 0。  
  
##  <a name="a-nameongetviewextenta--colecontrolongetviewextent"></a><a name="ongetviewextent"></a>COleControl::OnGetViewExtent  
 以回應容器的架構呼叫[IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032)要求。  
  
```  
virtual BOOL OnGetViewExtent(
    DWORD dwDrawAspect,
    LONG lindex,
    DVTARGETDEVICE* ptd,
    LPSIZEL lpsizel);
```  
  
### <a name="parameters"></a>參數  
 *dwDrawAspect*  
 `DWORD`描述哪些表單或外觀之外的物件便會顯示。 有效的值取自列舉[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)或**DVASPECT2**。  
  
 *lindex*  
 感興趣的物件部分。 目前只支援-1 是有效的。  
  
 `ptd`  
 指向[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)結構定義傳回的物件大小的目標裝置。  
  
 *lpsizel*  
 傳回物件大小的所在位置的指標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功傳回範圍資訊。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您的控制項使用兩次繪圖，且其不透明和透明的組件有不同的維度，請覆寫這個函式。  
  
##  <a name="a-nameongetviewrecta--colecontrolongetviewrect"></a><a name="ongetviewrect"></a>COleControl::OnGetViewRect  
 以回應容器的架構呼叫**IViewObjectEx::GetRect**要求。  
  
```  
virtual BOOL OnGetViewRect(DWORD dwAspect, LPRECTL pRect);
```  
  
### <a name="parameters"></a>參數  
 `dwAspect`  
 `DWORD`描述哪些表單或外觀之外的物件便會顯示。 有效的值取自列舉[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)或**DVASPECT2**:  
  
- `DVASPECT_CONTENT`整個物件週框。 在物件的來源與大小等於傳回的範圍的左上角**GetViewExtent***。*  
  
- **DVASPECT_OPAQUE**具有不透明的矩形區域的物件傳回的矩形。 其他失敗。  
  
- **DVASPECT_TRANSPARENT**涵蓋所有時間緊迫或透明部分的矩形。  
  
 `pRect`  
 指向[RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907)結構，指定應該在其中繪製物件的矩形。 此參數控制的定位和自動縮放的物件。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功傳回物件大小的矩形。否則為 0。  
  
### <a name="remarks"></a>備註  
 物件的大小由轉換`OnGetViewRect`到矩形，從特定位置 （預設為顯示畫面的左上的角）。 如果您的控制項使用兩次繪圖，且其不透明和透明的組件有不同的維度，請覆寫這個函式。  
  
##  <a name="a-nameongetviewstatusa--colecontrolongetviewstatus"></a><a name="ongetviewstatus"></a>COleControl::OnGetViewStatus  
 以回應容器的架構呼叫**IViewObjectEx::GetViewStatus**要求。  
  
```  
virtual DWORD OnGetViewStatus();
```  
  
### <a name="return-value"></a>傳回值  
 其中一個的值**forced VIEWSTATUS**列舉型別，如果成功，否則為 0。 值可以是下列任何組合︰  
  
 **VIEWSTATUS_OPAQUE**  
 物件是完全不透明的。 如果未設定此位元，物件會包含透明的組件。 這只適用於內容相關的層面和不`DVASPECT_ICON`或`DVASPECT_DOCPRINT`。  
  
 **VIEWSTATUS_SOLIDBKGND**  
 物件具有透明背景 （單色、 筆刷模式所組成）。 這個位元是有意義才**VIEWSTATUS_OPAQUE**設定，且只適用於內容相關的層面和不`DVASPECT_ICON`或`DVASPECT_DOCPRINT`。  
  
 **VIEWSTATUS_DVASPECTOPAQUE**  
 物件支援**DVASPECT_OPAQUE**。 所有**IViewObjectEx**需要繪製的外觀，因為參數可以呼叫這個層面的方法。  
  
 **VIEWSTATUS_DVASPECTTRANSPARENT**  
 物件支援**DVASPECT_TRANSPARENT**。 所有**IViewObjectEx**需要繪製的外觀，因為參數可以呼叫這個層面的方法。  
  
### <a name="remarks"></a>備註  
 如果您的控制項使用兩次繪圖，請覆寫這個函式。 預設實作會傳回**VIEWSTATUS_OPAQUE**。  
  
##  <a name="a-nameonhidetoolbarsa--colecontrolonhidetoolbars"></a><a name="onhidetoolbars"></a>COleControl::OnHideToolBars  
 停用的 UI 控制項時，由架構呼叫。  
  
```  
virtual void OnHideToolBars();
```  
  
### <a name="remarks"></a>備註  
 實作應該隱藏所有顯示的工具列`OnShowToolbars`。  
  
##  <a name="a-nameoninactivemousemovea--colecontroloninactivemousemove"></a><a name="oninactivemousemove"></a>COleControl::OnInactiveMouseMove  
 滑鼠指標在收到的非作用中物件的容器呼叫`WM_MOUSEMOVE`訊息。  
  
```  
virtual void OnInactiveMouseMove(
    LPCRECT lprcBounds,
    long x,
    long y,
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>參數  
 `lprcBounds`  
 週框矩形，包含視窗的用戶端座標中的物件。 在螢幕上的確切位置和大小告訴物件時`WM_MOUSEMOVE`收到的訊息。  
  
 *x*  
 用戶端座標中的滑鼠位置包含視窗的 x 座標。  
  
 *y*  
 用戶端座標中的滑鼠位置包含視窗的 y 座標。  
  
 `dwKeyState`  
 識別鍵盤輔助按鍵在鍵盤上的目前狀態。 有效的值可以是任何旗標的組合**MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_BUTTON**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
### <a name="remarks"></a>備註  
 請注意視窗工作區座標 （像素） 用來將滑鼠游標位置。 這麼做，可以藉由也在相同的座標系統中傳遞的物件，這個周框。  
  
##  <a name="a-nameoninactivesetcursora--colecontroloninactivesetcursor"></a><a name="oninactivesetcursor"></a>COleControl::OnInactiveSetCursor  
 滑鼠指標在收到的非作用中物件的容器呼叫`WM_SETCURSOR`訊息。  
  
```  
virtual BOOL OnInactiveSetCursor(
    LPCRECT lprcBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL bSetAlways);
```  
  
### <a name="parameters"></a>參數  
 `lprcBounds`  
 週框矩形，包含視窗的用戶端座標中的物件。 在螢幕上的確切位置和大小告訴物件時`WM_SETCURSOR`收到的訊息。  
  
 *x*  
 用戶端座標中的滑鼠位置包含視窗的 x 座標。  
  
 *y*  
 用戶端座標中的滑鼠位置包含視窗的 y 座標。  
  
 *dwMouseMsg*  
 要為其滑鼠訊息識別碼`WM_SETCURSOR`發生。  
  
 *bSetAlways*  
 指定物件必須設定資料指標。 如果**TRUE**，物件必須設定資料指標; 如果**FALSE**，資料指標並不需要設定資料指標，且應傳回**S_FALSE**這種情況下。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 請注意視窗工作區座標 （像素） 用來將滑鼠游標位置。 這麼做，可以藉由也在相同的座標系統中傳遞的物件，這個周框。  
  
##  <a name="a-nameonkeydowneventa--colecontrolonkeydownevent"></a><a name="onkeydownevent"></a>COleControl::OnKeyDownEvent  
 已處理的內建的 KeyDown 事件之後，由架構呼叫。  
  
```  
virtual void OnKeyDownEvent(
    USHORT nChar,  
    USHORT nShiftState);
```  
  
### <a name="parameters"></a>參數  
 `nChar`  
 按下的按鍵虛擬按鍵碼值。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.  
  
 `nShiftState`  
 包含下列旗標的組合︰  
  
- **SHIFT_MASK**動作期間按下 SHIFT 鍵。  
  
- **CTRL_MASK**動作期間按下 CTRL 鍵。  
  
- **ALT_MASK**動作期間按下 ALT 鍵。  
  
### <a name="remarks"></a>備註  
 如果控制項需要索引鍵資訊的存取權，在引發事件之後，請覆寫這個函式。  
  
##  <a name="a-nameonkeypresseventa--colecontrolonkeypressevent"></a><a name="onkeypressevent"></a>COleControl::OnKeyPressEvent  
 股票已經引發 KeyPress 事件之後，由框架呼叫。  
  
```  
virtual void OnKeyPressEvent(USHORT nChar);
```  
  
### <a name="parameters"></a>參數  
 `nChar`  
 包含虛擬按鍵碼值的按鍵。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.  
  
### <a name="remarks"></a>備註  
 請注意，`nChar`值可能已修改的容器。  
  
 如果您想要通知之後會發生此事件會覆寫這個函式。  
  
##  <a name="a-nameonkeyupeventa--colecontrolonkeyupevent"></a><a name="onkeyupevent"></a>COleControl::OnKeyUpEvent  
 已處理的內建的 KeyDown 事件之後，由架構呼叫。  
  
```  
virtual void OnKeyUpEvent(
    USHORT nChar,  
    USHORT nShiftState);
```  
  
### <a name="parameters"></a>參數  
 `nChar`  
 按下的按鍵虛擬按鍵碼值。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.  
  
 `nShiftState`  
 包含下列旗標的組合︰  
  
- **SHIFT_MASK**動作期間按下 SHIFT 鍵。  
  
- **CTRL_MASK**動作期間按下 CTRL 鍵。  
  
- **ALT_MASK**動作期間按下 ALT 鍵。  
  
### <a name="remarks"></a>備註  
 如果控制項需要索引鍵資訊的存取權，在引發事件之後，請覆寫這個函式。  
  
##  <a name="a-nameonmappropertytopagea--colecontrolonmappropertytopage"></a><a name="onmappropertytopage"></a>COleControl::OnMapPropertyToPage  
 若要取得實作指定的屬性編輯屬性頁面的類別識別碼架構呼叫。  
  
```  
virtual BOOL OnMapPropertyToPage(
    DISPID dispid,  
    LPCLSID lpclsid,  
    BOOL* pbPageOptional);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 控制項屬性的分派識別碼。  
  
 `lpclsid`  
 指標**CLSID**透過類別識別碼傳回的結構。  
  
 *pbPageOptional*  
 傳回使用指定的屬性頁面是否為選擇性的指標。  
  
### <a name="return-value"></a>傳回值  
 如果類別識別碼傳入為非零`lpclsid`，否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可提供方法來叫用從容器的屬性瀏覽器控制項的屬性頁。  
  
##  <a name="a-nameonmnemonica--colecontrolonmnemonic"></a><a name="onmnemonic"></a>COleControl::OnMnemonic  
 架構容器已偵測到已按下的 OLE 控制項的助憶鍵時呼叫。  
  
```  
virtual void OnMnemonic(LPMSG pMsg);
```  
  
### <a name="parameters"></a>參數  
 `pMsg`  
 助憶鍵 (Mnemonic) 按鍵所產生之 Windows 訊息的指標。  
  
##  <a name="a-nameonpropertiesa--colecontrolonproperties"></a><a name="onproperties"></a>COleControl::OnProperties  
 控制項的屬性動詞命令叫用後，容器會由架構呼叫。  
  
```  
virtual BOOL OnProperties(
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpMsg`  
 指標，叫用動詞命令的 Windows 訊息。  
  
 `hWndParent`  
 控制項的父視窗控制代碼。  
  
 `lpRect`  
 矩形容器中控制項所使用的指標。  
  
### <a name="return-value"></a>傳回值  
 如果呼叫成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會顯示強制回應屬性對話方塊。  
  
 您也可以使用此函式會造成您的控制項屬性頁的顯示。 呼叫`OnProperties`函式，將控制項的父代中的控制代碼傳遞`hWndParent`參數。 在此情況下，值`lpMsg`和`lpRect`參數都會被忽略。  
  
##  <a name="a-nameonqueryhitpointa--colecontrolonqueryhitpoint"></a><a name="onqueryhitpoint"></a>COleControl::OnQueryHitPoint  
 以回應容器的架構呼叫**IViewObjectEx::QueryHitPoint**要求。  
  
```  
virtual BOOL OnQueryHitPoint(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG lCloseHint,
    DWORD* pHitResult);
```  
  
### <a name="parameters"></a>參數  
 `dwAspect`  
 指定呈現物件的方法。 有效的值取自列舉[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)或**DVASPECT2**。  
  
 `pRectBounds`  
 指標`RECT`結構，指定 OLE 控制項的用戶端區域的周框矩形。  
  
 `ptlLoc`  
 指標**點**結構，指定要叫用檢查點。 OLE 用戶端區域座標中指定的點。  
  
 `lCloseHint`  
 定義 「 關閉 」 點檢查叫用的距離。  
  
 `pHitResult`  
 指標，叫用查詢的結果。 下列其中一個值：  
  
- **HITRESULT_OUTSIDE** `ptlLoc`是外部的 OLE 物件，並不會關閉。  
  
- **HITRESULT_TRANSPARENT** *ptlLoc*的 OLE 物件，但不是接近影像的界限內。 例如，可能是透明的圓點**HITRESULT_TRANSPARENT**。  
  
- **HITRESULT_CLOSE** `ptlLoc`是內部或外部的 OLE 物件，但夠關閉視為內部物件。 小型、 精簡，或詳細的物件可以使用此值。 即使點是外框矩形物件仍可能會關閉 （這所需達到的小型物件）。  
  
- **HITRESULT_HIT** `ptlLoc`內物件的映像。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功地傳回叫用的結果。否則為 0。 叫用是與 OLE 控制項顯示區域重疊。  
  
### <a name="remarks"></a>備註  
 查詢物件的顯示矩形是否與指定的點 （點擊點）。 `QueryHitPoint`您可以覆寫測試針對非矩形的物件。  
  
##  <a name="a-nameonqueryhitrecta--colecontrolonqueryhitrect"></a><a name="onqueryhitrect"></a>COleControl::OnQueryHitRect  
 以回應容器的架構呼叫**IViewObjectEx::QueryHitRect**要求。  
  
```  
virtual BOOL OnQueryHitRect(
    DWORD dwAspect,  
    LPCRECT pRectBounds,  
    LPCRECT prcLoc,  
    LONG lCloseHint,  
    DWORD* pHitResult);
```  
  
### <a name="parameters"></a>參數  
 `dwAspect`  
 指定物件要進行表示的方式。 有效的值取自列舉[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)或**DVASPECT2**。  
  
 `pRectBounds`  
 指標`RECT`結構，指定 OLE 控制項的用戶端區域的周框矩形。  
  
 *prcLoc*  
 指標`RECT`結構，指定要檢查，以叫用 （與物件矩形重疊），相對於物件的左上角的矩形。  
  
 `lCloseHint`  
 未使用。  
  
 `pHitResult`  
 指標，叫用查詢的結果。 下列其中一個值：  
  
- **HITRESULT_OUTSIDE**沒有點的矩形中叫用的 OLE 物件。  
  
- **HITRESULT_HIT**的矩形中至少一個點會在物件上的叫用。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功地傳回叫用的結果。否則為 0。  
  
### <a name="remarks"></a>備註  
 查詢物件的顯示矩形是否重疊的任何時間點指定的矩形 （點擊矩形）。 `QueryHitRect`您可以覆寫測試針對非矩形的物件。  
  
##  <a name="a-nameonrenderdataa--colecontrolonrenderdata"></a><a name="onrenderdata"></a>COleControl::OnRenderData  
 擷取指定之格式的資料架構所呼叫。  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定要求資訊的格式結構。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)資料所要傳回的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在控制項的物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)延遲轉譯為成員函式。 此函式的預設實作會呼叫`OnRenderFileData`或`OnRenderGlobalData`分別，如果提供的儲存體中的檔案或記憶體。 如果要求的格式為`CF_METAFILEPICT`或持續性的屬性集的格式，將適當的資料呈現的預設實作，並且傳回非零值。 否則，它會傳回 0，不做任何動作。  
  
 如果*-> tymed lpStgMedium*是**TYMED_NULL**、 **STGMEDIUM**應該配置及所指定的填滿*-> tymed lpFormatEtc*。 如果不是**TYMED_NULL**、 **STGMEDIUM**應填入的資料的位置。  
  
 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您的資料是小型且固定的大小，覆寫`OnRenderGlobalData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。  
  
 如需詳細資訊，請參閱**FORMATETC**和**STGMEDIUM**中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonrenderfiledataa--colecontrolonrenderfiledata"></a><a name="onrenderfiledata"></a>COleControl::OnRenderFileData  
 擷取指定之格式的資料儲存媒體檔案時架構呼叫。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定要求資訊的格式結構。  
  
 `pFile`  
 指向[CFile](../../mfc/reference/cfile-class.md)裡面的資料是要呈現的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在控制項的物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫`OnRenderData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。  
  
 如需詳細資訊，請參閱**FORMATETC**結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonrenderglobaldataa--colecontrolonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleControl::OnRenderGlobalData  
 擷取指定的格式中的資料，當指定的儲存體中的全域記憶體架構所呼叫。  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定要求資訊的格式結構。  
  
 `phGlobal`  
 指向資料所要傳回的全域記憶體的控制代碼。 如果已不配置任何記憶體，這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在控制項的物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 如果`phGlobal`是**NULL**，然後新`HGLOBAL`應該配置並傳回`phGlobal`。 否則，`HGLOBAL`所指定`phGlobal`應該填入資料。 資料量放在`HGLOBAL`不能超過目前的記憶體區塊大小。 此外，無法重新配置較大的區塊。  
  
 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫`OnRenderData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。  
  
 如需詳細資訊，請參閱**FORMATETC**結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonresetstatea--colecontrolonresetstate"></a><a name="onresetstate"></a>COleControl::OnResetState  
 當控制項的屬性應該設為其預設值，由架構呼叫。  
  
```  
virtual void OnResetState();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[DoPropExchange](#dopropexchange)，傳遞`CPropExchange`會導致屬性設為其預設值的物件。  
  
 控制寫入器可以在此插入 OLE 控制項的初始化程式碼可覆寫。 此函式時，會呼叫[ipersiststream:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680568)或[ipersiststorage:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680557)失敗，或[IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234)或[IPersistStorage::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194)呼叫，而不第一個呼叫**ipersiststream:: Load**或**ipersiststorage:: Load**。  
  
##  <a name="a-nameonsetclientsitea--colecontrolonsetclientsite"></a><a name="onsetclientsite"></a>Colecontrol:: Onsetclientsite  
 容器控制項的呼叫時，由框架呼叫**IOleControl::SetClientSite**函式。  
  
```  
virtual void OnSetClientSite();
```  
  
### <a name="remarks"></a>備註  
 根據預設，`OnSetClientSite`會檢查是否載入資料路徑屬性，而如果有需要，會呼叫`DoDataPathPropExchange`。  
  
 覆寫這個函式來執行這項通知的任何特殊處理。 特別是，此函式的覆寫應呼叫基底類別。  
  
##  <a name="a-nameonsetdataa--colecontrolonsetdata"></a><a name="onsetdata"></a>COleControl::OnSetData  
 使用指定的資料取代控制項的資料架構所呼叫。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構指定的資料格式。  
  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)資料所在的結構。  
  
 `bRelease`  
 **TRUE**如果控制項應該釋出儲存媒體中;**FALSE**如果控制項應該釋出儲存媒體。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果資料持續性的屬性中設定格式，預設實作會據以修改控制項的狀態。 否則，預設實作會沒有作用。 如果`bRelease`是**TRUE**，然後呼叫**ReleaseStgMedium**為止; 否則為 not。  
  
 覆寫這個函式，以取代指定之資料的控制項的資料。  
  
 如需詳細資訊，請參閱**FORMATETC**和**STGMEDIUM**中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonsetextenta--colecontrolonsetextent"></a><a name="onsetextent"></a>COleControl::OnSetExtent  
 需要變更，由於呼叫控制項的寬度，由框架呼叫[IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330)。  
  
```  
virtual BOOL OnSetExtent(LPSIZEL lpSizeL);
```  
  
### <a name="parameters"></a>參數  
 `lpSizeL`  
 指標**大小**使用長整數來代表控制項，以表示高度與寬度的結構**HIMETRIC**單位。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已接受的大小變更。否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會處理控制項的寬度調整大小。 如果控制項是就地啟用作用中，容器的呼叫**OnPosRectChanged**再進行。  
  
 覆寫這個函式來變更控制項的預設調整大小。  
  
##  <a name="a-nameonsetobjectrectsa--colecontrolonsetobjectrects"></a><a name="onsetobjectrects"></a>COleControl::OnSetObjectRects  
 若要實作的呼叫架構呼叫[IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767)。  
  
```  
virtual BOOL OnSetObjectRects(
    LPCRECT lpRectPos,  
    LPCRECT lpRectClip);
```  
  
### <a name="parameters"></a>參數  
 *lpRectPos*  
 表示控制項的新位置和大小，相對於容器 RECT 結構的指標。  
  
 `lpRectClip`  
 指標`RECT`結構，表示控制項是裁剪的矩形區域。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已接受重新定位。否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會自動重新定位和控制項視窗的調整大小控點，並傳回**TRUE**。  
  
 覆寫這個函式來變更此函式的預設行為。  
  
##  <a name="a-nameonshowtoolbarsa--colecontrolonshowtoolbars"></a><a name="onshowtoolbars"></a>COleControl::OnShowToolBars  
 當已經啟用的 UI 控制項，由架構呼叫。  
  
```  
virtual void OnShowToolBars();
```  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。  
  
##  <a name="a-nameontextchangeda--colecontrolontextchanged"></a><a name="ontextchanged"></a>COleControl::OnTextChanged  
 內建的標題或文字屬性值變更時，由架構呼叫。  
  
```  
virtual void OnTextChanged();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`InvalidateControl`。  
  
 如果您要通知之後，這個屬性會變更，請覆寫這個函式。  
  
##  <a name="a-nameonwindowlessmessagea--colecontrolonwindowlessmessage"></a><a name="onwindowlessmessage"></a>COleControl::OnWindowlessMessage  
 以回應容器的架構呼叫**IOleInPlaceObjectWindowless::OnWindowMessage**要求。  
  
```  
virtual BOOL OnWindowlessMessage(
    UINT msg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```  
  
### <a name="parameters"></a>參數  
 `msg`  
 Windows 所傳送的訊息識別碼。  
  
 `wParam`  
 Windows 所傳送。 指定特定訊息的其他資訊。 此參數的內容而定的值`msg`參數。  
  
 `lParam`  
 Windows 所傳送。 指定特定訊息的其他資訊。 此參數的內容而定的值`msg`參數。  
  
 *plResult*  
 Windows 結果碼。 指定結果的訊息處理和傳送的訊息而定。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 處理無視窗控制項的視窗訊息。 `COleControl``OnWindowlessMessage`應該用於訊息滑鼠和鍵盤訊息以外的視窗訊息。 `COleControl`提供[SetCapture](#setcapture)和[SetFocus](#setfocus)來取得無視窗的 OLE 物件的滑鼠捕捉和鍵盤焦點。  
  
 無視窗物件沒有視窗，因為他們需要一種機制，讓容器分派訊息給他們。 無視窗的 OLE 物件取得訊息其容器中，透過`OnWindowMessage`方法`IOleInPlaceObjectWindowless`介面 (副檔名為[IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646)支援無視窗)。 `OnWindowMessage`不接受`HWND`參數。  
  
##  <a name="a-nameparenttoclienta--colecontrolparenttoclient"></a><a name="parenttoclient"></a>COleControl::ParentToClient  
 將轉譯的座標`pPoint`到工作區座標。  
  
```  
virtual UINT ParentToClient(
    LPCRECT lprcBounds,
    LPPOINT pPoint,
    BOOL bHitTest = FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 `lprcBounds`  
 OLE 控制項容器中的界限的指標。 非工作區，但整個控制項包括框線和捲軸的區域。  
  
 `pPoint`  
 轉譯控制項的用戶端區域的座標為指向父 （容器） 的指標。  
  
 `bHitTest`  
 指定點擊測試執行的點上。  
  
### <a name="return-value"></a>傳回值  
 如果`bHitTest`是**FALSE**，傳回**HTNOWHERE**。 如果`bHitTest`是**TRUE**、 傳回登陸 OLE 控制項的工作區中的父代 （容器） 點所在的位置，而且是其中一個下列滑鼠點擊測試的值︰  
  
- **HTBORDER**中並沒有縮放邊框之視窗的框線。  
  
- **HTBOTTOM**中較低的水平框線的視窗。  
  
- **HTBOTTOMLEFT**左下角的視窗框線。  
  
- **HTBOTTOMRIGHT**右下角的視窗框線。  
  
- **HTCAPTION**標題列區域中。  
  
- **HTCLIENT**工作區中。  
  
- **HTERROR**螢幕背景或視窗之間的分隔線 (相同**HTNOWHERE**不同之處在於**DefWndProc** Windows 函式會產生系統嗶聲，表示錯誤)。  
  
- **HTGROWBOX**大小 方塊中。  
  
- **HTHSCROLL**水平捲軸。  
  
- **HTLEFT**在視窗的左框線。  
  
- **HTMAXBUTTON**中最大化 按鈕。  
  
- **HTMENU**功能表區域中。  
  
- **HTMINBUTTON**中最小化 按鈕。  
  
- **HTNOWHERE**螢幕背景或視窗之間的分隔線。  
  
- **HTREDUCE**中最小化 按鈕。  
  
- **HTRIGHT**在視窗的右框線。  
  
- **HTSIZE**大小 方塊中 (相同**HTGROWBOX**)。  
  
- **HTSYSMENU**控制 功能表或 關閉 按鈕中的子視窗。  
  
- **HTTOP**中的視窗水平框線。  
  
- **HTTOPLEFT**左上角的視窗框線。  
  
- **HTTOPRIGHT**右上角的視窗框線。  
  
- **HTTRANSPARENT**中目前所涵蓋的另一個視窗的視窗。  
  
- **HTVSCROLL**垂直捲軸。  
  
- **HTZOOM**中最大化 按鈕。  
  
### <a name="remarks"></a>備註  
 在輸入`pPoint`相對於父系 （左上角的容器） 的原點。 在輸出`pPoint`相對於來源的 OLE 控制項 （左上角之控制項的工作區） 的工作區。  
  
##  <a name="a-namepostmodaldialoga--colecontrolpostmodaldialog"></a><a name="postmodaldialog"></a>COleControl::PostModalDialog  
 告知容器已關閉強制回應對話方塊。  
  
```  
void PostModalDialog(HWND hWndParent = NULL);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 強制回應對話方塊的父視窗的控制代碼。  
  
### <a name="remarks"></a>備註  
 顯示任何強制回應對話方塊之後，呼叫此函式。 您必須呼叫此函式，以便讓容器可以啟用停用任何最上層視窗`PreModalDialog`。 此函式應該搭配呼叫`PreModalDialog`。  
  
##  <a name="a-namepremodaldialoga--colecontrolpremodaldialog"></a><a name="premodaldialog"></a>COleControl::PreModalDialog  
 通知即將顯示強制回應對話方塊的容器。  
  
```  
void PreModalDialog(HWND hWndParent = NULL);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 強制回應對話方塊的父視窗的控制代碼。  
  
### <a name="remarks"></a>備註  
 顯示任何強制回應對話方塊之前呼叫此函式。 您必須呼叫此函式，讓容器可以停用所有最上層的視窗。 已顯示強制回應對話方塊後，然後您必須呼叫`PostModalDialog`。  
  
##  <a name="a-namerecreatecontrolwindowa--colecontrolrecreatecontrolwindow"></a><a name="recreatecontrolwindow"></a>COleControl::RecreateControlWindow  
 終結並重新建立控制項的視窗。  
  
```  
void RecreateControlWindow();
```  
  
### <a name="remarks"></a>備註  
 這可能需要變更視窗的樣式位元。  
  
##  <a name="a-namerefresha--colecontrolrefresh"></a><a name="refresh"></a>COleControl::Refresh  
 強制重新繪製 OLE 控制項。  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>備註  
 此函式支援`COleControl`基底類別，做為內建的方法，稱為 「 重新整理。 這可讓 OLE 控制項的使用者在特定時間重新繪製控制項。 如需有關這個方法的詳細資訊，請參閱文章[ActiveX 控制項︰ 方法](../../mfc/mfc-activex-controls-methods.md)。  
  
##  <a name="a-namereleasecapturea--colecontrolreleasecapture"></a><a name="releasecapture"></a>COleControl::ReleaseCapture  
 釋放滑鼠捕捉。  
  
```  
BOOL ReleaseCapture();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果控制項目前具有滑鼠捕捉，則會釋放擷取。 否則，此函式沒有任何作用。  
  
##  <a name="a-namereleasedca--colecontrolreleasedc"></a><a name="releasedc"></a>COleControl::ReleaseDC  
 釋放容器釋放裝置內容，供其他應用程式的無視窗控制項的顯示裝置內容。  
  
```  
int ReleaseDC(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 識別要釋放的容器裝置內容。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式必須呼叫`ReleaseDC`每次呼叫[GetDC](#getdc)。  
  
##  <a name="a-namereparentcontrolwindowa--colecontrolreparentcontrolwindow"></a><a name="reparentcontrolwindow"></a>COleControl::ReparentControlWindow  
 設定控制項的父代。  
  
```  
virtual void ReparentControlWindow(
    HWND hWndOuter,  
    HWND hWndParent);
```  
  
### <a name="parameters"></a>參數  
 *hWndOuter*  
 控制項視窗的控制代碼。  
  
 `hWndParent`  
 新的父視窗的控制代碼。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來重設控制項視窗的父代。  
  
##  <a name="a-nameresetstockpropsa--colecontrolresetstockprops"></a><a name="resetstockprops"></a>COleControl::ResetStockProps  
 初始化的狀態`COleControl`內建屬性設為預設值。  
  
```  
void ResetStockProps();
```  
  
### <a name="remarks"></a>備註  
 屬性是︰ 外觀、 背景色彩、 框線樣式、 標題、 啟用、 字型、 前景色彩、 hWnd 和文字。 如需內建屬性的說明，請參閱[ActiveX 控制項︰ 加入內建屬性](../../mfc/mfc-activex-controls-adding-stock-properties.md)。  
  
 您可以使用，以改善控制項的二進位初始化效能`ResetStockProps`和`ResetVersion`覆寫`COleControl::OnResetState`。 請參閱下列範例。 如需最佳化初始化的詳細資訊，請參閱[ActiveX 控制項︰ 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAxCtl #&7;](../../mfc/reference/codesnippet/cpp/colecontrol-class_8.cpp)]  
  
##  <a name="a-nameresetversiona--colecontrolresetversion"></a><a name="resetversion"></a>COleControl::ResetVersion  
 初始化指定的值的版本號碼。  
  
```  
void ResetVersion(DWORD dwVersionDefault);
```  
  
### <a name="parameters"></a>參數  
 `dwVersionDefault`  
 要指派給控制項的版本號碼。  
  
### <a name="remarks"></a>備註  
 您可以使用，以改善控制項的二進位初始化效能`ResetVersion`和`ResetStockProps`覆寫`COleControl::OnResetState`。 請參閱範例[ResetStockProps](#resetstockprops)。 如需最佳化初始化的詳細資訊，請參閱[ActiveX 控制項︰ 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
##  <a name="a-namescrollwindowa--colecontrolscrollwindow"></a><a name="scrollwindow"></a>COleControl::ScrollWindow  
 允許捲動螢幕上它就地使用中映像內的區域無視窗的 OLE 物件。  
  
```  
void ScrollWindow(
    int xAmount,
    int yAmount,
    LPCRECT lpRect = NULL,
    LPCRECT lpClipRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 `xAmount`  
 指定數量的水平捲軸的裝置單位。 這個參數必須為負值，向左捲動。  
  
 `yAmount`  
 以裝置為單位，垂直捲動的指定單位的數量。 這個參數必須是負值向上捲動。  
  
 `lpRect`  
 指向[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或 RECT 結構，包含視窗的用戶端座標中指定的部分捲動時，OLE 物件的工作區。 如果`lpRect`是**NULL**，捲動整個 OLE 物件的工作區。  
  
 `lpClipRect`  
 指向`CRect`物件或`RECT`結構，指定要剪輯的矩形。 將捲動的矩形內的像素。 即使是在矩形外的位元不受影響`lpRect`矩形。 如果`lpClipRect`是**NULL**，捲軸的矩形不會對不裁剪。  
  
##  <a name="a-nameselectfontobjecta--colecontrolselectfontobject"></a><a name="selectfontobject"></a>COleControl::SelectFontObject  
 選取放入裝置內容中的字型。  
  
```  
CFont* SelectFontObject(
    CDC* pDC,  
    CFontHolder& fontHolder);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容物件的指標。  
  
 `fontHolder`  
 若要參考[CFontHolder](../../mfc/reference/cfontholder-class.md)物件，代表選取的字型。  
  
### <a name="return-value"></a>傳回值  
 指標，先前選取的字型。 呼叫端已經完成使用的所有繪圖作業時*fontHolder，*它應該藉由傳遞做為參數重新選取先前選取的字型[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)。  
  
##  <a name="a-nameselectstockfonta--colecontrolselectstockfont"></a><a name="selectstockfont"></a>COleControl::SelectStockFont  
 選取放入裝置內容中的內建字型屬性。  
  
```  
CFont* SelectStockFont(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容會在其中選取字型。  
  
### <a name="return-value"></a>傳回值  
 先前選取的指標`CFont`物件。 您應該使用[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)完成時，這種字型選取回裝置內容。  
  
##  <a name="a-nameserializeextenta--colecontrolserializeextent"></a><a name="serializeextent"></a>COleControl::SerializeExtent  
 序列化或初始化配置給控制項的顯示空間的狀態。  
  
```  
void SerializeExtent(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 A`CArchive`来序列化或從物件。  
  
### <a name="remarks"></a>備註  
 您可以使用，以改善控制項的二進位的持續性效能`SerializeExtent`， `SerializeStockProps`，和`SerializeVersion`覆寫**COleControl::Serialize**。 請參閱下列範例。 如需最佳化初始化的詳細資訊，請參閱[ActiveX 控制項︰ 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAxCtl #&8;](../../mfc/reference/codesnippet/cpp/colecontrol-class_9.cpp)]  
  
##  <a name="a-nameserializestockpropsa--colecontrolserializestockprops"></a><a name="serializestockprops"></a>COleControl::SerializeStockProps  
 序列化或初始化的狀態`COleControl`內建屬性︰ 外觀、 背景色彩、 框線樣式、 標題、 啟用、 字型、 前景色彩和文字。  
  
```  
void SerializeStockProps(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 A`CArchive`来序列化或從物件。  
  
### <a name="remarks"></a>備註  
 如需內建屬性的說明，請參閱[ActiveX 控制項︰ 加入內建屬性](../../mfc/mfc-activex-controls-adding-stock-properties.md)。  
  
 您可以使用，以改善控制項的二進位的持續性效能`SerializeStockProps`， `SerializeExtent`，和`SerializeVersion`覆寫**COleControl::Serialize**。 如需範例，請參閱位於程式碼[SerializeExtent](#serializeextent)。 如需最佳化初始化的詳細資訊，請參閱[ActiveX 控制項︰ 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
##  <a name="a-nameserializeversiona--colecontrolserializeversion"></a><a name="serializeversion"></a>COleControl::SerializeVersion  
 序列化或初始化控制項的版本資訊的狀態。  
  
```  
DWORD SerializeVersion(
    CArchive& ar,
    DWORD dwVersionDefault,
    BOOL bConvert = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 A`CArchive`来序列化或從物件。  
  
 `dwVersionDefault`  
 控制項的目前版本號碼。  
  
 `bConvert`  
 指出是否持續性資料應轉換成最新的格式儲存，或保留在相同的格式時載入時。  
  
### <a name="return-value"></a>傳回值  
 控制版本號碼。 如果載入指定的封存，`SerializeVersion`傳回載入從該保存的版本。 否則，它會傳回目前載入的版本。  
  
### <a name="remarks"></a>備註  
 您可以使用，以改善控制項的二進位的持續性效能`SerializeVersion`， `SerializeExtent`，和`SerializeStockProps`覆寫**COleControl::Serialize**。 如需範例，請參閱位於程式碼[SerializeExtent](#serializeextent)。 如需最佳化初始化的詳細資訊，請參閱[ActiveX 控制項︰ 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
##  <a name="a-namesetappearancea--colecontrolsetappearance"></a><a name="setappearance"></a>COleControl::SetAppearance  
 設定控制項的內建的外觀屬性值。  
  
```  
void SetAppearance (short sAppearance);
```  
  
### <a name="parameters"></a>參數  
 *sAppearance*  
 A**簡短**( `VT_I2`) 值，以用於控制項的外觀。 零值以一般設定控制項的外觀，值為 1 到 3D 設定控制項的外觀。  
  
### <a name="remarks"></a>備註  
 如需關於內建屬性的詳細資訊，請參閱[ActiveX 控制項︰ 屬性](../../mfc/mfc-activex-controls-properties.md)。  
  
##  <a name="a-namesetbackcolora--colecontrolsetbackcolor"></a><a name="setbackcolor"></a>COleControl::SetBackColor  
 設定控制項的內建的背景色彩屬性值。  
  
```  
void SetBackColor(OLE_COLOR dwBackColor);
```  
  
### <a name="parameters"></a>參數  
 *dwBackColor*  
 **OLE_COLOR**繪製控制項的背景使用的值。  
  
### <a name="remarks"></a>備註  
 如需有關使用此屬性和其他相關屬性，請參閱文章[ActiveX 控制項︰ 屬性](../../mfc/mfc-activex-controls-properties.md)。  
  
##  <a name="a-namesetborderstylea--colecontrolsetborderstyle"></a><a name="setborderstyle"></a>COleControl::SetBorderStyle  
 設定控制項的內建的框線樣式屬性值。  
  
```  
void SetBorderStyle(short sBorderStyle);
```  
  
### <a name="parameters"></a>參數  
 *sBorderStyle*  
 新框線樣式的控制項。0 表示沒有框線，而 1 表示一般的框線。  
  
### <a name="remarks"></a>備註  
 [控制] 視窗會重新建立和`OnBorderStyleChanged`呼叫。  
  
##  <a name="a-namesetcapturea--colecontrolsetcapture"></a><a name="setcapture"></a>COleControl::SetCapture  
 會使控制項的容器視窗才能代替控制項的滑鼠捕捉的所有權。  
  
```  
CWnd* SetCapture();
```  
  
### <a name="return-value"></a>傳回值  
 指標**CWnd**先前接收到滑鼠輸入的視窗物件。  
  
### <a name="remarks"></a>備註  
 如果已啟動並無視窗控制項，這個函式會導致才能擁有滑鼠捕捉，代表控制項的控制項的容器視窗。 否則，這個函式會導致控制項本身需要持有的滑鼠捕捉 (相同`CWnd::SetCapture`)。  
  
##  <a name="a-namesetcontrolsizea--colecontrolsetcontrolsize"></a><a name="setcontrolsize"></a>COleControl::SetControlSize  
 設定 OLE 控制項視窗的大小，並通知控制項站台正在變更的容器。  
  
```  
BOOL SetControlSize(int cx, int cy);
```  
  
### <a name="parameters"></a>參數  
 `cx`  
 指定新控制項的寬度，單位為像素。  
  
 `cy`  
 指定新控制項的高度，單位為像素。  
  
### <a name="return-value"></a>傳回值  
 如果呼叫成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式不應該用於控制項的建構函式。  
  
 請注意，用於控制 windows 的所有座標都是相對於控制項的左上角。  
  
##  <a name="a-namesetenableda--colecontrolsetenabled"></a><a name="setenabled"></a>COleControl::SetEnabled  
 設定內建控制項的 Enabled 屬性值。  
  
```  
void SetEnabled(BOOL bEnabled);
```  
  
### <a name="parameters"></a>參數  
 `bEnabled`  
 **TRUE**控制項是否已啟用，否則為**FALSE**。  
  
### <a name="remarks"></a>備註  
 設定這個屬性之後, **OnEnabledChange**呼叫。  
  
##  <a name="a-namesetfocusa--colecontrolsetfocus"></a><a name="setfocus"></a>COleControl::SetFocus  
 會使控制項的容器視窗，才能擁有輸入焦點的控制項的代表。  
  
```  
CWnd* SetFocus();
```  
  
### <a name="return-value"></a>傳回值  
 指標**CWnd**先前擁有輸入的焦點的視窗物件或**NULL**如果沒有這類的時段。  
  
### <a name="remarks"></a>備註  
 如果已啟動並無視窗控制項，這個函式會導致才能擁有輸入焦點，代表控制項的控制項的容器視窗。 輸入的焦點引導至容器的視窗的鍵盤輸入和容器會分派給呼叫的 OLE 物件的所有待處理鍵盤訊息`SetFocus`。 任何先前擁有輸入的焦點的視窗會失去它。  
  
 如果控制項不是無視窗，這個函式會導致控制項本身需要擁有輸入焦點 (相同`CWnd::SetFocus`)。  
  
##  <a name="a-namesetfonta--colecontrolsetfont"></a><a name="setfont"></a>COleControl::SetFont  
 設定控制項的內建字型屬性。  
  
```  
void SetFont(LPFONTDISP pFontDisp);
```  
  
### <a name="parameters"></a>參數  
 *pFontDisp*  
 字型的分派介面指標。  
  
##  <a name="a-namesetforecolora--colecontrolsetforecolor"></a><a name="setforecolor"></a>COleControl::SetForeColor  
 設定控制項的內建的前景色彩屬性值。  
  
```  
void SetForeColor(OLE_COLOR dwForeColor);
```  
  
### <a name="parameters"></a>參數  
 *dwForeColor*  
 **OLE_COLOR**用於繪製控制項的前景的值。  
  
### <a name="remarks"></a>備註  
 如需有關使用此屬性和其他相關屬性，請參閱文章[ActiveX 控制項︰ 屬性](../../mfc/mfc-activex-controls-properties.md)。  
  
##  <a name="a-namesetinitialdataformatsa--colecontrolsetinitialdataformats"></a><a name="setinitialdataformats"></a>COleControl::SetInitialDataFormats  
 初始化控制項支援的資料格式的清單架構呼叫。  
  
```  
virtual void SetInitialDataFormats();
```  
  
### <a name="remarks"></a>備註  
 預設實作會指定兩種格式︰`CF_METAFILEPICT`和持續性的屬性集。  
  
##  <a name="a-namesetinitialsizea--colecontrolsetinitialsize"></a><a name="setinitialsize"></a>COleControl::SetInitialSize  
 設定 OLE 控制項容器中第一次顯示時的大小。  
  
```  
void SetInitialSize(
    int cx,  
    int cy);
```  
  
### <a name="parameters"></a>參數  
 `cx`  
 OLE 控制項，單位為像素的初始寬度。  
  
 `cy`  
 OLE 控制項，單位為像素的初始高度。  
  
### <a name="remarks"></a>備註  
 若要設定控制項的初始大小您建構函式中呼叫此函式。 以裝置單位或像素為單位的初始大小。 建議您控制項的建構函式中進行這個呼叫。  
  
##  <a name="a-namesetmodifiedflaga--colecontrolsetmodifiedflag"></a><a name="setmodifiedflag"></a>COleControl::SetModifiedFlag  
 變更控制項的已修改的狀態。  
  
```  
void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bModified`  
 控制項的新值的修改旗標。 **TRUE**指出已經修改控制項的狀態。**FALSE**表示只儲存控制項的狀態。  
  
### <a name="remarks"></a>備註  
 呼叫此函式發生變更時，會影響控制項的永續性狀態。 例如，如果持續性屬性的值變更時，呼叫此函式`bModified` **TRUE**。  
  
##  <a name="a-namesetnotpermitteda--colecontrolsetnotpermitted"></a><a name="setnotpermitted"></a>Colecontrol:: Setnotpermitted  
 表示編輯要求已失敗。  
  
```  
void SetNotPermitted();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式時`BoundPropertyRequestEdit`失敗。 此函式會擲回例外狀況型別**COleDispScodeException**來表示，不允許設定作業。  
  
##  <a name="a-namesetnotsupporteda--colecontrolsetnotsupported"></a><a name="setnotsupported"></a>Colecontrol:: Setnotsupported  
 防止使用者控制項的屬性值的修改。  
  
```  
void SetNotSupported();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個函式取代任何屬性的 Set 函式不支援修改控制項的使用者屬性值的位置。 範例會唯讀的屬性。  
  
##  <a name="a-namesetrectincontainera--colecontrolsetrectincontainer"></a><a name="setrectincontainer"></a>COleControl::SetRectInContainer  
 設定相對於容器，以裝置單位來表示控制項的矩形座標。  
  
```  
BOOL SetRectInContainer(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 矩形，包含控制項的新的座標相對於容器指標。  
  
### <a name="return-value"></a>傳回值  
 如果呼叫成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果控制項已開啟，它會調整大小;否則容器的**OnPosRectChanged**函式呼叫。  
  
##  <a name="a-namesettexta--colecontrolsettext"></a><a name="settext"></a>COleControl::SetText  
 設定控制項的內建的標題或文字屬性的值。  
  
```  
void SetText(LPCTSTR pszText);
```  
  
### <a name="parameters"></a>參數  
 `pszText`  
 字元字串指標。  
  
### <a name="remarks"></a>備註  
 請注意，內建的標題和文字屬性會對應到相同的值。 這表示任一屬性所做的變更將會自動變更這兩個屬性。 一般情況下，控制項應該支援內建的標題或 Text 屬性，但不可同時。  
  
##  <a name="a-namethrowerrora--colecontrolthrowerror"></a><a name="throwerror"></a>Colecontrol:: Throwerror  
 表示控制項中的錯誤次數。  
  
```  
void ThrowError(
    SCODE sc,  
    UINT nDescriptionID,  
    UINT nHelpID = -1);

 
void ThrowError(
    SCODE sc,  
    LPCTSTR pszDescription = NULL,  
    UINT nHelpID = 0);
```  
  
### <a name="parameters"></a>參數  
 `sc`  
 要報告的狀態碼值。 如需可能的程式碼的完整清單，請參閱文章[ActiveX 控制項︰ 進階主題](../../mfc/mfc-activex-controls-advanced-topics.md)。  
  
 `nDescriptionID`  
 字串資源識別碼例外狀況的報告。  
  
 `nHelpID`  
 要報告的主題說明識別碼。  
  
 `pszDescription`  
 字串，包含要報告的例外狀況的說明。  
  
### <a name="remarks"></a>備註  
 此函式應該只從呼叫 Get 或 Set 函式內 OLE 屬性，或 OLE automation 方法的實作。 如果您需要通知其他時間發生的錯誤，您應該會引發內建的錯誤事件。  
  
##  <a name="a-nametransformcoordsa--colecontroltransformcoords"></a><a name="transformcoords"></a>COleControl::TransformCoords  
 轉換座標之間的值**HIMETRIC**單位和容器的原生的單位。  
  
```  
void TransformCoords(
    POINTL* lpptlHimetric,  
    POINTF* lpptfContainer,  
    DWORD flags);
```  
  
### <a name="parameters"></a>參數  
 *lpptlHimetric*  
 指標**POINTL**結構，其中包含在座標**HIMETRIC**單位。  
  
 *lpptfContainer*  
 指標**POINTF**結構包含容器的單位大小的座標。  
  
 `flags`  
 下列值的組合︰  
  
- **XFORMCOORDS_POSITION**容器中的位置。  
  
- **XFORMCOORDS_SIZE**容器中的大小。  
  
- **XFORMCOORDS_HIMETRICTOCONTAINER**轉換**HIMETRIC**單位為容器的單位。  
  
- **XFORMCOORDS_CONTAINERTOHIMETRIC**轉換容器的單位**HIMETRIC**單位。  
  
### <a name="remarks"></a>備註  
 前兩個旗標， **XFORMCOORDS_POSITION**和**XFORMCOORDS_SIZE**，指出是否應該將座標視為位置或大小。 其餘的兩個旗標會指出轉換的方向。  
  
##  <a name="a-nametranslatecolora--colecontroltranslatecolor"></a><a name="translatecolor"></a>COleControl::TranslateColor  
 將轉換的色彩值**OLE_COLOR**資料型別[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)資料型別。  
  
```  
COLORREF TranslateColor(
    OLE_COLOR clrColor,  
    HPALETTE hpal = NULL);
```  
  
### <a name="parameters"></a>參數  
 `clrColor`  
 A **OLE_COLOR**資料型別。 如需詳細資訊，請參閱 Windows [OleTranslateColor](http://msdn.microsoft.com/library/windows/desktop/ms694353)函式。  
  
 `hpal`  
 選擇性的調色盤; 的控制代碼可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 定義穩固的 RGB （紅色、 綠色、 藍色） 32 位元色彩值色彩最接近`clrColor`裝置可以表示的值。  
  
### <a name="remarks"></a>備註  
 此函式可以轉譯至內建的前景色彩和背景色彩屬性**COLORREF**所使用的類型[CDC](../../mfc/reference/cdc-class.md)成員函式。  
  
##  <a name="a-namewillambientsbevalidduringloada--colecontrolwillambientsbevalidduringload"></a><a name="willambientsbevalidduringload"></a>COleControl::WillAmbientsBeValidDuringLoad  
 決定您的控制項後續載入從持續性的狀態時，是否應該使用的環境屬性的值做為預設值。  
  
```  
BOOL WillAmbientsBeValidDuringLoad();
```  
  
### <a name="return-value"></a>傳回值  
 非零代表環境屬性將會有效。否則環境屬性就不會有效。  
  
### <a name="remarks"></a>備註  
 在某些容器中，您的控制項可能沒有存取其環境屬性的覆寫的初始呼叫期間`COleControl::DoPropExchange`。 如果容器呼叫是如此[IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730)或[ipersiststorage:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680557)之前呼叫[IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) (也就是說，如果不接受**OLEMISC_SETCLIENTSITEFIRST**狀態位元)。  
  
##  <a name="a-namewindowproca--colecontrolwindowproc"></a><a name="windowproc"></a>COleControl::WindowProc  
 提供的 Windows 處理程序`COleControl`物件。  
  
```  
virtual LRESULT WindowProc(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `message`  
 指定要處理 Windows 訊息。  
  
 `wParam`  
 提供用於處理訊息的其他資訊。 參數值取決於訊息。  
  
 `lParam`  
 提供用於處理訊息的其他資訊。 參數值取決於訊息。  
  
### <a name="return-value"></a>傳回值  
 發送的訊息傳回的值。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可將特定訊息透過控制項的訊息對應分派。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CIRC3](../../visual-cpp-samples.md)   
 [MFC 範例 TESTHELP](../../visual-cpp-samples.md)   
 [COlePropertyPage 類別](../../mfc/reference/colepropertypage-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFontHolder 類別](../../mfc/reference/cfontholder-class.md)   
 [CPictureHolder 類別](../../mfc/reference/cpictureholder-class.md)

