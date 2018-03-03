---
title: "CComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fffa5c09f1572200ca7850c8870b7daee9e3e75f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|[Ccombobox:: Addstring](#addstring)|將字串新增至清單方塊的下拉式方塊或清單方塊的已排序資料的位置中的清單結尾**CBS_SORT**樣式。|  
|[CComboBox::Clear](#clear)|（清除） 會刪除目前選取範圍，如果有的話，在編輯控制項中。|  
|[CComboBox::CompareItem](#compareitem)|由架構呼叫以判斷新的清單項目已排序的主控描繪下拉式方塊中的相對位置。|  
|[CComboBox::Copy](#copy)|將目前的選取範圍複製到剪貼簿中的任何**CF_TEXT**格式。|  
|[CComboBox::Create](#create)|建立下拉式方塊，並將它附加至`CComboBox`物件。|  
|[CComboBox::Cut](#cut)|（剪下） 會刪除目前選取項目，如果編輯中的任何控制，並將複製到剪貼簿中刪除的文字**CF_TEXT**格式。|  
|[CComboBox::DeleteItem](#deleteitem)|從主控描繪下拉式方塊刪除清單項目時由架構呼叫。|  
|[CComboBox::DeleteString](#deletestring)|從下拉式方塊的清單方塊中，刪除字串。|  
|[CComboBox::Dir](#dir)|將下拉式方塊的清單方塊中的檔案名稱的清單。|  
|[CComboBox::DrawItem](#drawitem)|由架構描繪下拉式方塊中變更的視覺外觀時呼叫。|  
|[CComboBox::FindString](#findstring)|尋找包含指定的前置詞清單方塊的下拉式方塊中的第一個字串。|  
|[CComboBox::FindStringExact](#findstringexact)|尋找第一個清單方塊中的字串 （下拉式方塊），符合指定的字串。|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|擷取有關的資訊`CComboBox`物件。|  
|[CComboBox::GetCount](#getcount)|擷取清單方塊的下拉式方塊中的項目數目。|  
|[CComboBox::GetCueBanner](#getcuebanner)|取得下拉式方塊控制項中顯示的提示文字。|  
|[CComboBox::GetCurSel](#getcursel)|擷取索引的目前選取的項目，如果有的話，清單方塊的下拉式方塊中。|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|擷取可見的 （已向卸除） 清單方塊的下拉式清單方塊的螢幕座標。|  
|[CComboBox::GetDroppedState](#getdroppedstate)|決定下拉式方塊的清單方塊是否可見 （向下卸除）。|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|擷取最小允許下拉式方塊的下拉式清單方塊部分的寬度。|  
|[CComboBox::GetEditSel](#geteditsel)|取得下拉式方塊編輯控制項中目前的選取範圍的開始和結束的字元位置。|  
|[CComboBox::GetExtendedUI](#getextendedui)|決定下拉式方塊是否有預設的使用者介面或擴充的使用者介面。|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|下拉式方塊的清單方塊部分可以水平捲動的像素為單位傳回的寬度。|  
|[CComboBox::GetItemData](#getitemdata)|擷取與指定的下拉式方塊項目相關聯的應用程式提供 32 位元值。|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|擷取與指定的下拉式方塊項目相關聯的應用程式提供 32 位元指標。|  
|[CComboBox::GetItemHeight](#getitemheight)|擷取清單中的項目下拉式方塊的高度。|  
|[CComboBox::GetLBText](#getlbtext)|取得字串，從清單方塊的下拉式方塊。|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|取得下拉式方塊的清單方塊中的字串的長度。|  
|[CComboBox::GetLocale](#getlocale)|擷取下拉式方塊的地區設定識別碼。|  
|[CComboBox::GetMinVisible](#getminvisible)|取得目前的下拉式方塊的下拉式清單中的可見項目的最小數目。|  
|[CComboBox::GetTopIndex](#gettopindex)|下拉式方塊的清單方塊部分中傳回第一個可見項目的索引。|  
|[CComboBox::InitStorage](#initstorage)|Preallocates 項目和下拉式方塊的清單方塊部分中的字串的記憶體區塊。|  
|[CComboBox::InsertString](#insertstring)|將字串插入下拉式方塊的清單方塊中。|  
|[CComboBox::LimitText](#limittext)|限制使用者可以在編輯控制項的下拉式方塊中輸入文字的長度。|  
|[CComboBox::MeasureItem](#measureitem)|由架構呼叫以判斷何時建立主控描繪下拉式方塊的下拉式方塊的維度。|  
|[CComboBox::Paste](#paste)|從剪貼簿資料插入編輯控制項，在目前游標位置。 資料會插入剪貼簿包含資料時，才**CF_TEXT**格式。|  
|[CComboBox::ResetContent](#resetcontent)|移除所有項目從清單方塊，並編輯下拉式方塊控制項。|  
|[CComboBox::SelectString](#selectstring)|搜尋下拉式方塊的清單方塊中的字串，如果找到字串，清單方塊中選取字串，並將字串複製到編輯控制項。|  
|[CComboBox::SetCueBanner](#setcuebanner)|設定下拉式方塊控制項所顯示的提示文字。|  
|[CComboBox::SetCurSel](#setcursel)|選取清單方塊的下拉式方塊中的字串。|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|設定最小允許下拉式方塊的下拉式清單方塊部分的寬度。|  
|[CComboBox::SetEditSel](#seteditsel)|選取下拉式方塊編輯控制項中的字元。|  
|[CComboBox::SetExtendedUI](#setextendedui)|選取的預設使用者介面或具有下拉式方塊的擴充的使用者介面**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**樣式。|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|設定下拉式方塊的清單方塊部分可以水平捲動的像素為單位的寬度。|  
|[CComboBox::SetItemData](#setitemdata)|設定下拉式方塊中指定的項目相關聯的 32 位元值。|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|設定下拉式方塊中指定的項目相關聯的 32 位元指標。|  
|[CComboBox::SetItemHeight](#setitemheight)|在下拉式方塊或下拉式方塊編輯控制項 （或靜態文字） 部分的高度設定清單項目的高度。|  
|[CComboBox::SetLocale](#setlocale)|設定下拉式方塊的地區設定識別碼。|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|目前的下拉式方塊的下拉式清單中設定的最小的可見項目數目。|  
|[CComboBox::SetTopIndex](#settopindex)|會告知下拉式方塊，以顯示具有指定之索引的項目上方的清單方塊部分。|  
|[CComboBox::ShowDropDown](#showdropdown)|顯示或隱藏清單方塊的下拉式方塊具有**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**樣式。|  
  
## <a name="remarks"></a>備註  
 下拉式方塊清單方塊與靜態控制項或編輯控制項組合所組成。 控制項的清單方塊部分可能會隨時顯示，或當使用者選取在控制項旁邊的下拉式箭號可能只有下拉式清單。  
  
 目前選取的項目 （如果有的話） 清單方塊中會顯示在靜態，或編輯控制項。 此外，如果下拉式方塊的下拉式清單樣式，使用者可以在清單中，輸入的起始字元的其中一個項目和清單方塊中，如果可以看見，會反白顯示下一個項目，該初始的字元。  
  
 下表比較三個下拉式方塊[樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。  
  
|樣式|當清單方塊是可見的嗎|靜態或編輯控制項|  
|-----------|-------------------------------|-----------------------------|  
|簡單|永遠|Edit|  
|Drop-down|卸除時|Edit|  
|下拉式清單|卸除時|Static|  
  
 您可以建立`CComboBox`從對話方塊範本，或直接在您的程式碼中的物件。 在這兩種情況下，第一次呼叫建構函式`CComboBox`建構`CComboBox`物件; 然後呼叫[建立](#create)成員函式來建立控制項並將其附加至`CComboBox`物件。  
  
 如果您想要處理 Windows 通知訊息傳送至其父代下拉式方塊 (通常的類別衍生自`CDialog`)，將訊息對應項目和訊息處理常式成員函式加入至每個訊息的父類別。  
  
 每個訊息對應項目有下列形式：  
  
 **ON_**通知**(**`id`**，**`memberFxn`**)**  
  
 其中`id`指定傳送通知的下拉式方塊控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 在父系的函式原型如下所示：  
  
 **afx_msg** `void` `memberFxn` **（);**  
  
 無法預測會傳送特定通知的順序。 特別是， **CBN_SELCHANGE**之前或之後，可能會發生通知**CBN_CLOSEUP**通知。  
  
 可能的訊息對應項目如下所示：  
  
- **ON_CBN_CLOSEUP** (Windows 3.1 和更新版本。)清單方塊的下拉式方塊已關閉。 這項通知訊息不會傳送具有下拉式方塊[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
- **ON_CBN_DBLCLK**使用者按兩下下拉式方塊的清單方塊中的字串。 這項通知訊息才會傳送具有下拉式清單方塊**CBS_SIMPLE**樣式。 下拉式方塊與[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，按兩下不會發生因為只要按一下隱藏清單方塊。  
  
- **ON_CBN_DROPDOWN**即將下拉式清單方塊的下拉式方塊 （可變成可見）。 這項通知訊息可以只針對發生與下拉式方塊**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**樣式。  
  
- **ON_CBN_EDITCHANGE**使用者採取的動作，可能已更改下拉式方塊編輯控制項部分中的文字。 不同於**CBN_EDITUPDATE**訊息時，此訊息會傳送後 Windows 更新的畫面。 不會傳送下拉式方塊是否**CBS_DROPDOWNLIST**樣式。  
  
- **ON_CBN_EDITUPDATE**下拉式方塊編輯控制項部分即將顯示變更的文字。 這項通知訊息會傳送控制項已格式化文字，但它會顯示文字之前。 不會傳送下拉式方塊是否**CBS_DROPDOWNLIST**樣式。  
  
- **ON_CBN_ERRSPACE**下拉式方塊無法配置足夠的記憶體，以符合特定的要求。  
  
- **ON_CBN_SELENDCANCEL** (Windows 3.1 和更新版本。)指出應該取消使用者的選取項目。 使用者按一下的項目，然後按一下另一個視窗或隱藏下拉式方塊的清單方塊的控制項。 這項通知訊息之前傳送**CBN_CLOSEUP**表示應該忽略使用者選取的通知訊息。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**會傳送通知訊息，即使**CBN_CLOSEUP**不會傳送通知訊息 (如果與下拉式方塊是做為**CBS_SIMPLE**樣式)。  
  
- **ON_CBN_SELENDOK**使用者選取的項目，然後按下 ENTER 鍵或按一下向下鍵來隱藏下拉式方塊的清單方塊。 這項通知訊息之前傳送**CBN_CLOSEUP**訊息以指出該使用者的選取項目應該被視為有效。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**會傳送通知訊息，即使**CBN_CLOSEUP**不會傳送通知訊息 (如果與下拉式方塊是做為**CBS_SIMPLE**樣式)。  
  
- **ON_CBN_KILLFOCUS**下拉式方塊正失去輸入的焦點。  
  
- **ON_CBN_SELCHANGE**下拉式方塊的清單方塊中的選擇是即將變更使用者按一下清單方塊中，或使用方向鍵來變更選取範圍的結果。 在處理此訊息時，下拉式方塊編輯控制項中的文字只擷取透過`GetLBText`或另一個類似的函式。 `GetWindowText`無法使用。  
  
- **ON_CBN_SETFOCUS**下拉式方塊會收到輸入的焦點。  
  
 如果您建立`CComboBox`物件 （透過對話方塊資源），對話方塊內`CComboBox`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您將內嵌`CComboBox`物件在另一個視窗中的物件，您不需要終結。 如果您建立`CComboBox`物件在堆疊上，會自動終結。 如果您建立`CComboBox`使用堆積上的物件**新**函式，您必須呼叫**刪除**物件終結時終結 Windows 下拉式方塊。  
  
 **請注意**如果您想要處理`WM_KEYDOWN`和`WM_CHAR`訊息，您有子類別化下拉式方塊的編輯和清單方塊控制項中，衍生類別，從`CEdit`和`CListBox`，並將這些訊息的處理常式加入至衍生類別。 如需詳細資訊，請參閱[http://support.microsoft.com/default.aspxscid=kb;en-us;Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667)和[CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="addstring"></a>Ccombobox:: Addstring  
 將字串新增至清單方塊的下拉式方塊。  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 `lpszString`  
 指向以 null 結束的字串被加入。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是大於或等於 0，則以零為起始的索引清單方塊中的字串。 傳回值是**CB_ERR**如果發生錯誤。 傳回的值是**CB_ERRSPACE**如果空間不足，無法使用存放新的字串。  
  
### <a name="remarks"></a>備註  
 如果不使用建立清單方塊[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，字串會新增至清單的結尾。 否則，字串會插入清單中，而且排序清單。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
 若要將字串插入清單中的特定位置，使用[InsertString](#insertstring)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>CComboBox::CComboBox  
 建構 `CComboBox` 物件。  
  
```  
CComboBox();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>CComboBox::Clear  
 （清除） 會刪除目前選取範圍，如果有的話，在下拉式方塊編輯控制項中。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 若要刪除目前選取範圍，並放置到剪貼簿內容已刪除，請使用[剪下](#cut)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CComboBox::CompareItem  
 由架構呼叫以判斷新的項目已排序的主控描繪下拉式方塊的清單方塊部分中的相對位置。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpCompareItemStruct`  
 長指標[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)結構。  
  
### <a name="return-value"></a>傳回值  
 表示兩個項目中所述的相對位置`COMPAREITEMSTRUCT`結構。 它可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|- 1|項目 1 排序項目 2 之前。|  
|0|項目 1 和 2 的項目排序相同。|  
|1|項目 1 排序項目 2 之後。|  
  
 請參閱[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)的說明`COMPAREITEMSTRUCT`。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 如果您建立主控描繪下拉式方塊**LBS_SORT**樣式，您必須覆寫此成員函式，以協助架構排序加入至清單方塊的新項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>CComboBox::Copy  
 將目前的選取項目，複製到剪貼簿中的下拉式方塊編輯控制項中的任何**CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="create"></a>CComboBox::Create  
 建立下拉式方塊，並將它附加至`CComboBox`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定下拉式方塊樣式。 套用的任何組合[下拉式方塊樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)到方塊。  
  
 `rect`  
 指向的位置和大小的下拉式方塊。 可以是[RECT 結構](../../mfc/reference/rect-structure1.md)或`CRect`物件。  
  
 `pParentWnd`  
 指定下拉式方塊的父視窗 (通常`CDialog`)。 它不得為**NULL**。  
  
 `nID`  
 指定下拉式方塊的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CComboBox`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫**建立**，建立 Windows 下拉式方塊，並將它附加至`CComboBox`物件。  
  
 當**建立**執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)下拉式方塊的訊息。  
  
 這些訊息會由預設的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式在`CWnd`基底類別。 若要擴充的預設訊息處理，衍生自`CComboBox`、 將訊息對應新增到新的類別，並覆寫先前的訊息處理常式成員函式。 覆寫`OnCreate`，例如，若要執行所需的初始化新的類別。  
  
 套用下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)至下拉式方塊控制項。 :  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**新增垂直捲動功能的清單方塊中的下拉式方塊  
  
- **WS_HSCROLL**来加入的清單方塊的下拉式方塊中的水平捲軸  
  
- **WS_GROUP**群組控制項  
  
- **WS_TABSTOP** tab 鍵順序中包含下拉式方塊  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>CComboBox::Cut  
 刪除 （剪下） 目前選取項目，如果在下拉式方塊中的任何編輯控制，並將複製到剪貼簿中刪除的文字**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>備註  
 若要刪除目前選取範圍，而不會讓刪除的文字到剪貼簿，呼叫[清除](#clear)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>CComboBox::DeleteItem  
 當使用者從主控描繪刪除項目時由架構呼叫`CComboBox`物件或終結下拉式方塊。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDeleteItemStruct`  
 Windows 的長指標[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)結構，其中包含已刪除項目的相關資訊。 請參閱[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)此結構描述。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫此函式以視需要重繪下拉式方塊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>CComboBox::DeleteString  
 刪除位置中的項目`nIndex`從下拉式方塊。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要刪除之字串的索引。  
  
### <a name="return-value"></a>傳回值  
 如果傳回的值大於或等於 0，它是字串清單中所剩餘的計數。 傳回值是**CB_ERR**如果`nIndex`指定索引的項目數大於清單中。  
  
### <a name="remarks"></a>備註  
 之後的所有項目`nIndex`現在下移一個位置。 例如，如果下拉式方塊包含兩個項目，刪除第一個項目會導致要現在會在第一個位置中的剩餘項目。 `nIndex`= 0，第一個位置中的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>CComboBox::Dir  
 將下拉式方塊的清單方塊中的檔案名稱或磁碟機的清單。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>參數  
 `attr`  
 可以是任何組合的`enum`值中所述[Getstatus](../../mfc/reference/cfile-class.md#getstatus)或下列值的任何組合：  
  
- **DDL_READWRITE**讀取或寫入檔案。  
  
- **DDL_READONLY**可以讀取但不是會寫入檔案。  
  
- **DDL_HIDDEN**檔案隱藏的因此不會出現在目錄清單中。  
  
- **DDL_SYSTEM**檔案是系統檔案。  
  
- **DDL_DIRECTORY**所指定的名稱`lpszWildCard`指定的目錄。  
  
- **DDL_ARCHIVE**在封存檔案。  
  
- **DDL_DRIVES**包含比對所指定之名稱的所有磁碟機`lpszWildCard`。  
  
- **DDL_EXCLUSIVE** Exclusive 旗標。 如果設定 exclusive 旗標，會列出指定類型的檔案。 否則，會列出指定之型別的的檔案，除了 「 標準 」 檔案。  
  
 `lpszWildCard`  
 指向檔案規格字串。 字串可以包含萬用字元 (例如，*。\*)。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是大於或等於 0，則最後一個檔案名稱加入至清單的以零為起始的索引。 傳回值是**CB_ERR**如果發生錯誤。 傳回的值是**CB_ERRSPACE**空間不足，無法是否可用來儲存新的字串。  
  
### <a name="remarks"></a>備註  
 Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>CComboBox::DrawItem  
 當主控描繪下拉式方塊中變更的視覺外觀時，架構呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)此結構描述。  
  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作主控描繪的繪圖`CComboBox`物件。 此成員函式會終止之前，應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>CComboBox::FindString  
 找到，但不會選取第一個字串，其中包含指定的清單方塊的下拉式方塊中的前置詞。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到清單方塊底端時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 如果-1，會將整個清單方塊搜尋開頭。  
  
 `lpszString`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是大於或等於 0，則相符的項目以零為起始索引。 它是**CB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>CComboBox::FindStringExact  
 呼叫`FindStringExact`尋找第一個清單方塊中的字串 （下拉式方塊），會比對字串中指定的成員函式`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndexStart`  
 指定要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到清單方塊底端時，它會繼續從清單方塊的上方回所指定的項目`nIndexStart`。 如果`nIndexStart`為-1，整個清單方塊會從一開始搜尋。  
  
 `lpszFind`  
 指向以 null 結束的字串搜尋。 這個字串可以包含完整的檔名，包括副檔名。 搜尋不區分大小寫，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 相符的項目以零為起始索引或**CB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 如果使用下拉式方塊但無需建立主控描繪樣式[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，`FindStringExact`會嘗試比對的值的 doubleword 值`lpszFind`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo  
 擷取資訊`CComboBox`物件。  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>參數  
 *pcbi*  
 指標[COMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775798)結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[CB_GETCOMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775839)訊息、 Windows SDK 中所述。  
  
##  <a name="getcount"></a>CComboBox::GetCount  
 呼叫此成員函式可擷取的下拉式方塊的清單方塊部分中的項目數。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 項目數目。 傳回的計數是比最後一個項目 （索引以零為起始） 的索引值大一。 它是**CB_ERR**如果發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="getcuebanner"></a>CComboBox::GetCueBanner  
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
|[輸出] `lpszText`|收到的提示橫幅文字的緩衝區指標。|  
|[輸入] `cchText`|緩衝區的大小，`lpszText`參數所指向。|  
  
### <a name="return-value"></a>傳回值  
 在第一個多載， [CString](../../atl-mfc-shared/using-cstring.md)物件，其中包含提示橫幅文字，如果它存在，否則`CString`長度為零的物件。  
  
 -或-  
  
 在第二個多載，`true`如果此方法成功，否則`false`。  
  
### <a name="remarks"></a>備註  
 提示文字會顯示下拉式方塊控制項的輸入區域中的提示。 提示文字會顯示，直到使用者提供輸入。  
  
 這個方法會傳送[CB_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775843) Windows SDK 中所述的訊息。  
  
##  <a name="getcursel"></a>CComboBox::GetCurSel  
 呼叫此成員函式，來決定要選取哪一個下拉式方塊中的項目。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊的下拉式方塊中目前選取之項目的以零為起始的索引或**CB_ERR**如果不選取任何項目。  
  
### <a name="remarks"></a>備註  
 `GetCurSel`傳回清單中的索引。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect  
 呼叫`GetDroppedControlRect`成員函式來擷取可見 （卸除下） 的清單方塊的下拉式清單方塊的螢幕座標。  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>參數  
 *lprect*  
 指向[RECT 結構](../../mfc/reference/rect-structure1.md)要接收的座標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>CComboBox::GetDroppedState  
 呼叫`GetDroppedState`成員函式以決定清單方塊的下拉式清單方塊是否顯示 （向下卸除）。  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果清單方塊中是可見的。否則便是 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth  
 呼叫此函式可擷取的最小的允許寬度，以像素的下拉式方塊的清單方塊。  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，可允許寬度下限，以像素為單位。否則， **CB_ERR**。  
  
### <a name="remarks"></a>備註  
 此函式僅適用於下拉式方塊和[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
 根據預設，下拉式清單方塊中允許的最小寬度是 0。 允許的最小寬度可以藉由呼叫設定[SetDroppedWidth](#setdroppedwidth)。 下拉式方塊的清單方塊部分會顯示，其寬度時，較大的可允許的最小寬度或下拉式方塊的寬度。  
  
### <a name="example"></a>範例  
  請參閱範例的[SetDroppedWidth](#setdroppedwidth)。  
  
##  <a name="geteditsel"></a>CComboBox::GetEditSel  
 取得下拉式方塊編輯控制項中目前的選取範圍的開始和結束的字元位置。  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 32 位元值，其中包含高序位文字中的選取範圍結尾之後的低序位字組中的開始位置和未選取的第一個字元的位置。 如果在下拉式方塊編輯控制項，不使用這個函式**CB_ERR**傳回。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>CComboBox::GetExtendedUI  
 呼叫`GetExtendedUI`判斷下拉式方塊是否有預設的使用者介面或擴充的使用者介面的成員函式。  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果下拉式方塊具有擴充的使用者介面; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 擴充的使用者介面可以識別下列方式：  
  
-   按一下靜態控制項顯示僅針對下拉式方塊和清單方塊[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
-   按向下鍵，就會顯示清單方塊 （已停用 F4）。  
  
 在靜態控制項中捲動時，停用項目清單是不可見 （箭號會停用索引鍵）。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent  
 擷取從下拉式方塊的下拉式方塊的清單方塊部分可以水平捲動的像素為單位的寬度。  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊的 像素為單位的清單方塊部分的可捲動的寬度。  
  
### <a name="remarks"></a>備註  
 這是下拉式方塊的清單方塊部分有水平捲軸時，才適用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>CComboBox::GetItemData  
 擷取與指定的下拉式方塊項目相關聯的應用程式提供 32 位元值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含下拉式方塊的清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 項目，與關聯的 32 位元值或**CB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 32 位元值可以設定與`dwItemData`參數[SetItemData](#setitemdata)成員函式呼叫。 使用`GetItemDataPtr`成員函式，如果要擷取的 32 位元值是指標 ( **void\***)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>CComboBox::GetItemDataPtr  
 擷取應用程式提供 32 位元與關聯的值做為指標指定的下拉式方塊項目 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含下拉式方塊的清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 擷取是指標，則為-1，如果發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>CComboBox::GetItemHeight  
 呼叫`GetItemHeight`成員函式來擷取清單中的項目下拉式方塊的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定下拉式方塊的高度是要擷取的元件。 如果`nIndex`參數為-1，將會擷取下拉式方塊編輯控制項 （或靜態文字） 部分的高度。 如果下拉式方塊擁有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，`nIndex`指定其高度是要擷取之清單項目的以零為起始的索引。 否則，`nIndex`應該設定為 0。  
  
### <a name="return-value"></a>傳回值  
 高度 （以像素的方塊中指定的項目）。 如果發生錯誤，傳回值是 **CB_ERR** 。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>CComboBox::GetLBText  
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
 `nIndex`  
 包含要複製的清單方塊字串以零為起始的索引。  
  
 `lpszText`  
 指向要接收字串緩衝區。 緩衝區必須有足夠的空間，如字串和結束的 null 字元。  
  
 `rString`  
 若要參考`CString`。  
  
### <a name="return-value"></a>傳回值  
 字串，但不包括結束的 null 字元的長度 （以位元組為單位）。 如果`nIndex`未指定有效的索引，則傳回值是**CB_ERR**。  
  
### <a name="remarks"></a>備註  
 這個成員的第二個表單函式的填滿`CString`物件項目的文字。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>CComboBox::GetLBTextLen  
 取得下拉式方塊的清單方塊中的字串的長度。  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含清單方塊字串之以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 以位元組為單位，但不包括結束的 null 字元字串的長度。 如果`nIndex`未指定有效的索引，則傳回值是**CB_ERR**。  
  
### <a name="example"></a>範例  
  請參閱範例的[CComboBox::GetLBText](#getlbtext)。  
  
##  <a name="getlocale"></a>CComboBox::GetLocale  
 擷取使用下拉式方塊的地區設定。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊中的字串，地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 會使用地區設定，例如，以決定排序次序的排序的下拉式方塊中的字串。  
  
### <a name="example"></a>範例  
  請參閱範例的[CComboBox::SetLocale](#setlocale)。  
  
##  <a name="getminvisible"></a>CComboBox::GetMinVisible  
 在目前的下拉式方塊控制項下拉式清單中取得的最小的可見項目數目。  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的下拉式清單中的可見項目的最小數目。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[CB_GETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) Windows SDK 中所述的訊息。  
  
##  <a name="gettopindex"></a>CComboBox::GetTopIndex  
 擷取的下拉式方塊的清單方塊部分中的第一個可見項目以零為起始的索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，下拉式方塊的清單方塊部分中的第一個可見項目以零為起始索引**CB_ERR**否則。  
  
### <a name="remarks"></a>備註  
 一開始，項目 0 頂端的清單方塊中，但如果捲動清單方塊，另一個項目可能會在頂端。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>CComboBox::InitStorage  
 將清單方塊項目儲存在下拉式方塊的清單方塊部分會配置記憶體。  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>參數  
 `nItems`  
 指定要加入項目數目。  
  
 `nBytes`  
 指定的記憶體數量，以位元組為單位，來配置項目的字串。  
  
### <a name="return-value"></a>傳回值  
 如果成功，最大數目的項目下拉式方塊的清單方塊部分可以儲存之前需要的記憶體配置，否則**CB_ERRSPACE**，這表示沒有足夠的記憶體可用。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之前加入的清單方塊部分中的項目數量龐大`CComboBox`。  
  
 只有 Windows 95/98:`wParam`參數會限制為 16 位元值。 這表示清單方塊不能包含超過 32,767 個項目。 雖然項目數目有限制，在清單方塊中項目的總大小只會受到可用記憶體。  
  
 此函式可協助加速有大量的項目 (超過 100) 的清單方塊的初始化。 它 preallocates 讓後續的記憶體數量指定[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函式接受最短的時間。 您可以使用估計值的參數。 如果增長時，會配置一些額外的記憶體。如果您低估，超過預先配置的量的項目使用一般配置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>CComboBox::InsertString  
 將字串插入下拉式方塊的清單方塊中。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含要接收字串之清單方塊中位置以零為基底的索引。 如果這個參數是-1，則會將字串加入至清單的結尾。  
  
 `lpszString`  
 指向要插入的 null 結尾字串。  
  
### <a name="return-value"></a>傳回值  
 已插入字串之位置以零為基底的索引。 如果發生錯誤，傳回值是 **CB_ERR** 。 如果空間不足，無法存放新的字串，傳回值是 **CB_ERRSPACE** 。  
  
### <a name="remarks"></a>備註  
 不同於[AddString](#addstring)成員函式，`InsertString`成員函式不會造成與清單[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)排序樣式。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>CComboBox::LimitText  
 限制使用者可以在編輯控制項的下拉式方塊中輸入的文字長度以位元組為單位。  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>參數  
 `nMaxChars`  
 指定使用者可以輸入文字的長度 （以位元組為單位）。 這個參數是 0，如果文字長度會設定為 65535 個位元組。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零。 如果呼叫的樣式組合方塊[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或沒有編輯控制項下拉式清單方塊，則傳回值是**CB_ERR**。  
  
### <a name="remarks"></a>備註  
 如果下拉式方塊中沒有樣式[CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)，設定文字限制為大於編輯控制項的大小不會有任何作用。  
  
 `LimitText`只會限制使用者可以輸入的文字。 它不會影響任何文字中已有此編輯控制項時傳送訊息，也不會影響在選取清單方塊中的字串時複製到編輯控制項文字的長度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>CComboBox::MeasureItem  
 建立主控描繪樣式與下拉式方塊時由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpMeasureItemStruct`  
 長指標[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，並填寫`MEASUREITEMSTRUCT`通知清單的維度的 Windows 方塊下拉式方塊中的結構。 如果下拉式方塊以建立[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，架構會呼叫此成員函式的清單方塊中的每個項目。 否則，這個成員是只能呼叫一次。  
  
 使用**CBS_OWNERDRAWFIXED**中建立主控描繪下拉式方塊樣式[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成員函式`CWnd`涉及進一步程式設計考量。 請參閱[技術附註 14](../../mfc/tn014-custom-controls.md)。  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>CComboBox::Paste  
 從剪貼簿資料插入在目前游標位置下拉式方塊編輯控制項。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>備註  
 資料會插入剪貼簿包含資料時，才**CF_TEXT**格式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>CComboBox::ResetContent  
 移除所有項目從清單方塊，並編輯下拉式方塊控制項。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>CComboBox::SelectString  
 搜尋字串的下拉式方塊中，清單方塊中，如果找到字串，清單方塊中選取字串，並將它複製到編輯控制項。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到清單方塊底端時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 如果-1，會將整個清單方塊搜尋開頭。  
  
 `lpszString`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 如果找不到字串的選取項目以零為起始的索引。 如果搜尋成功，則傳回值是**CB_ERR**且不會變更目前的選取範圍。  
  
### <a name="remarks"></a>備註  
 只有當其初始的字元 （從起點） 符合前置詞字串中的字元，會選取字串。  
  
 請注意，`SelectString`和`FindString`成員函數會尋找字串，但`SelectString`成員函式也會選取字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>CComboBox::SetCueBanner  
 設定下拉式方塊控制項所顯示的提示文字。  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*lpszText*|指向以 null 結尾的緩衝區，其中包含提示文字。|  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 提示文字會顯示下拉式方塊控制項的輸入區域中的提示。 提示文字會顯示，直到使用者提供輸入。  
  
 這個方法會傳送[CB_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775897) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_combobox`，也就是用來以程式設計方式存取下拉式方塊控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定下拉式方塊控制項的提示橫幅。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>CComboBox::SetCurSel  
 選取清單方塊的下拉式方塊中的字串。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>參數  
 `nSelect`  
 指定要選取之字串的以零為起始的索引。 如果-1，會移除任何目前的選取清單方塊中，並清除編輯控制項。  
  
### <a name="return-value"></a>傳回值  
 選取訊息是否成功的項目以零為起始的索引。 傳回值是**CB_ERR**如果`nSelect`大於清單中的項目數或`nSelect`設為-1，這會清除選取項目。  
  
### <a name="remarks"></a>備註  
 如有必要，清單方塊顯示出來的字串 （如果清單方塊會顯示）。 下拉式方塊編輯控制項中的文字會變更以反映新的選取範圍。 會移除任何先前的選取清單方塊中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth  
 呼叫此函式可設定的最小的允許寬度，以像素的下拉式方塊的清單方塊。  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 下拉式方塊的 像素為單位的清單方塊部分允許最小寬度。  
  
### <a name="return-value"></a>傳回值  
 如果成功，新寬度的清單方塊中，否則**CB_ERR**。  
  
### <a name="remarks"></a>備註  
 此函式僅適用於下拉式方塊和[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
 根據預設，下拉式清單方塊中允許的最小寬度是 0。 下拉式方塊的清單方塊部分會顯示，其寬度時，較大的可允許的最小寬度或下拉式方塊的寬度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>CComboBox::SetEditSel  
 選取下拉式方塊編輯控制項中的字元。  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>參數  
 `nStartChar`  
 指定的開始位置。 如果開始位置設定為-1，則會移除任何現有的選取範圍。  
  
 `nEndChar`  
 指定的結束位置。 如果最後一個結束的位置設定為-1，然後的所有文字的開始位置選取編輯控制項中的字元。  
  
### <a name="return-value"></a>傳回值  
 如果此成員函式成功，則為非零否則便是 0。 它是**CB_ERR**如果`CComboBox`具有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，或沒有清單方塊。  
  
### <a name="remarks"></a>備註  
 位置是以零為起始的。 若要選取編輯控制項的第一個字元，您可以指定 0 的開始位置。 結束位置為只在選取的最後一個字元之後的字元。 例如，若要選取編輯控制項的前四個字元，您會使用 0 的開始位置和結束位置的 4。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CComboBox::GetEditSel](#geteditsel)。  
  
##  <a name="setextendedui"></a>CComboBox::SetExtendedUI  
 呼叫`SetExtendedUI`選取預設的使用者介面或具有下拉式方塊的擴充的使用者介面的成員函式[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bExtended*  
 指定下拉式方塊是否應該使用擴充的使用者介面或預設的使用者介面。 值為**TRUE**選取擴充使用者介面，而值**FALSE**選取的標準使用者介面。  
  
### <a name="return-value"></a>傳回值  
 **CB_OKAY**如果作業成功，或**CB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 擴充的使用者介面可以識別下列方式：  
  
-   按一下靜態控制項顯示僅針對下拉式方塊和清單方塊**CBS_DROPDOWNLIST**樣式。  
  
-   按向下鍵，就會顯示清單方塊 （已停用 F4）。  
  
 在靜態控制項中捲動時，停用項目清單是不可見 （方向鍵會停用）。  
  
### <a name="example"></a>範例  
  請參閱範例的[CComboBox::GetExtendedUI](#getextendedui)。  
  
##  <a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent  
 設定寬度，單位為像素的下拉式方塊的清單方塊部分可以水平捲動。  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>參數  
 *nExtent*  
 指定之下拉式方塊的清單方塊部分可以水平捲動的像素數目。  
  
### <a name="remarks"></a>備註  
 如果清單方塊的寬度小於此值，水平捲軸會水平捲動清單方塊中的項目。 如果清單方塊的寬度是等於或大於此值，會隱藏水平捲軸或下拉式方塊擁有[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，停用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>CComboBox::SetItemData  
 設定下拉式方塊中指定的項目相關聯的 32 位元值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含要設定之項目的以零為起始的索引。  
  
 `dwItemData`  
 包含與項目相關聯的新值。  
  
### <a name="return-value"></a>傳回值  
 **CB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 使用`SetItemDataPtr`32 位元的項目是否為指標的成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>CComboBox::SetItemDataPtr  
 設定指定下拉式方塊中的指定指標的項目相關聯的 32 位元值 ( **void\***)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含的項目以零為起始的索引。  
  
 `pData`  
 包含與項目相關聯的指標。  
  
### <a name="return-value"></a>傳回值  
 **CB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 此指標都是有效的存留期間的下拉式方塊中，即使在下拉式方塊的項目相對位置可能會變更為新增或移除項目。 因此，可以變更方塊內項目的索引，但指標都可靠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>CComboBox::SetItemHeight  
 呼叫`SetItemHeight`成員函式中的下拉式方塊或下拉式方塊編輯控制項 （或靜態文字） 部分的高度設定的清單項目高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要設定的清單項目高度或下拉式方塊編輯控制項 （或靜態文字） 部分的高度。  
  
 如果下拉式方塊擁有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，`nIndex`指定要設定，否則則為其高度的清單項目的以零為起始的索引`nIndex`必須是 0 和所有清單項目將會設定的高度。  
  
 如果`nIndex`為-1，編輯控制項的高度或下拉式方塊的靜態文字部分設定。  
  
 `cyItemHeight`  
 指定的高度，單位為像素所識別的下拉式方塊元件`nIndex`。  
  
### <a name="return-value"></a>傳回值  
 **CB_ERR**如果索引或高度無效，否則為 0。  
  
### <a name="remarks"></a>備註  
 下拉式方塊編輯控制項 （或靜態文字） 部分的高度是獨立的清單項目高度設定。 應用程式必須確定編輯控制項 （或靜態文字） 部分的高度不小於特定的清單方塊項目的高度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>CComboBox::SetLocale  
 設定下拉式方塊的地區設定識別碼。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>參數  
 `nNewLocale`  
 要設定的下拉式方塊的新的地區設定識別碼 (LCID) 值。  
  
### <a name="return-value"></a>傳回值  
 先前的地區設定識別碼 (LCID) 值的下拉式方塊。  
  
### <a name="remarks"></a>備註  
 如果**SetLocale**不呼叫時，預設的地區設定從系統取得。 可以修改此系統的預設地區設定，使用 [控制台] 的地區 （或國際標準） 的應用程式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems  
 設定的最小數目的可見項目在目前的下拉式方塊的下拉式清單方塊控制項中。  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iMinVisible`|指定的最小的可見項目數目。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[CB_SETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_combobox`，也就是用來以程式設計方式存取下拉式方塊控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會將 20 個項目插入下拉式方塊控制項的下拉式清單。 然後它會指定當使用者按下的下拉式箭號，顯示最少 10 個項目。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>CComboBox::SetTopIndex  
 可確保特定項目會顯示在下拉式方塊的清單方塊部分。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定清單方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，零或**CB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 系統會將清單方塊捲動直到其中一個所指定的項目`nIndex`會出現在清單頂端或最大捲軸範圍已達到。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>CComboBox::ShowDropDown  
 顯示或隱藏清單方塊的下拉式方塊具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bShowIt*  
 指定是否要顯示或隱藏的下拉式清單方塊。 值為**TRUE**顯示清單方塊。 值為**FALSE**隱藏清單方塊。  
  
### <a name="remarks"></a>備註  
 根據預設，此樣式的下拉式方塊會顯示清單方塊。  
  
 此成員函式沒有任何作用，以建立下拉式方塊上的[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式。  
  
### <a name="example"></a>範例  
  請參閱範例的[CComboBox::GetDroppedState](#getdroppedstate)。  
  
## <a name="see-also"></a>請參閱  
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
