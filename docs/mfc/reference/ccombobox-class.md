---
title: CComboBox 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
dev_langs:
- C++
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0226e38b34268217b4f21a1f5262cd1f1afbec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702087"
---
# <a name="ccombobox-class"></a>CComboBox 類別
提供 Windows 下拉式方塊的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CComboBox : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComboBox::CComboBox](#ccombobox)|建構 `CComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Ccombobox:: Addstring](#addstring)|將字串加入至清單方塊的下拉式方塊，或使用 CBS_SORT 樣式的清單方塊已排序資料的位置中的清單結尾。|  
|[CComboBox::Clear](#clear)|刪除 （清除） 目前的選取範圍，如果有的話，在編輯控制項中。|  
|[CComboBox::CompareItem](#compareitem)|由架構呼叫以判斷新的清單項目已排序的主控描繪下拉式方塊中的相對位置。|  
|[CComboBox::Copy](#copy)|如果有的話，到剪貼簿 CF_TEXT 格式，請將複製目前的選取範圍。|  
|[CComboBox::Create](#create)|建立下拉式方塊，並將它附加至`CComboBox`物件。|  
|[CComboBox::Cut](#cut)|刪除 （切割） 目前的選取範圍，如果在編輯中的任何控制，而且 CF_TEXT 格式複製到剪貼簿上已刪除的文字。|  
|[CComboBox::DeleteItem](#deleteitem)|從主控描繪下拉式方塊刪除清單項目時，由架構呼叫。|  
|[CComboBox::DeleteString](#deletestring)|從下拉式方塊的清單方塊中，刪除字串。|  
|[CComboBox::Dir](#dir)|將下拉式方塊的清單方塊中的檔案名稱的清單。|  
|[CComboBox::DrawItem](#drawitem)|由架構呼叫時變更為主控描繪下拉式方塊的視覺外觀。|  
|[Ccombobox:: Findstring](#findstring)|尋找包含下拉式方塊的清單方塊中指定的前置詞的第一個字串。|  
|[CComboBox::FindStringExact](#findstringexact)|尋找第一個清單方塊中的字串 （下拉式方塊），符合指定的字串。|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|擷取有關的資訊`CComboBox`物件。|  
|[CComboBox::GetCount](#getcount)|擷取在下拉式方塊的清單方塊中的項目數。|  
|[CComboBox::GetCueBanner](#getcuebanner)|取得下拉式方塊控制項中顯示的提示文字。|  
|[CComboBox::GetCurSel](#getcursel)|擷取索引的目前選取的項目，如果有的話，在下拉式方塊的清單方塊中。|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|擷取可見的 （已關閉卸除） 清單方塊的下拉式清單方塊的螢幕座標。|  
|[CComboBox::GetDroppedState](#getdroppedstate)|決定下拉式方塊的清單方塊是否顯示 （向下卸除）。|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|擷取最小允許下拉式方塊的下拉式清單方塊部分的寬度。|  
|[CComboBox::GetEditSel](#geteditsel)|取得下拉式方塊編輯控制項中目前的選取範圍的開始和結束的字元位置。|  
|[CComboBox::GetExtendedUI](#getextendedui)|決定下拉式方塊是否有預設的使用者介面或擴充的使用者介面。|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|傳回在下拉式方塊的清單方塊部分可以水平捲動的像素的寬度。|  
|[CComboBox::GetItemData](#getitemdata)|擷取指定的下拉式方塊項目相關聯的應用程式提供 32 位元值。|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|擷取與指定的下拉式方塊項目相關聯的應用程式提供 32 位元指標。|  
|[CComboBox::GetItemHeight](#getitemheight)|擷取在下拉式方塊的清單項目的高度。|  
|[CComboBox::GetLBText](#getlbtext)|取得字串，從清單方塊的下拉式方塊。|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|在下拉式方塊的清單方塊中，取得字串的長度。|  
|[CComboBox::GetLocale](#getlocale)|擷取下拉式方塊的地區設定識別碼。|  
|[CComboBox::GetMinVisible](#getminvisible)|在目前的下拉式方塊的下拉式清單中取得可見的項目的數目下限。|  
|[CComboBox::GetTopIndex](#gettopindex)|在下拉式方塊的清單方塊部分中傳回第一個可見項目的索引。|  
|[CComboBox::InitStorage](#initstorage)|會預先配置的項目和下拉式方塊的清單方塊部分中字串的記憶體區塊。|  
|[CComboBox::InsertString](#insertstring)|將字串插入下拉式方塊的清單方塊中。|  
|[CComboBox::LimitText](#limittext)|限制使用者可以輸入至編輯控制項的下拉式方塊文字的長度。|  
|[CComboBox::MeasureItem](#measureitem)|由架構呼叫以判斷何時建立主控描繪下拉式方塊的下拉式方塊的維度。|  
|[CComboBox::Paste](#paste)|從剪貼簿將資料插入在目前游標位置的編輯控制項。 只有當剪貼簿包含 CF_TEXT 格式的資料插入資料。|  
|[CComboBox::ResetContent](#resetcontent)|移除所有項目從清單方塊和編輯下拉式方塊控制項。|  
|[CComboBox::SelectString](#selectstring)|搜尋下拉式方塊的清單方塊中的字串，如果找到該字串，則選取清單方塊中的字串與字串複製到編輯控制項。|  
|[CComboBox::SetCueBanner](#setcuebanner)|設定下拉式方塊控制項顯示的提示文字。|  
|[CComboBox::SetCurSel](#setcursel)|選取清單方塊的下拉式方塊中的字串。|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|設定最小允許下拉式方塊的下拉式清單方塊部分的寬度。|  
|[CComboBox::SetEditSel](#seteditsel)|選取下拉式方塊編輯控制項中的字元。|  
|[CComboBox::SetExtendedUI](#setextendedui)|選取預設的使用者介面或具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 樣式的下拉式方塊的擴充的使用者介面。|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|設定下拉式方塊的清單方塊部分可以水平捲動的像素的寬度。|  
|[CComboBox::SetItemData](#setitemdata)|設定下拉式方塊中指定的項目相關聯的 32 位元值。|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|設定下拉式方塊中指定的項目相關聯的 32 位元指標。|  
|[CComboBox::SetItemHeight](#setitemheight)|在下拉式方塊或下拉式方塊編輯控制項 （或靜態文字） 部分的高度設定清單項目的高度。|  
|[CComboBox::SetLocale](#setlocale)|設定下拉式方塊的地區設定識別碼。|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|在目前的下拉式方塊的下拉式清單中設定可見的項目的數目下限。|  
|[CComboBox::SetTopIndex](#settopindex)|會告知頂端顯示具有指定索引的項目至下拉式方塊的清單方塊部分。|  
|[CComboBox::ShowDropDown](#showdropdown)|顯示或隱藏 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 樣式下拉式方塊的清單方塊。|  
  
## <a name="remarks"></a>備註  
 下拉式方塊包含結合靜態控制項或編輯控制項的清單方塊。 控制項的清單方塊部分可能會顯示在所有的時間，或當使用者選取控制項旁的下拉式箭號可能只有下拉式清單。  
  
 目前選取的項目 （如果有的話） 的清單方塊中會顯示在靜態，或編輯控制項。 此外，如果下拉式方塊的下拉式清單樣式，使用者可以在清單中，輸入之初始字元的其中一個項目和清單方塊中，如果可以看見，會反白顯示該初始字元的下一個項目。  
  
 下表比較三個的下拉式方塊[樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。  
  
|樣式|當清單方塊是可見的|靜態或編輯控制項|  
|-----------|-------------------------------|-----------------------------|  
|簡單|永遠|編輯|  
|Drop-down|當已下拉|編輯|  
|下拉式清單|當已下拉|Static|  
  
 您可以建立`CComboBox`從對話方塊範本，或直接在您的程式碼中的物件。 在這兩種情況下，第一次呼叫建構函式`CComboBox`來建構`CComboBox`物件，然後呼叫[建立](#create)成員函式來建立控制項，並將其附加至`CComboBox`物件。  
  
 如果您想要處理 Windows 通知訊息傳送至其父代下拉式方塊 (通常是從衍生的類別`CDialog`)，將訊息對應項目和訊息處理常式成員函式新增至每個訊息的父類別。  
  
 每個訊息對應項目都會使用下列格式：  
  
 **ON_** 通知 **(**`id`**，**`memberFxn`**)**  
  
 何處`id`指定將通知傳送給下拉式方塊控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 父代的函式原型如下所示：  
  
 **afx_msg** `void` `memberFxn` **（);**  
  
 無法預測特定通知會傳送的順序。 特別是之前, 或之後 CBN_CLOSEUP 通知，可能會發生 CBN_SELCHANGE 通知。  
  
 可能的訊息對應項目如下所示：  
  
- ON_CBN_CLOSEUP (Windows 3.1 和更新版本。)下拉式方塊的清單方塊已關閉。 此通知訊息不會傳送具有下拉式方塊[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
- ON_CBN_DBLCLK 使用者按兩下清單方塊的下拉式方塊中的字串。 CBS_SIMPLE 樣式下拉式方塊，才會傳送此通知訊息。 針對與 seznamem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或是[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，按兩下不會發生因為只要按一下會隱藏清單方塊。  
  
- 在即將下拉式清單方塊的下拉式方塊的 ON_CBN_DROPDOWN （顯示出來）。 只有與 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 樣式下拉式方塊可以進行此通知訊息。  
  
- ON_CBN_EDITCHANGE 使用者所執行的動作，可能已變更編輯控制項下拉式方塊部分中的文字。 不同 CBN_EDITUPDATE 訊息中，於 Windows 更新畫面之後，會傳送這則訊息。 它不會傳送下拉式方塊是否 CBS_DROPDOWNLIST 樣式。  
  
- ON_CBN_EDITUPDATE 下拉式方塊編輯控制項部分即將變更的顯示文字。 控制項已格式化的文字之後，但它會顯示文字之前，會傳送此通知訊息。 它不會傳送下拉式方塊是否 CBS_DROPDOWNLIST 樣式。  
  
- ON_CBN_ERRSPACE 下拉式方塊無法配置足夠的記憶體，以滿足特定的要求。  
  
- ON_CBN_SELENDCANCEL (Windows 3.1 和更新版本。)指出應該取消使用者的選取項目。 使用者按一下的項目，並按一下另一個視窗或控制項可隱藏下拉式方塊的清單方塊。 CBN_CLOSEUP 通知訊息，表示應該忽略的使用者的選取範圍之前，會傳送此通知訊息。 即使 CBN_CLOSEUP 通知訊息不會傳送 （若為 CBS_SIMPLE 樣式下拉式方塊），則會傳送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知訊息。  
  
- ON_CBN_SELENDOK 使用者選取的項目，然後按下 ENTER 鍵，或按一下向下鍵來隱藏下拉式方塊的清單方塊。 CBN_CLOSEUP 訊息以指出該使用者的選取項目應該視為有效之前傳送此通知訊息。 即使 CBN_CLOSEUP 通知訊息不會傳送 （若為 CBS_SIMPLE 樣式下拉式方塊），則會傳送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知訊息。  
  
- ON_CBN_KILLFOCUS 下拉式方塊正失去輸入的焦點。  
  
- ON_CBN_SELCHANGE 下拉式方塊的清單方塊中選取項目是因為使用者在清單方塊中按一下，或使用方向鍵來變更選取項目而即將變更。 在處理此訊息時，下拉式方塊編輯控制項中的文字只擷取透過`GetLBText`或另一個類似的函式。 `GetWindowText` 無法使用。  
  
- ON_CBN_SETFOCUS 下拉式方塊中，會收到輸入的焦點。  
  
 如果您建立`CComboBox` 對話方塊中 （透過對話方塊資源），物件`CComboBox`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您在內嵌`CComboBox`物件在另一個視窗中的物件，您不需要它終結。 如果您建立`CComboBox`物件在堆疊上，它會自動終結。 如果您建立`CComboBox`物件上使用堆積**新**函式，您必須呼叫**刪除**Windows 下拉式方塊終結時終結它在物件上。  
  
 **附註**如果您想要處理 WM_KEYDOWN 和 WM_CHAR 訊息時，您有子類別化下拉式方塊的編輯和清單方塊控制項中，衍生類別，從`CEdit`和`CListBox`，並將這些訊息的處理常式新增至衍生的類別。 如需詳細資訊，請參閱 < [ http://support.microsoft.com/default.aspxscid=kb; en-us-我們;Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667)並[CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="addstring"></a>  Ccombobox:: Addstring  
 將字串加入至清單方塊的下拉式方塊。  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 *lpszString*  
 指向以 null 結束的字串，會加入。  
  
### <a name="return-value"></a>傳回值  
 如果大於或等於 0 的傳回值，它就會是清單方塊中的字串以零為起始的索引。 如果發生錯誤，傳回的值會為 CB_ERR如果空間不足無法存放新的字串，傳回的值會是 CB_ERRSPACE。  
  
### <a name="remarks"></a>備註  
 如果清單方塊不以建立[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，字串會新增至清單的結尾。 否則，字串插入至清單中，而且排序清單。  
  
> [!NOTE]
>  Windows 不支援這個函式`ComboBoxEx`控制項。 如需有關此控制項的詳細資訊，請參閱 < [ComboBoxEx 控制項](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。  
  
 若要插入清單中的特定位置中的字串，請使用[InsertString](#insertstring)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>  CComboBox::CComboBox  
 建構 `CComboBox` 物件。  
  
```  
CComboBox();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>  CComboBox::Clear  
 刪除 （清除） 目前的選取範圍，如果有的話，在下拉式方塊編輯控制項中。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 若要刪除目前選取範圍，並放置到剪貼簿上已刪除的內容，請使用[剪下](#cut)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>  CComboBox::CompareItem  
 由架構呼叫以判斷新的項目已排序的主控描繪下拉式方塊的清單方塊部分中的相對位置。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpCompareItemStruct*  
 長指標[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)結構。  
  
### <a name="return-value"></a>傳回值  
 指出兩個項目中所述的相對位置`COMPAREITEMSTRUCT`結構。 它可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|- 1|項目 1 排序項目 2 之前。|  
|0|項目 1 和 2 的項目排序相同。|  
|1|項目 2 之後，排序項目 1。|  
  
 請參閱[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)的說明`COMPAREITEMSTRUCT`。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 如果您建立主控描繪下拉式方塊的 LBS_SORT 樣式時，您必須覆寫此成員函式，以協助架構排序新的項目加入至清單方塊中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>  CComboBox::Copy  
 如果到剪貼簿格式 CF_TEXT 下拉式方塊編輯控制項中的任何，請將複製目前的選取範圍。  
  
```  
void Copy();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="create"></a>  CComboBox::Create  
 建立下拉式方塊，並將它附加至`CComboBox`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *cheaderctrl:: Create*  
 指定下拉式方塊的樣式。 套用的任何組合[下拉式方塊樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)至方塊。  
  
 *rect*  
 指向的位置和下拉式方塊的大小。 可以是[RECT 結構](../../mfc/reference/rect-structure1.md)或`CRect`物件。  
  
 *pParentWnd*  
 指定下拉式方塊的父視窗 (通常`CDialog`)。 它必須不是 NULL。  
  
 *nID*  
 指定下拉式方塊的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CComboBox`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫`Create`，這會建立 Windows 下拉式方塊，並將它附加至`CComboBox`物件。  
  
 當`Create`執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，並[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)下拉式方塊的訊息。  
  
 根據預設，處理這些訊息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，以及[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式在 `CWnd`基底類別。 若要擴充的預設訊息處理，衍生的類別`CComboBox`、 將訊息對應新增至新的類別，並覆寫先前的訊息處理常式成員函式。 覆寫`OnCreate`，例如，若要執行的新類別所需的初始設定。  
  
 套用下列[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)至下拉式方塊控制項。 :  
  
- WS_CHILD 一律  
  
- WS_VISIBLE 通常  
  
- WS_DISABLED 很少  
  
- WS_VSCROLL 若要新增 下拉式方塊中的清單方塊的垂直捲動  
  
- WS_HSCROLL 若要新增 下拉式方塊中的清單方塊的水平捲軸  
  
- WS_GROUP 群組控制項  
  
- WS_TABSTOP 若要用 tab 鍵順序來包含下拉式方塊  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>  CComboBox::Cut  
 刪除 （切割） 目前的選取範圍，如果在下拉式方塊中的任何編輯控制和 CF_TEXT 格式複製到剪貼簿上已刪除的文字。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>備註  
 若要刪除目前的選取範圍，而不會讓已刪除的文字到剪貼簿，請呼叫[清除](#clear)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>  CComboBox::DeleteItem  
 由架構呼叫，當使用者刪除的項目從主控描繪`CComboBox`物件或終結下拉式方塊。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDeleteItemStruct*  
 Windows 的長指標[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)結構，包含已刪除的項目相關的資訊。 請參閱[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)針對此結構描述。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 此函式來重繪下拉式方塊，視需要來覆寫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>  CComboBox::DeleteString  
 刪除位置中的項目*nIndex*下拉式方塊中。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定要刪除之字串的索引。  
  
### <a name="return-value"></a>傳回值  
 如果傳回的值大於或等於 0，它是在清單中所剩餘的字串數目。 如果，則傳回的值為 CB_ERR *nIndex*指定索引的項目數大於清單中。  
  
### <a name="remarks"></a>備註  
 之後的所有項目*nIndex*現在向下移動一個位置。 比方說，如果下拉式方塊包含兩個項目，刪除第一個項目會導致要現在是在第一個位置中的其餘項目。 *nIndex*= 0 中的第一個位置的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>  CComboBox::Dir  
 將下拉式方塊的清單方塊中的檔案名稱或磁碟機的清單。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>參數  
 *attr*  
 可以是任意的組合**enum**值中所述[Cfile](../../mfc/reference/cfile-class.md#getstatus)或任何組合的下列值：  
  
- 可讀取或寫入 DDL_READWRITE 檔案。  
  
- 可以讀取但不是會寫入 DDL_READONLY 檔案。  
  
- DDL_HIDDEN 檔案隱藏的而且沒有出現在目錄清單中。  
  
- DDL_SYSTEM 檔案是系統檔案。  
  
- 所指定的名稱 DDL_DIRECTORY *lpszWildCard*指定的目錄。  
  
- 已封存 DDL_ARCHIVE 檔案。  
  
- DDL_DRIVES 包含符合指定之名稱的所有磁碟機*lpszWildCard*。  
  
- DDL_EXCLUSIVE 獨佔的旗標。 如果設定專屬的旗標，會列出指定類型的檔案。 否則會列出指定型別的的檔案，除了 「 正常 」 的檔案。  
  
 *lpszWildCard*  
 指向檔案規格字串。 字串可以包含萬用字元 (例如，*。\*)。  
  
### <a name="return-value"></a>傳回值  
 如果傳回的值大於或等於 0，它會是最後一個新增至清單的檔名的以零起始的索引。 如果發生錯誤，傳回的值會為 CB_ERR如果空間不足無法存放新的字串，傳回的值會是 CB_ERRSPACE。  
  
### <a name="remarks"></a>備註  
 Windows 不支援這個函式`ComboBoxEx`控制項。 如需有關此控制項的詳細資訊，請參閱 < [ComboBoxEx 控制項](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>  CComboBox::DrawItem  
 由架構的視覺外觀的主控描繪下拉式方塊變更時呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDrawItemStruct*  
 指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含的所需的繪圖類型的相關資訊。  
  
### <a name="remarks"></a>備註  
 `itemAction`隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)針對此結構描述。  
  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作活動，抽獎獲得主控描繪`CComboBox`物件。 此成員函式會終止之前，應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>  Ccombobox:: Findstring  
 找到，但不會選取第一個字串，其中包含下拉式方塊的清單方塊中指定的前置詞。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>參數  
 *nStartAfter*  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到底部的清單方塊中時，它會繼續從清單方塊的上方回到指定的項目*nStartAfter*。 如果為-1，整個清單方塊中搜尋開頭。  
  
 *lpszString*  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋會是大小寫無關，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 如果傳回的值大於或等於 0，它會是相符項目的以零起始的索引。 如果搜尋成功，它就會是 CB_ERR。  
  
### <a name="remarks"></a>備註  
 Windows 不支援這個函式`ComboBoxEx`控制項。 如需有關此控制項的詳細資訊，請參閱 < [ComboBoxEx 控制項](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>  CComboBox::FindStringExact  
 呼叫`FindStringExact`成員函式來尋找第一個清單方塊中的字串 （下拉式方塊），符合指定的字串*lpszFind*。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndexStart*  
 指定要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到底部的清單方塊中時，它會繼續從清單方塊的上方回到指定的項目*nIndexStart*。 如果*nIndexStart*為-1，整個清單方塊會從一開始搜尋。  
  
 *lpszFind*  
 指向以 null 結束的字串搜尋。 此字串可以包含完整的檔名，包括副檔名。 搜尋不區分大小寫，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 相符的項目或如果搜尋成功 CB_ERR 的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 如果使用下拉式方塊但建立主控描繪樣式[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式`FindStringExact`嘗試比對的值 doubleword 值*lpszFind*。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>  CComboBox::GetComboBoxInfo  
 擷取資訊`CComboBox`物件。  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>參數  
 *pcbi*  
 指標[COMBOBOXINFO](/windows/desktop/api/winuser/ns-winuser-tagcomboboxinfo)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬[CB_GETCOMBOBOXINFO](/windows/desktop/Controls/cb-getcomboboxinfo)訊息、 Windows SDK 中所述。  
  
##  <a name="getcount"></a>  CComboBox::GetCount  
 呼叫此成員函式可擷取下拉式方塊的清單方塊部分中的項目數。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 項目數目。 傳回的計數是一個大於索引值的最後一個項目 （索引以零為起始）。 如果發生錯誤時，它就會是 CB_ERR。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="getcuebanner"></a>  CComboBox::GetCueBanner  
 取得下拉式方塊控制項中顯示的提示文字。  
  
```  
CString GetCueBanner() const;  
  
BOOL GetCueBanner(
    LPTSTR lpszText,   
    int cchText) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*lpszText*|[out]接收的提示橫幅文字的緩衝區指標。|  
|*cchText*|[in]緩衝區的大小， *lpszText*參數所指向。|  
  
### <a name="return-value"></a>傳回值  
 在第一個多載中， [CString](../../atl-mfc-shared/using-cstring.md)物件，其中包含提示橫幅文字，如果有的話，否則`CString`長度為零的物件。  
  
 -或-  
  
 在第二個多載中，則為 TRUE，如果這個方法會成功;否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 提示字元中輸入區域的下拉式方塊控制項中顯示提示文字。 提示文字會顯示，直到使用者提供輸入。  
  
 這個方法會傳送[CB_GETCUEBANNER](/windows/desktop/Controls/cb-getcuebanner)訊息，Windows SDK 中所述。  
  
##  <a name="getcursel"></a>  CComboBox::GetCurSel  
 呼叫此成員函式，來決定要選取哪一個下拉式方塊中的項目。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊的下拉式方塊或如果未選取項目是 CB_ERR 中目前選取的項目以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 `GetCurSel` 傳回索引至清單。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>  CComboBox::GetDroppedControlRect  
 呼叫`GetDroppedControlRect`成員函式來擷取可見 (卸除 down) 的清單方塊的下拉式清單方塊的螢幕座標。  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>參數  
 *lprect*  
 指向[RECT 結構](../../mfc/reference/rect-structure1.md)將要接收座標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>  CComboBox::GetDroppedState  
 呼叫`GetDroppedState`成員函式來決定清單方塊的下拉式方塊是否顯示 （向下卸除）。  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果清單方塊會顯示;否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>  CComboBox::GetDroppedWidth  
 呼叫此函式可擷取的最小的允許寬度，單位為像素下拉式方塊的清單方塊。  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，最小的允許寬度，單位為像素;否則，CB_ERR。  
  
### <a name="remarks"></a>備註  
 此函式僅適用於具有下拉式方塊[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或是[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
 根據預設，在下拉式清單方塊允許的最小寬度是 0。 可以藉由呼叫設定的允許的最小寬度[SetDroppedWidth](#setdroppedwidth)。 在出現的下拉式方塊的清單方塊部分時，其寬度是較大的允許的寬度下限或下拉式方塊的寬度。  
  
### <a name="example"></a>範例  
  範例，請參閱[SetDroppedWidth](#setdroppedwidth)。  
  
##  <a name="geteditsel"></a>  CComboBox::GetEditSel  
 取得下拉式方塊編輯控制項中目前的選取範圍的開始和結束的字元位置。  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 32 位元值，其中包含的高序位文字中的選取範圍結束之後的低序位字組中的開始位置和位置的第一個未選取的字元。 如果下拉式方塊，而不需要編輯控制項上使用此函式，則會傳回 CB_ERR。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>  CComboBox::GetExtendedUI  
 呼叫`GetExtendedUI`成員函式來判斷下拉式方塊具有預設的使用者介面或擴充的使用者介面。  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果下拉式方塊具有延伸的使用者介面中，為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 擴充的使用者介面可以透過下列方式來識別：  
  
-   按一下靜態控制項，會顯示僅針對下拉式方塊和清單方塊[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
-   按向下鍵顯示清單方塊中 （F4 會停用）。  
  
 靜態控制項中捲動時停用的項目清單不是顯示 （箭號會停用索引鍵）。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>  CComboBox::GetHorizontalExtent  
 從下拉式方塊中擷取的像素為單位的下拉式方塊的清單方塊部分可以水平捲動的寬度。  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊中，像素為單位的清單方塊部分的可捲動的寬度。  
  
### <a name="remarks"></a>備註  
 這是下拉式方塊的清單方塊部分有水平捲軸時，才適用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>  CComboBox::GetItemData  
 擷取指定的下拉式方塊項目相關聯的應用程式提供 32 位元值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含下拉式方塊的清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果發生錯誤相關聯的項目或 CB_ERR 32 位元值。  
  
### <a name="remarks"></a>備註  
 32 位元值可以設定具有*dwItemData*的參數[SetItemData](#setitemdata)成員函式呼叫。 使用`GetItemDataPtr`成員函式，如果要擷取的 32 位元值是指標 (**void** <strong>\*</strong>)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>  CComboBox::GetItemDataPtr  
 擷取應用程式所提供的 32 位元值，而此一做為指標指定的下拉式方塊項目相關聯 (**void** <strong>\*</strong>)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含下拉式方塊的清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果發生錯誤，請擷取是指標，則為-1。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>  CComboBox::GetItemHeight  
 呼叫`GetItemHeight`成員函式來擷取在下拉式方塊中的清單項目的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定下拉式方塊的高度是要擷取的元件。 如果*nIndex*參數值-1，將會在擷取下拉式方塊編輯控制項 （或靜態文字） 部分的高度。 如果下拉式方塊中含有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式*nIndex*指定高度為要擷取之清單項目的以零為起始的索引。 否則，請*nIndex*應該設定為 0。  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素下拉式方塊中指定的項目。 如果發生錯誤時，傳回的值將為 CB_ERR。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>  CComboBox::GetLBText  
 取得字串，從清單方塊的下拉式方塊。  
  
```  
int GetLBText(
    int nIndex,  
    LPTSTR lpszText) const;  
  
void GetLBText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含要複製的清單方塊字串以零為起始的索引。  
  
 *lpszText*  
 要接收字串之緩衝區的點。 緩衝區必須有足夠的空間，如字串和結束的 null 字元。  
  
 *rString*  
 參考`CString`。  
  
### <a name="return-value"></a>傳回值  
 字串，但不包含終止的 null 字元的長度 （以位元組為單位）。 如果*nIndex*未指定有效的索引，則傳回值是 CB_ERR。  
  
### <a name="remarks"></a>備註  
 這個成員的第二種形式的函式會填滿`CString`物件項目的文字。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>  CComboBox::GetLBTextLen  
 在下拉式方塊的清單方塊中，取得字串的長度。  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含清單方塊字串之以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 以位元組為單位，但不包含終止的 null 字元字串的長度。 如果*nIndex*未指定有效的索引，則傳回值是 CB_ERR。  
  
### <a name="example"></a>範例  
  範例，請參閱[CComboBox::GetLBText](#getlbtext)。  
  
##  <a name="getlocale"></a>  CComboBox::GetLocale  
 擷取使用下拉式方塊的地區設定。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊中的字串，地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 會使用地區設定，例如，以判斷排序的下拉式方塊中的字串的排序次序。  
  
### <a name="example"></a>範例  
  範例，請參閱[CComboBox::SetLocale](#setlocale)。  
  
##  <a name="getminvisible"></a>  CComboBox::GetMinVisible  
 在目前的下拉式方塊控制項下拉式清單中取得可見的項目的數目下限。  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的下拉式清單中可見的項目最小數目。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[CB_GETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible)訊息，Windows SDK 中所述。  
  
##  <a name="gettopindex"></a>  CComboBox::GetTopIndex  
 擷取在下拉式方塊的清單方塊部分中的第一個可見項目以零為起始索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 以零起始的索引的第一個可見的項目，如果成功，下拉式方塊的清單方塊部分 CB_ERR，否則為。  
  
### <a name="remarks"></a>備註  
 一開始，項目 0 頂端的清單方塊中，但如果捲動清單方塊，另一個項目可能會在頂端。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>  CComboBox::InitStorage  
 將清單方塊項目儲存在下拉式方塊的清單方塊部分會配置記憶體。  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>參數  
 *nItems*  
 指定要加入項目數目。  
  
 *nBytes*  
 指定的記憶體數量，以位元組為單位，來配置項目字串。  
  
### <a name="return-value"></a>傳回值  
 如果成功，最大的項目數下拉式方塊的清單方塊部分可以儲存在記憶體重新配置之前會有需要否則為 CB_ERRSPACE，這表示沒有足夠記憶體可供使用。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，再將大量的項目新增至清單方塊部分`CComboBox`。  
  
 Windows 95/98 只： *wParam*參數會限制為 16 位元值。 這表示清單方塊不能包含超過 32,767 個項目。 雖然項目數目有限制，總大小的清單方塊中的項目只會受到可用記憶體。  
  
 此函式可協助加速有大量的項目 (超過 100) 的清單方塊的初始化。 它會預先配置的指定讓後續的記憶體數量[AddString](#addstring)， [InsertString](#insertstring)，並[Dir](#dir)函式接受最短的時間。 您可以使用估計值的參數。 如果在增長時，會配置一些額外的記憶體;如果您低估，一般配置使用超過預先配置的量的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>  CComboBox::InsertString  
 將字串插入下拉式方塊的清單方塊中。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含要接收字串之清單方塊中位置以零為基底的索引。 如果這個參數是-1，則會將字串加入至清單的結尾。  
  
 *lpszString*  
 指向要插入的 null 結尾字串。  
  
### <a name="return-value"></a>傳回值  
 已插入字串之位置以零為基底的索引。 如果發生錯誤時，傳回的值將為 CB_ERR。 如果空間不足無法存放新的字串，傳回的值會是 CB_ERRSPACE。  
  
### <a name="remarks"></a>備註  
 不同於[AddString](#addstring)成員函式`InsertString`成員函式不會造成與清單[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)排序樣式。  
  
> [!NOTE]
>  Windows 不支援這個函式`ComboBoxEx`控制項。 如需有關此控制項的詳細資訊，請參閱 < [ComboBoxEx 控制項](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>  CComboBox::LimitText  
 限制使用者可以輸入至下拉式方塊編輯控制項的文字長度以位元組為單位。  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>參數  
 *nMaxChars*  
 指定使用者可以輸入文字的長度 （以位元組為單位）。 如果此參數為 0，文字長度設為 65,535 個位元組。  
  
### <a name="return-value"></a>傳回值  
 如果成功，非零值。 如果呼叫下拉式方塊的樣式[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或下拉式方塊，而不需要編輯控制項，傳回的值為 CB_ERR。  
  
### <a name="remarks"></a>備註  
 如果下拉式方塊沒有樣式[CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)，設定文字限制大於編輯控制項的大小不會有任何作用。  
  
 `LimitText` 只會限制使用者可以輸入的文字。 它不會影響任何文字中已有編輯控制項時傳送訊息，也不會影響在選取清單方塊中的字串時，複製到編輯控制項文字的長度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>  CComboBox::MeasureItem  
 建立主控描繪樣式下拉式方塊時，由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpMeasureItemStruct*  
 長指標[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，並填寫`MEASUREITEMSTRUCT`結構以通知 Windows 個維度的清單方塊下拉式方塊中。 如果建立與 seznamem [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，架構會呼叫此成員函式的清單方塊中的每個項目。 否則，這個成員是只呼叫一次。  
  
 使用主控描繪下拉式方塊中使用 CBS_OWNERDRAWFIXED 樣式建立[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成員函式`CWnd`涉及進一步程式設計考量。 請參閱中的討論[技術的附註 14](../../mfc/tn014-custom-controls.md)。  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>  CComboBox::Paste  
 從剪貼簿將資料插入在目前游標位置下拉式方塊編輯控制項。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>備註  
 只有當剪貼簿包含 CF_TEXT 格式的資料插入資料。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>  CComboBox::ResetContent  
 移除所有項目從清單方塊和編輯下拉式方塊控制項。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>  CComboBox::SelectString  
 搜尋下拉式方塊，清單方塊中的字串，並找到字串，如果清單方塊中選取字串，並將它複製到編輯控制項。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 *nStartAfter*  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到底部的清單方塊中時，它會繼續從清單方塊的上方回到指定的項目*nStartAfter*。 如果為-1，整個清單方塊中搜尋開頭。  
  
 *lpszString*  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋會是大小寫無關，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 選取的項目，如果找不到字串以零為起始的索引。 如果搜尋成功，則傳回值是 CB_ERR 並不會變更目前的選取範圍。  
  
### <a name="remarks"></a>備註  
 只有當其起始的字元 （從起點） 符合的前置詞字串中的字元，則會選取字串。  
  
 請注意，`SelectString`並`FindString`成員函數尋找字串，但`SelectString`成員函式也會選取字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>  CComboBox::SetCueBanner  
 設定下拉式方塊控制項顯示的提示文字。  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*lpszText*|[in]以 null 終止的緩衝區，其中包含提示文字的指標。|  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 提示字元中輸入區域的下拉式方塊控制項中顯示提示文字。 提示文字會顯示，直到使用者提供輸入。  
  
 這個方法會傳送[CB_SETCUEBANNER](/windows/desktop/Controls/cb-setcuebanner)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數*m_combobox*，也就是用來以程式設計方式存取下拉式方塊控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>範例  
 在下列程式碼中，設定下拉式方塊控制項的提示橫幅。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>  CComboBox::SetCurSel  
 選取清單方塊的下拉式方塊中的字串。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>參數  
 *n 請選取*  
 指定要選取之字串的以零為起始的索引。 如果為-1，會移除任何目前的選取範圍的清單方塊中，並清除編輯控制項。  
  
### <a name="return-value"></a>傳回值  
 如果訊息已成功選取的項目以零為起始的索引。 如果，則傳回的值為 CB_ERR *n 請選取*大於清單中的項目數或如果*n 請選取*設為-1，這會清除選取項目。  
  
### <a name="remarks"></a>備註  
 如有必要，清單方塊顯示出來的字串 （如果在清單方塊會顯示）。 下拉式方塊編輯控制項中的文字會變更以反映新的選取範圍。 會移除任何先前的選取項目在清單方塊中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>  CComboBox::SetDroppedWidth  
 呼叫此函式可設定的最小的允許寬度，單位為像素下拉式方塊的清單方塊。  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>參數  
 *nWidth*  
 下拉式方塊中，像素為單位的清單方塊部分的可允許最小寬度。  
  
### <a name="return-value"></a>傳回值  
 如果成功，清單方塊中，否則為 CB_ERR 的新寬度。  
  
### <a name="remarks"></a>備註  
 此函式僅適用於具有下拉式方塊[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或是[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
 根據預設，在下拉式清單方塊允許的最小寬度是 0。 在出現的下拉式方塊的清單方塊部分時，其寬度是較大的允許的寬度下限或下拉式方塊的寬度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>  CComboBox::SetEditSel  
 選取下拉式方塊編輯控制項中的字元。  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>參數  
 *nStartChar*  
 指定的開始位置。 如果開始位置設定為-1，則會移除任何現有的選取範圍。  
  
 *nEndChar*  
 指定的結束位置。 如果到最後一個結束的位置設定為-1，然後從起始位置的所有文字會選取編輯控制項中的字元。  
  
### <a name="return-value"></a>傳回值  
 如果成功，此成員函式，非零值。否則為 0。 如果是 CB_ERR`CComboBox`已經[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或沒有清單方塊的樣式。  
  
### <a name="remarks"></a>備註  
 位置是以零為起始的。 若要選取編輯控制項的第一個字元，您可以指定 0 的開始位置。 結束的位置會為只在選取的最後一個字元之後的字元。 例如，若要選取編輯控制項的前四個字元，您會使用 0 的開始位置和結束位置的 4。  
  
> [!NOTE]
>  Windows 不支援這個函式`ComboBoxEx`控制項。 如需有關此控制項的詳細資訊，請參閱 < [ComboBoxEx 控制項](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。  
  
### <a name="example"></a>範例  
  範例，請參閱[CComboBox::GetEditSel](#geteditsel)。  
  
##  <a name="setextendedui"></a>  CComboBox::SetExtendedUI  
 呼叫`SetExtendedUI`成員函式來選取預設的使用者介面或下拉式方塊具有延伸的使用者介面[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或是[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bExtended*  
 指定下拉式方塊是否應該使用擴充的使用者介面或預設的使用者介面。 TRUE 值選取的擴充的使用者介面。值為 FALSE 會選取的標準使用者介面。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，CB_OKAY 或 CB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 擴充的使用者介面可以透過下列方式來識別：  
  
-   按一下靜態控制項，會顯示清單方塊中，只用於 CBS_DROPDOWNLIST 樣式的下拉式方塊。  
  
-   按向下鍵顯示清單方塊中 （F4 會停用）。  
  
 靜態控制項中捲動時，停用看不到項目清單 （方向鍵會停用）。  
  
### <a name="example"></a>範例  
  範例，請參閱[CComboBox::GetExtendedUI](#getextendedui)。  
  
##  <a name="sethorizontalextent"></a>  CComboBox::SetHorizontalExtent  
 設定寬度，單位為像素的下拉式方塊的清單方塊部分可以水平捲動。  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>參數  
 *nExtent*  
 指定用下拉式方塊的清單方塊部分可以水平捲動的像素數。  
  
### <a name="remarks"></a>備註  
 如果清單方塊的寬度小於此值，水平捲軸會水平捲動清單方塊中的項目。 如果清單方塊的寬度是等於或大於這個值，會隱藏水平捲軸或下拉式方塊是否[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，停用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>  CComboBox::SetItemData  
 設定下拉式方塊中指定的項目相關聯的 32 位元值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含要設定之項目的以零為起始的索引。  
  
 *dwItemData*  
 包含與項目相關聯的新值。  
  
### <a name="return-value"></a>傳回值  
 CB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 使用`SetItemDataPtr`32 位元的項目是否為指標的成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>  CComboBox::SetItemDataPtr  
 設定為指定的指標下拉式方塊中指定的項目相關聯的 32 位元值 (**void** <strong>\*</strong>)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含項目的以零為起始的索引。  
  
 *pData*  
 包含項目相關聯的指標。  
  
### <a name="return-value"></a>傳回值  
 CB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 這個指標會保持有效的存留期間的下拉式方塊中，即使新增或移除項目時，可能會變更項目的下拉式方塊內的相對位置。 因此，在方塊內項目的索引可能會變更，但，指標都是可靠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>  CComboBox::SetItemHeight  
 呼叫`SetItemHeight`成員函式中的下拉式方塊或下拉式方塊編輯控制項 （或靜態文字） 部分的高度設定的清單項目高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定要設定的清單項目高度或下拉式方塊編輯控制項 （或靜態文字） 部分的高度。  
  
 下拉式方塊是否[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式*nIndex*指定的設定，否則為其高度的清單項目以零起始的索引*nIndex*必須是 0並將設定的所有清單項目高度。  
  
 如果*nIndex*為-1，編輯控制項的高度或下拉式方塊的靜態文字部分設定。  
  
 *cyItemHeight*  
 指定高度，單位為像素所識別的下拉式方塊元件*nIndex*。  
  
### <a name="return-value"></a>傳回值  
 如果索引或高度不正確;，CB_ERR否則為 0。  
  
### <a name="remarks"></a>備註  
 下拉式方塊編輯控制項 （或靜態文字） 部分的高度是獨立的清單項目高度設定。 應用程式必須確定您的編輯控制項 （或靜態文字） 的部分的高度不小於特定的清單方塊項目的高度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>  CComboBox::SetLocale  
 設定此下拉式方塊的地區設定識別碼。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>參數  
 *nNewLocale*  
 要設定的下拉式方塊的新地區設定識別碼 (LCID) 值。  
  
### <a name="return-value"></a>傳回值  
 此下拉式方塊上一個地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 如果`SetLocale`不呼叫時，預設的地區設定從系統取得。 此系統預設地區設定可以修改使用 [控制台] 的區域 （或國際） 的應用程式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>  CComboBox::SetMinVisibleItems  
 設定可見的項目最小數目下拉式清單中的目前下拉式方塊控制項。  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*iMinVisible*|[in]指定可見的項目的數目下限。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[CB_SETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數*m_combobox*，也就是用來以程式設計方式存取下拉式方塊控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會插入下拉式方塊控制項的下拉式清單中的 20 個項目。 然後它會指定在使用者按下的下拉式箭號，顯示最少 10 個項目。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>  CComboBox::SetTopIndex  
 可確保特定項目會顯示在下拉式方塊的清單方塊部分。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定清單方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，為零或 CB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 系統會將清單方塊捲動直到其中一個所指定的項目*nIndex*會出現在清單頂端或最大捲軸範圍已達到。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>  CComboBox::ShowDropDown  
 顯示或隱藏清單方塊的下拉式方塊具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或是[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bShowIt*  
 指定是否要顯示或隱藏的下拉式清單方塊。 TRUE 值會顯示清單方塊。 值為 FALSE 會隱藏清單方塊。  
  
### <a name="remarks"></a>備註  
 根據預設，這個樣式的下拉式方塊會顯示在清單方塊。  
  
 此成員函式沒有任何作用，在建立與 seznamem [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
### <a name="example"></a>範例  
  範例，請參閱[CComboBox::GetDroppedState](#getdroppedstate)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLBARS](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton 類別](../../mfc/reference/cbutton-class.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)   
 [CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)   
 [CStatic 類別](../../mfc/reference/cstatic-class.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)
