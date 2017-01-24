---
title: "COleControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControl class"
  - "控制項 [MFC], OLE"
  - "控制項 [MFC], windowless"
  - "OLE 控制項, MFC"
  - "windowless controls"
  - "windowless controls, MFC"
ms.assetid: 53e95299-38e8-447b-9c5f-a381d27f5123
caps.latest.revision: 25
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開發的 OLE 控制項的功能強大的基底類別。  
  
## 語法  
  
```  
class COleControl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleControl::COleControl](../Topic/COleControl::COleControl.md)|建立 `COleControl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleControl::AmbientAppearance](../Topic/COleControl::AmbientAppearance.md)|擷取目前控制項的外觀。|  
|[COleControl::AmbientBackColor](../Topic/COleControl::AmbientBackColor.md)|傳回環境 BackColor 屬性的值。|  
|[COleControl::AmbientDisplayName](../Topic/COleControl::AmbientDisplayName.md)|傳回控制項的名稱所指定的容器。|  
|[COleControl::AmbientFont](../Topic/COleControl::AmbientFont.md)|傳回環境字型屬性的值。|  
|[COleControl::AmbientForeColor](../Topic/COleControl::AmbientForeColor.md)|傳回環境 ForeColor 屬性的值。|  
|[COleControl::AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md)|傳回容器的地區設定 ID.|  
|[COleControl::AmbientScaleUnits](../Topic/COleControl::AmbientScaleUnits.md)|傳回容器 \(Container\) 使用的單位類型。|  
|[COleControl::AmbientShowGrabHandles](../Topic/COleControl::AmbientShowGrabHandles.md)|判斷抓取控點是否已經顯示。|  
|[COleControl::AmbientShowHatching](../Topic/COleControl::AmbientShowHatching.md)|判斷孵化應是否已經顯示。|  
|[COleControl::AmbientTextAlign](../Topic/COleControl::AmbientTextAlign.md)|傳回容器指定文字對齊類型。|  
|[COleControl::AmbientUIDead](../Topic/COleControl::AmbientUIDead.md)|判斷控制項是否可回應使用者介面動作。|  
|[COleControl::AmbientUserMode](../Topic/COleControl::AmbientUserMode.md)|判斷容器的方式。|  
|[COleControl::BoundPropertyChanged](../Topic/COleControl::BoundPropertyChanged.md)|告知容器變更繫結屬性。|  
|[COleControl::BoundPropertyRequestEdit](../Topic/COleControl::BoundPropertyRequestEdit.md)|要求使用權限可以編輯屬性值。|  
|[COleControl::ClientToParent](../Topic/COleControl::ClientToParent.md)|平移點相對於控制項的原點為點相對於其容器的原點。|  
|[COleControl::ClipCaretRect](../Topic/COleControl::ClipCaretRect.md)|如果方法是由控制項重疊，調整插入號矩形。|  
|[COleControl::ControlInfoChanged](../Topic/COleControl::ControlInfoChanged.md)|在控制項處理的一組助憶鍵後呼叫這個函式已變更。|  
|[COleControl::DisplayError](../Topic/COleControl::DisplayError.md)|示範庫存錯誤事件傳送到控制項的使用者。|  
|[COleControl::DoClick](../Topic/COleControl::DoClick.md)|內建 `DoClick` 方法的實作。|  
|[COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)|`COleControl` 序列化物件的屬性。|  
|[COleControl::DoSuperclassPaint](../Topic/COleControl::DoSuperclassPaint.md)|從  視窗重新繪製控制項子類別化的 OLE 控制項。|  
|[COleControl::EnableSimpleFrame](../Topic/COleControl::EnableSimpleFrame.md)|啟用簡單框架控制項支援。|  
|[COleControl::ExchangeExtent](../Topic/COleControl::ExchangeExtent.md)|將控制項的寬度和高度。|  
|[COleControl::ExchangeStockProps](../Topic/COleControl::ExchangeStockProps.md)|序列化控制共用屬性。|  
|[COleControl::ExchangeVersion](../Topic/COleControl::ExchangeVersion.md)|將控制項的版本號碼。|  
|[COleControl::FireClick](../Topic/COleControl::FireClick.md)|內建 `Click` 引發事件。|  
|[COleControl::FireDblClick](../Topic/COleControl::FireDblClick.md)|內建 `DblClick` 引發事件。|  
|[COleControl::FireError](../Topic/COleControl::FireError.md)|內建 `Error` 引發事件。|  
|[COleControl::FireEvent](../Topic/COleControl::FireEvent.md)|引發自訂事件。|  
|[COleControl::FireKeyDown](../Topic/COleControl::FireKeyDown.md)|內建 `KeyDown` 引發事件。|  
|[COleControl::FireKeyPress](../Topic/COleControl::FireKeyPress.md)|內建 `KeyPress` 引發事件。|  
|[COleControl::FireKeyUp](../Topic/COleControl::FireKeyUp.md)|內建 `KeyUp` 引發事件。|  
|[COleControl::FireMouseDown](../Topic/COleControl::FireMouseDown.md)|內建 `MouseDown` 引發事件。|  
|[COleControl::FireMouseMove](../Topic/COleControl::FireMouseMove.md)|內建 `MouseMove` 引發事件。|  
|[COleControl::FireMouseUp](../Topic/COleControl::FireMouseUp.md)|內建 `MouseUp` 引發事件。|  
|[COleControl::FireReadyStateChange](../Topic/COleControl::FireReadyStateChange.md)|表示控制項的就緒狀態變更時，會引發事件。|  
|[COleControl::GetActivationPolicy](../Topic/COleControl::GetActivationPolicy.md)|變更 `IPointerInactive` 支援介面的控制項預設的啟動行為。|  
|[COleControl::GetAmbientProperty](../Topic/COleControl::GetAmbientProperty.md)|傳回指定的環境屬性的值。|  
|[COleControl::GetAppearance](../Topic/COleControl::GetAppearance.md)|傳回內建外觀屬性的值。|  
|[COleControl::GetBackColor](../Topic/COleControl::GetBackColor.md)|傳回內建 BackColor 屬性的值。|  
|[COleControl::GetBorderStyle](../Topic/COleControl::GetBorderStyle.md)|傳回內建 BorderStyle 屬性的值。|  
|[COleControl::GetCapture](../Topic/COleControl::GetCapture.md)|判斷無視窗，啟動的控制項物件是否具有滑鼠捕捉。|  
|[COleControl::GetClassID](../Topic/COleControl::GetClassID.md)|擷取控制項的 OLE 類別 ID。|  
|[COleControl::GetClientOffset](../Topic/COleControl::GetClientOffset.md)|擷取控制項的矩形區域的左上角和其工作區之間的左上角的差異。|  
|[COleControl::GetClientRect](../Topic/COleControl::GetClientRect.md)|擷取控制項的工作區大小。|  
|[COleControl::GetClientSite](../Topic/COleControl::GetClientSite.md)|查詢指標的物件在其容器內的目前用戶端網站。|  
|[COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)|擷取控制旗標設定為。|  
|[COleControl::GetControlSize](../Topic/COleControl::GetControlSize.md)|傳回 OLE 控制項的位置和大小。|  
|[COleControl::GetDC](../Topic/COleControl::GetDC.md)|對於無視窗 \(Windowless\) 控制項能夠從其容器所取得的裝置內容。|  
|[COleControl::GetEnabled](../Topic/COleControl::GetEnabled.md)|傳回內建啟用屬性的值。|  
|[COleControl::GetExtendedControl](../Topic/COleControl::GetExtendedControl.md)|擷取指標屬於容器的擴充項物件。|  
|[COleControl::GetFocus](../Topic/COleControl::GetFocus.md)|判斷控制項是否擁有焦點。|  
|[COleControl::GetFont](../Topic/COleControl::GetFont.md)|傳回內建的字型屬性的值。|  
|[COleControl::GetFontTextMetrics](../Topic/COleControl::GetFontTextMetrics.md)|傳回 `CFontHolder` 物件的度量資訊。|  
|[COleControl::GetForeColor](../Topic/COleControl::GetForeColor.md)|傳回內建 ForeColor 屬性的值。|  
|[COleControl::GetHwnd](../Topic/COleControl::GetHwnd.md)|傳回內建 hWnd 屬性的值。|  
|[COleControl::GetMessageString](../Topic/COleControl::GetMessageString.md)|針對功能表項目的狀態列文字。|  
|[COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md)|使用者無法存取控制項的屬性值。|  
|[COleControl::GetReadyState](../Topic/COleControl::GetReadyState.md)|傳回控制項的就緒狀態。|  
|[COleControl::GetRectInContainer](../Topic/COleControl::GetRectInContainer.md)|傳回控制項的矩形相對於其容器。|  
|[COleControl::GetStockTextMetrics](../Topic/COleControl::GetStockTextMetrics.md)|傳回內建的字型屬性的度量資訊。|  
|[COleControl::GetText](../Topic/COleControl::GetText.md)|傳回內建文字或標題屬性的值。|  
|[COleControl::GetWindowlessDropTarget](../Topic/COleControl::GetWindowlessDropTarget.md)|允許無視窗 \(Windowless\) 控制項覆寫是拖放作業的目標。|  
|[COleControl::InitializeIIDs](../Topic/COleControl::InitializeIIDs.md)|告知控制項所使用的基底類別 IID。|  
|[COleControl::InternalGetFont](../Topic/COleControl::InternalGetFont.md)|傳回內建的字型屬性的 `CFontHolder` 物件。|  
|[COleControl::InternalGetText](../Topic/COleControl::InternalGetText.md)|擷取股票標題或文字屬性。|  
|[COleControl::InternalSetReadyState](../Topic/COleControl::InternalSetReadyState.md)|將控制項的準備狀態並引發就緒狀態變更事件。|  
|[COleControl::InvalidateControl](../Topic/COleControl::InvalidateControl.md)|失效顯示控制項的範圍，會重新繪製。|  
|[COleControl::InvalidateRgn](../Topic/COleControl::InvalidateRgn.md)|null 在特定區域內的容器視窗的工作區。  可以使用重繪無視窗 \(Windowless\) 控制項位於區域。|  
|[COleControl::IsConvertingVBX](../Topic/COleControl::IsConvertingVBX.md)|允許具有特製化 OLE 控制項的載入。|  
|[COleControl::IsModified](../Topic/COleControl::IsModified.md)|判斷控制項狀態是否已變更。|  
|[COleControl::IsOptimizedDraw](../Topic/COleControl::IsOptimizedDraw.md)|指出容器是否支援目前的繪製作業的最佳化的繪圖。|  
|[COleControl::IsSubclassedControl](../Topic/COleControl::IsSubclassedControl.md)|呼叫以決定控制項的子類別 \(Subclass\) 視窗是控制項。|  
|[COleControl::Load](../Topic/COleControl::Load.md)|重設任何先前非同步的 \(Asynchronous\) 資料並初始化控制項的非同步屬性的新載入。|  
|[COleControl::LockInPlaceActive](../Topic/COleControl::LockInPlaceActive.md)|決定控制項是否可以容器停用。|  
|[COleControl::OnAmbientPropertyChange](../Topic/COleControl::OnAmbientPropertyChange.md)|呼叫，以變更環境屬性 \(Ambient Property\)。|  
|[COleControl::OnAppearanceChanged](../Topic/COleControl::OnAppearanceChanged.md)|變更時呼叫，以將股票外觀屬性。|  
|[COleControl::OnBackColorChanged](../Topic/COleControl::OnBackColorChanged.md)|變更時呼叫，以將股票 BackColor 屬性。|  
|[COleControl::OnBorderStyleChanged](../Topic/COleControl::OnBorderStyleChanged.md)|變更時呼叫，以將股票 BorderStyle 屬性。|  
|[COleControl::OnClick](../Topic/COleControl::OnClick.md)|呼叫會引發股票 Click 事件。|  
|[COleControl::OnClose](../Topic/COleControl::OnClose.md)|告知控制項 `IOleControl::Close` 呼叫。|  
|[COleControl::OnDoVerb](../Topic/COleControl::OnDoVerb.md)|呼叫，以控制項動詞命令執行之後。|  
|[COleControl::OnDraw](../Topic/COleControl::OnDraw.md)|呼叫方法，則控制項需要重繪本身。|  
|[COleControl::OnDrawMetafile](../Topic/COleControl::OnDrawMetafile.md)|呼叫由容器使用中繼檔 \(Metafile\) 裝置內容，，當控制項需要重繪本身。|  
|[COleControl::OnEdit](../Topic/COleControl::OnEdit.md)|呼叫由容器包含 UI 中啟動 OLE 控制項。|  
|[COleControl::OnEnabledChanged](../Topic/COleControl::OnEnabledChanged.md)|變更時呼叫，以將股票啟用屬性。|  
|[COleControl::OnEnumVerbs](../Topic/COleControl::OnEnumVerbs.md)|呼叫由容器列舉控制項的動詞命令。|  
|[COleControl::OnEventAdvise](../Topic/COleControl::OnEventAdvise.md)|呼叫時，事件處理常式會從控制項連接或中斷連接。|  
|[COleControl::OnFontChanged](../Topic/COleControl::OnFontChanged.md)|變更時呼叫，以將內建的字型屬性。|  
|[COleControl::OnForeColorChanged](../Topic/COleControl::OnForeColorChanged.md)|變更時呼叫，以將股票 ForeColor 屬性。|  
|[COleControl::OnFreezeEvents](../Topic/COleControl::OnFreezeEvents.md)|呼叫控制項的事件時，凍結或解除凍結。|  
|[COleControl::OnGetColorSet](../Topic/COleControl::OnGetColorSet.md)|告知控制項 `IOleObject::GetColorSet` 呼叫。|  
|[COleControl::OnGetControlInfo](../Topic/COleControl::OnGetControlInfo.md)|提供記憶體資訊加入至容器。|  
|[COleControl::OnGetDisplayString](../Topic/COleControl::OnGetDisplayString.md)|呼叫以取得字串表示屬性值。|  
|[COleControl::OnGetInPlaceMenu](../Topic/COleControl::OnGetInPlaceMenu.md)|要求將與容器 \(Container\) 功能表控制項功能表的控制代碼。|  
|[COleControl::OnGetNaturalExtent](../Topic/COleControl::OnGetNaturalExtent.md)|擷取控制項的顯示大小的覆寫最接近所顯示的大小和範圍模式。|  
|[COleControl::OnGetPredefinedStrings](../Topic/COleControl::OnGetPredefinedStrings.md)|傳回的字串表示屬性的可能值。|  
|[COleControl::OnGetPredefinedValue](../Topic/COleControl::OnGetPredefinedValue.md)|傳回值與預先定義的對應字串。|  
|[COleControl::OnGetViewExtent](../Topic/COleControl::OnGetViewExtent.md)|擷取控制項的顯示區域的大小的覆寫 \(可以用來啟用二 Web 樣式的繪圖\)。|  
|[COleControl::OnGetViewRect](../Topic/COleControl::OnGetViewRect.md)|呈現控制項的大小的覆寫輸入開始在特定位置的矩形。|  
|[COleControl::OnGetViewStatus](../Topic/COleControl::OnGetViewStatus.md)|擷取控制項的檢視狀態的覆寫。|  
|[COleControl::OnHideToolBars](../Topic/COleControl::OnHideToolBars.md)|呼叫由容器，當控制項已停用的 UI。|  
|[COleControl::OnInactiveMouseMove](../Topic/COleControl::OnInactiveMouseMove.md)|覆寫有非現用控制項的容器在滑鼠指標 `WM_MOUSEMOVE` 分派訊息下方的控制項。|  
|[COleControl::OnInactiveSetCursor](../Topic/COleControl::OnInactiveSetCursor.md)|覆寫有非現用控制項的容器在滑鼠指標 `WM_SETCURSOR` 分派訊息下方的控制項。|  
|[COleControl::OnKeyDownEvent](../Topic/COleControl::OnKeyDownEvent.md)|呼叫，以共用 KeyDown 事件引發之後。|  
|[COleControl::OnKeyPressEvent](../Topic/COleControl::OnKeyPressEvent.md)|呼叫，以共用 KeyPress 事件引發之後。|  
|[COleControl::OnKeyUpEvent](../Topic/COleControl::OnKeyUpEvent.md)|呼叫，以共用 KeyUp 事件引發之後。|  
|[COleControl::OnMapPropertyToPage](../Topic/COleControl::OnMapPropertyToPage.md)|表示使用哪個屬性頁提供編輯屬性。|  
|[COleControl::OnMnemonic](../Topic/COleControl::OnMnemonic.md)|呼叫時，控制項的助憶鍵則為。|  
|[COleControl::OnProperties](../Topic/COleControl::OnProperties.md)|呼叫時，控制項的「屬性」動詞命令叫用。|  
|[COleControl::OnQueryHitPoint](../Topic/COleControl::OnQueryHitPoint.md)|查詢的覆寫控制項的顯示是否重疊指定點。|  
|[COleControl::OnQueryHitRect](../Topic/COleControl::OnQueryHitRect.md)|查詢的覆寫控制項的顯示是否重疊在指定矩形的任何位置。|  
|[COleControl::OnRenderData](../Topic/COleControl::OnRenderData.md)|呼叫由架構擷取指定之格式的資料。|  
|[COleControl::OnRenderFileData](../Topic/COleControl::OnRenderFileData.md)|呼叫框架以指定格式的檔案中擷取資料。|  
|[COleControl::OnRenderGlobalData](../Topic/COleControl::OnRenderGlobalData.md)|呼叫框架從指定格式的全域記憶體擷取資料。|  
|[COleControl::OnResetState](../Topic/COleControl::OnResetState.md)|將控制項的屬性設為預設值。|  
|[COleControl::OnSetClientSite](../Topic/COleControl::OnSetClientSite.md)|告知控制項 `IOleControl::SetClientSite` 呼叫。|  
|[COleControl::OnSetData](../Topic/COleControl::OnSetData.md)|以其他值取代控制項的資料。|  
|[COleControl::OnSetExtent](../Topic/COleControl::OnSetExtent.md)|呼叫控制項的範圍之後進行變更。|  
|[COleControl::OnSetObjectRects](../Topic/COleControl::OnSetObjectRects.md)|呼叫，以變更後控制項的大小。|  
|[COleControl::OnShowToolBars](../Topic/COleControl::OnShowToolBars.md)|呼叫，當控制項正在啟動的 UI。|  
|[COleControl::OnTextChanged](../Topic/COleControl::OnTextChanged.md)|變更時呼叫，以將內建文字或標題屬性。|  
|[COleControl::OnWindowlessMessage](../Topic/COleControl::OnWindowlessMessage.md)|處理 Windows 訊息 \(除了滑鼠和鍵盤訊息之外\) 無視窗 \(Windowless\) 控制項。|  
|[COleControl::ParentToClient](../Topic/COleControl::ParentToClient.md)|平移點相對於容器的原點為點相對於控制項的原點。|  
|[COleControl::PostModalDialog](../Topic/COleControl::PostModalDialog.md)|告知容器強制回應對話方塊關閉。|  
|[COleControl::PreModalDialog](../Topic/COleControl::PreModalDialog.md)|告知容器強制回應對話方塊隨即顯示。|  
|[COleControl::RecreateControlWindow](../Topic/COleControl::RecreateControlWindow.md)|終結並重新建立控制項的視窗。|  
|[COleControl::Refresh](../Topic/COleControl::Refresh.md)|強制控制項外觀的重新繪製。|  
|[COleControl::ReleaseCapture](../Topic/COleControl::ReleaseCapture.md)|釋放滑鼠捕捉。|  
|[COleControl::ReleaseDC](../Topic/COleControl::ReleaseDC.md)|釋放無視窗 \(Windowless\) 控制項容器的顯示裝置內容。|  
|[COleControl::ReparentControlWindow](../Topic/COleControl::ReparentControlWindow.md)|重設控制項視窗的父代。|  
|[COleControl::ResetStockProps](../Topic/COleControl::ResetStockProps.md)|初始化 `COleControl` 股票屬性重設為其預設值。|  
|[COleControl::ResetVersion](../Topic/COleControl::ResetVersion.md)|初始化版本號碼為指定的值。|  
|[COleControl::ScrollWindow](../Topic/COleControl::ScrollWindow.md)|允許無視窗 \(Windowless\) 控制項移動的就地啟動影像內的區域中顯示。|  
|[COleControl::SelectFontObject](../Topic/COleControl::SelectFontObject.md)|選取自訂字型屬性到裝置內容中。|  
|[COleControl::SelectStockFont](../Topic/COleControl::SelectStockFont.md)|選取內建的字型屬性複製到裝置內容中。|  
|[COleControl::SerializeExtent](../Topic/COleControl::SerializeExtent.md)|序列化或初始化控制項的顯示空間。|  
|[COleControl::SerializeStockProps](../Topic/COleControl::SerializeStockProps.md)|序列化或 `COleControl` 股票初始化屬性。|  
|[COleControl::SerializeVersion](../Topic/COleControl::SerializeVersion.md)|序列化或初始化控制項的版本資訊。|  
|[COleControl::SetAppearance](../Topic/COleControl::SetAppearance.md)|設定內建外觀屬性的值。|  
|[COleControl::SetBackColor](../Topic/COleControl::SetBackColor.md)|設定內建 BackColor 屬性的值。|  
|[COleControl::SetBorderStyle](../Topic/COleControl::SetBorderStyle.md)|設定內建 BorderStyle 屬性的值。|  
|[COleControl::SetCapture](../Topic/COleControl::SetCapture.md)|引發控制項的容器視窗佔表示控制項的滑鼠捕捉。|  
|[COleControl::SetControlSize](../Topic/COleControl::SetControlSize.md)|設定 OLE 控制項的位置和大小。|  
|[COleControl::SetEnabled](../Topic/COleControl::SetEnabled.md)|設定內建啟用屬性的值。|  
|[COleControl::SetFocus](../Topic/COleControl::SetFocus.md)|引發控制項的容器視窗佔表示控制項的輸入焦點。|  
|[COleControl::SetFont](../Topic/COleControl::SetFont.md)|設定內建的字型屬性的值。|  
|[COleControl::SetForeColor](../Topic/COleControl::SetForeColor.md)|設定內建 ForeColor 屬性的值。|  
|[COleControl::SetInitialSize](../Topic/COleControl::SetInitialSize.md)|在容器設定 OLE 控制項的大小，以及第一次顯示。|  
|[COleControl::SetModifiedFlag](../Topic/COleControl::SetModifiedFlag.md)|變更控制項的已修改的狀態。|  
|[COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md)|表示編輯要求失敗。|  
|[COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md)|使用者無法存取控制項的屬性值所做的修改。|  
|[COleControl::SetRectInContainer](../Topic/COleControl::SetRectInContainer.md)|將控制項的矩形相對於其容器。|  
|[COleControl::SetText](../Topic/COleControl::SetText.md)|設定內建文字或標題屬性的值。|  
|[COleControl::ThrowError](../Topic/COleControl::ThrowError.md)|信號錯誤在 OLE 控制項發生錯誤。|  
|[COleControl::TransformCoords](../Topic/COleControl::TransformCoords.md)|轉換在容器和控制項範圍的座標值。|  
|[COleControl::TranslateColor](../Topic/COleControl::TranslateColor.md)|轉換 **OLE\_COLOR** 值組 **COLORREF** 值。|  
|[COleControl::WillAmbientsBeValidDuringLoad](../Topic/COleControl::WillAmbientsBeValidDuringLoad.md)|判斷環境屬性是否可在控制項下一次載入。|  
|[COleControl::WindowProc](../Topic/COleControl::WindowProc.md)|提供 `COleControl` 物件的視窗程序。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleControl::DrawContent](../Topic/COleControl::DrawContent.md)|呼叫框架，其在控制項的外觀需要更新。|  
|[COleControl::DrawMetafile](../Topic/COleControl::DrawMetafile.md)|呼叫框架，當使用中繼檔 \(Metafile\) 裝置內容。|  
|[COleControl::IsInvokeAllowed](../Topic/COleControl::IsInvokeAllowed.md)|啟用 Automation 方法引動過程。|  
|[COleControl::SetInitialDataFormats](../Topic/COleControl::SetInitialDataFormats.md)|呼叫框架初始化控制項所支援的資料格式清單。|  
  
## 備註  
 從 `CWnd`衍生自類別，這個類別繼承一個視窗視窗物件的所有功能以及其他特有的功能，例如 OLE 事件引發和支援的方法和屬性。  
  
 OLE 控制項可以插入 OLE 容器應用程式以及使用容器使用事件引發"雙向系統和公開的方法和屬性向容器。  請注意標準 OLE 容器才支援 OLE 控制項的基本功能。  它們無法支援 OLE 控制項的延伸功能。  表示事件傳送至容器因為發生在控制項時，會執行某些動作事件引發時發生。  接著，容器與控制項溝通使用所公開的方法和屬性，類似於 C\+\+. C\+\+ 成員函式和資料成員的類別。  當某些動作發生時，這個方法可讓開發人員控制控制項的外觀和告知容器。  
  
## 無視窗控制項  
 OLE 控制項可用於就地啟動，而不使用  視窗。  無視窗 \(Windowless\) 控制項有明顯好處:  
  
-   無視窗控制項可以是透明和非矩形  
  
-   無視窗控制項減少執行個體大小和物件的建立時間  
  
 控制項不需要視窗。  Windows 提供的服務可透過單一共用的視窗 \(通常是容器的\) 和位元分派程式碼輕鬆地提供。  在 Windows 中是物件中的主要不必要的複雜性。  
  
 如果使用的是無視窗啟動，具有視窗\) 的容器控制項 \(如提供自己的視窗則會提供的服務會負責。  例如，在中，如果控制項需要查詢鍵盤焦點，查詢滑鼠捕捉或取得裝置內容，這些作業是由容器所處理。  `COleControl`[無視窗管理成員函式](http://msdn.microsoft.com/zh-tw/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) 叫用在容器執行這些作業。  
  
 在無視窗啟動已啟用時，對控制項的容器 `IOleInPlaceObjectWindowless` 委派輸入訊息連接 \( [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) 副檔名無視窗 \(Windowless\) 控制項支援的\)。  這個介面的 `COleControl` 的實作會將您的控制項的訊息對應會分派這些訊息，然後適當調整滑鼠座標之後。  您可以將對應的項目處理像一般的 Windows 訊息的這些訊息，加入訊息對應。  
  
 在無視窗 \(Windowless\) 控制項，您應該一律使用 `COleControl` 成員函式而不是對應的 `CWnd` 成員函式或及其相關的 Windows API 函式。  
  
 OLE 控制項物件也可以建立視窗，才會變成使用中時，不過，為非現用現用轉換所需的工作量引發，而轉換的速度下移。  這是當問題時，會有:例如，請考慮文字方塊方格。  當向上或向下 cursoring 傳遞這個資料行時，所有控制項都必須位於就地啟動和停用。  非現用\/作用中轉換的速度會直接影響捲動速度。  
  
 如需開發 OLE 控制項框架的詳細資訊，請參閱 Microsoft 知識庫文件 [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md) 和 [概觀:建立 MFC ActiveX 控制項程式](../../mfc/reference/mfc-activex-control-wizard.md)。  如需最佳化 OLE 控制項的相關資訊，包括無視窗和重繪閃動可用的控制項，請參閱 [MFC ActiveX 控制項:最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `COleControl`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [MFC 範例 CIRC3](../../top/visual-cpp-samples.md)   
 [MFC TESTHELP 範例](../../top/visual-cpp-samples.md)   
 [COlePropertyPage Class](../../mfc/reference/colepropertypage-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFontHolder Class](../../mfc/reference/cfontholder-class.md)   
 [CPictureHolder Class](../../mfc/reference/cpictureholder-class.md)