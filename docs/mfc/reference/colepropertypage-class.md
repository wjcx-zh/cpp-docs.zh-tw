---
title: "COlePropertyPage 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePropertyPage
dev_langs:
- C++
helpviewer_keywords:
- OLE property pages
- custom controls [MFC], properties
- COlePropertyPage class
- properties [C++], displaying
- displaying properties
- property pages, OLE
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 20d70cc25305fc5d17860314d9cfbe927df65c70
ms.lasthandoff: 02/24/2017

---
# <a name="colepropertypage-class"></a>COlePropertyPage 類別
用來將自訂控制項的屬性顯示在類似對話方塊的圖形介面中。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE COlePropertyPage : public CDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|建構 `COlePropertyPage` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|表示使用者是否已修改控制項中的值。|  
|[COlePropertyPage::GetObjectArray](#getobjectarray)|傳回的 [屬性] 頁面上編輯物件的陣列。|  
|[COlePropertyPage::GetPageSite](#getpagesite)|[屬性] 頁面中傳回的指標`IPropertyPageSite`介面。|  
|[COlePropertyPage::IgnoreApply](#ignoreapply)|決定哪些控制項不會啟用 [套用] 按鈕。|  
|[COlePropertyPage::IsModified](#ismodified)|表示使用者是否已修改的屬性頁。|  
|[COlePropertyPage::OnEditProperty](#oneditproperty)|使用者編輯屬性時，由架構呼叫。|  
|[COlePropertyPage::OnHelp](#onhelp)|當使用者叫用的說明，由架構呼叫。|  
|[COlePropertyPage::OnInitDialog](#oninitdialog)|初始化屬性頁時，由架構呼叫。|  
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|選擇其他 OLE 控制項和新的屬性時，由架構呼叫。|  
|[Colepropertypage](#onsetpagesite)|當屬性框架提供網頁的網站時，由架構呼叫。|  
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|設定旗標，指出使用者是否已修改控制項中的值。|  
|[COlePropertyPage::SetDialogResource](#setdialogresource)|設定屬性頁的對話方塊資源。|  
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|設定屬性頁的簡短說明文字、 它的說明檔和其說明內容的名稱。|  
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|設定旗標，指出使用者是否已修改的屬性頁。|  
|[COlePropertyPage::SetPageName](#setpagename)|設定屬性頁的名稱 （標題）。|  
  
## <a name="remarks"></a>備註  
 比方說，在屬性頁可能包含一個編輯控制項，可讓使用者檢視和修改控制項的 caption 屬性。  
  
 每個自訂或內建的控制項屬性可以讓控制項的使用者檢視目前的屬性值，視需要修改該值的對話方塊控制項。  
  
 如需有關使用`COlePropertyPage`，請參閱文章[ActiveX 控制項︰ 屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `COlePropertyPage`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxctl.h  
  
##  <a name="a-namecolepropertypagea--colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>COlePropertyPage::COlePropertyPage  
 建構 `COlePropertyPage` 物件。  
  
```  
COlePropertyPage(
    UINT idDlg,  
    UINT idCaption);
```  
  
### <a name="parameters"></a>參數  
 *idDlg*  
 在對話方塊範本資源識別碼。  
  
 *idCaption*  
 資源識別碼屬性頁的標題。  
  
### <a name="remarks"></a>備註  
 當您實作的子類別`COlePropertyPage`，應該使用您的子類別建構函式`COlePropertyPage`建構函式來識別在對話方塊範本資源所依據的屬性頁，並包含其標題的字串資源。  
  
##  <a name="a-namegetcontrolstatusa--colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>COlePropertyPage::GetControlStatus  
 決定使用者是否已修改的值的屬性頁控制項，並提供指定的資源識別碼。  
  
```  
BOOL GetControlStatus(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 屬性頁控制項的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**控制項值已經過修改，否則如果**FALSE**。  
  
##  <a name="a-namegetobjectarraya--colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>COlePropertyPage::GetObjectArray  
 傳回的 [屬性] 頁面上編輯物件的陣列。  
  
```  
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```  
  
### <a name="parameters"></a>參數  
 `pnObjects`  
 將會收到頁面所要編輯的物件數目的不帶正負號長整數指標。  
  
### <a name="return-value"></a>傳回值  
 陣列的指標`IDispatch`指標，用來存取屬性頁上的每個控制項的屬性。 呼叫端必須釋放這些介面指標。  
  
### <a name="remarks"></a>備註  
 每個屬性頁物件維護的指標陣列`IDispatch`頁面所要編輯之物件的介面。 此函式會將其`pnObjects`該陣列中的元素數目的引數和傳回陣列的第一個元素的指標。  
  
##  <a name="a-namegetpagesitea--colepropertypagegetpagesite"></a><a name="getpagesite"></a>COlePropertyPage::GetPageSite  
 取得屬性頁的指標`IPropertyPageSite`介面。  
  
```  
LPPROPERTYPAGESITE GetPageSite();
```  
  
### <a name="return-value"></a>傳回值  
 屬性頁的指標`IPropertyPageSite`介面。  
  
### <a name="remarks"></a>備註  
 控制項和容器互相合作，讓使用者可以瀏覽並編輯控制項屬性。 控制項提供屬性頁中，每個都是 OLE 物件，可讓使用者編輯一組相關的屬性。 容器會提供顯示屬性頁的內容框架。 對於每個頁面上，屬性框架提供網頁，支援`IPropertyPageSite`介面。  
  
##  <a name="a-nameignoreapplya--colepropertypageignoreapply"></a><a name="ignoreapply"></a>COlePropertyPage::IgnoreApply  
 決定哪些控制項不會啟用 [套用] 按鈕。  
  
```  
void IgnoreApply(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 若要忽略控制項的 ID。  
  
### <a name="remarks"></a>備註  
 屬性頁的 [套用] 按鈕會在屬性頁控制項的值有變更時，才啟用。 您可以使用此函式來指定不會導致它們的值變更時，才能啟用 [套用] 按鈕的控制項。  
  
##  <a name="a-nameismodifieda--colepropertypageismodified"></a><a name="ismodified"></a>COlePropertyPage::IsModified  
 判斷使用者是否已變更的內容頁上的任何值。  
  
```  
BOOL IsModified();
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果已修改的屬性頁。  
  
##  <a name="a-nameoneditpropertya--colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COlePropertyPage::OnEditProperty  
 若要編輯的特定屬性時，架構會呼叫此函式。  
  
```  
virtual BOOL OnEditProperty(DISPID dispid);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 要編輯之屬性的分派 ID。  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回**FALSE**。 此函式的覆寫應傳回**TRUE**。  
  
### <a name="remarks"></a>備註  
 您可以覆寫它將焦點設定在頁面上適當的控制項。 預設實作不做任何動作，並傳回**FALSE**。  
  
##  <a name="a-nameonhelpa--colepropertypageonhelp"></a><a name="onhelp"></a>COlePropertyPage::OnHelp  
 當使用者要求線上說明時，架構會呼叫此函式。  
  
```  
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```  
  
### <a name="parameters"></a>參數  
 *lpszHelpDir*  
 包含屬性頁的說明檔的目錄。  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回**FALSE**。  
  
### <a name="remarks"></a>備註  
 覆寫其內容頁必須執行任何特殊動作，當使用者存取說明。 預設實作不做任何動作，並傳回**FALSE**，這個值會指示架構呼叫 WinHelp。  
  
##  <a name="a-nameoninitdialoga--colepropertypageoninitdialog"></a><a name="oninitdialog"></a>COlePropertyPage::OnInitDialog  
 初始化屬性頁 對話方塊時，架構會呼叫此函式。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回**FALSE**。  
  
### <a name="remarks"></a>備註  
 覆寫它如果初始化對話方塊時，不需要任何特殊動作。 預設實作會呼叫`CDialog::OnInitDialog`，並傳回**FALSE**。  
  
##  <a name="a-nameonobjectschangeda--colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COlePropertyPage::OnObjectsChanged  
 選擇其他 OLE 控制項和新的屬性時，由架構呼叫。  
  
```  
virtual void OnObjectsChanged();
```  
  
### <a name="remarks"></a>備註  
 當檢視 OLE 控制項的屬性，在開發環境中，非強制回應對話方塊用來顯示其屬性頁。 如果選取另一個控制項，則必須顯示一組不同的屬性頁的一組新的屬性。 架構會呼叫此函式可通知的變更屬性頁。  
  
 覆寫此函式以接收通知，此動作，並執行任何特殊動作。  
  
##  <a name="a-nameonsetpagesitea--colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>Colepropertypage  
 當屬性框架提供屬性頁的網頁時，架構會呼叫此函式。  
  
```  
virtual void OnSetPageSite();
```  
  
### <a name="remarks"></a>備註  
 預設實作載入網頁的標題，並嘗試判斷從對話方塊資源的頁面大小。 覆寫這個函式，如果屬性頁需要進一步的動作。覆寫應呼叫基底類別實作。  
  
##  <a name="a-namesetcontrolstatusa--colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>COlePropertyPage::SetControlStatus  
 屬性頁控制項狀態變更。  
  
```  
BOOL SetControlStatus(
    UINT nID,  
    BOOL bDirty);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 包含屬性頁控制項 ID。  
  
 `bDirty`  
 指定是否已修改的屬性頁面的欄位。 設定為**TRUE**如果欄位已被修改， **FALSE**如果未修改。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**，如果指定的控制項已設定，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 如果屬性頁控制項的狀態已變更，關閉 [屬性] 頁面上，或選擇 [套用] 按鈕時，會以適當的值更新控制項的屬性。  
  
##  <a name="a-namesetdialogresourcea--colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>COlePropertyPage::SetDialogResource  
 設定屬性頁的對話方塊資源。  
  
```  
void SetDialogResource(HGLOBAL hDialog);
```  
  
### <a name="parameters"></a>參數  
 *hDialog*  
 屬性頁的對話方塊資源的控制代碼。  
  
##  <a name="a-namesethelpinfoa--colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>COlePropertyPage::SetHelpInfo  
 指定工具提示資訊、 說明檔案名稱和屬性頁的說明內容。  
  
```  
void SetHelpInfo(
    LPCTSTR lpszDocString,  
    LPCTSTR lpszHelpFile = NULL,  
    DWORD dwHelpContext = 0);
```  
  
### <a name="parameters"></a>參數  
 *lpszDocString*  
 字串，包含顯示在狀態列上或其他位置的簡短說明資訊。  
  
 `lpszHelpFile`  
 屬性頁的說明檔的名稱。  
  
 *dwHelpContext*  
 [屬性] 頁面上的說明內容。  
  
##  <a name="a-namesetmodifiedflaga--colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>COlePropertyPage::SetModifiedFlag  
 表示使用者是否已修改的屬性頁。  
  
```  
void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bModified`  
 指定屬性頁的已修改的旗標的新值。  
  
##  <a name="a-namesetpagenamea--colepropertypagesetpagename"></a><a name="setpagename"></a>COlePropertyPage::SetPageName  
 設定屬性頁的名稱，通常會顯示屬性框架資料頁的索引標籤。  
  
```  
void SetPageName(LPCTSTR lpszPageName);
```  
  
### <a name="parameters"></a>參數  
 *lpszPageName*  
 包含屬性頁的名稱之字串的指標。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CIRC3](../../visual-cpp-samples.md)   
 [MFC 範例 TESTHELP](../../visual-cpp-samples.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)

