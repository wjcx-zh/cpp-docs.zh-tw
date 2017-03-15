---
title: "CComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBox
dev_langs:
- C++
helpviewer_keywords:
- combo boxes, CComboBox objects
- CComboBox class
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
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
ms.openlocfilehash: 5328c245e0d662c4701042b37c16870d6b1e33c7
ms.lasthandoff: 02/24/2017

---
# <a name="ccombobox-class"></a>CComboBox 類別
提供 Windows 下拉式方塊的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CComboBox : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComboBox::CComboBox](#ccombobox)|建構 `CComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Ccombobox:: Addstring](#addstring)|將字串加入至清單方塊的下拉式方塊或清單方塊的已排序資料的位置中的清單結尾**CBS_SORT**樣式。|  
|[CComboBox::Clear](#clear)|（清除） 會刪除目前選取項目，如果編輯控制項中的任何。|  
|[CComboBox::CompareItem](#compareitem)|若要判斷新清單項目的已排序的主控描繪下拉式方塊中的相對位置架構呼叫。|  
|[CComboBox::Copy](#copy)|將目前的選取範圍複製到剪貼簿中的任何**CF_TEXT**格式。|  
|[CComboBox::Create](#create)|建立下拉式方塊，並將它附加`CComboBox`物件。|  
|[CComboBox::Cut](#cut)|（剪下） 中刪除目前選取項目，如果編輯中的任何控制項，並複製到剪貼簿中刪除的文字**CF_TEXT**格式。|  
|[CComboBox::DeleteItem](#deleteitem)|從主控描繪下拉式方塊刪除清單項目時，由架構呼叫。|  
|[CComboBox::DeleteString](#deletestring)|刪除從清單方塊的下拉式方塊的字串。|  
|[CComboBox::Dir](#dir)|將下拉式方塊的清單方塊中的檔案名稱的清單。|  
|[CComboBox::DrawItem](#drawitem)|架構變更為主控描繪下拉式方塊的視覺外觀時呼叫。|  
|[CComboBox::FindString](#findstring)|尋找包含在清單方塊的下拉式方塊中指定的前置詞的第一個字串。|  
|[CComboBox::FindStringExact](#findstringexact)|尋找第一個清單方塊中的字串 （下拉式方塊），符合指定的字串。|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|擷取有關的資訊`CComboBox`物件。|  
|[CComboBox::GetCount](#getcount)|擷取清單方塊的下拉式方塊中的項目數。|  
|[CComboBox::GetCueBanner](#getcuebanner)|取得下拉式方塊控制項中顯示的提示文字。|  
|[CComboBox::GetCurSel](#getcursel)|如果下拉式方塊的清單方塊中的任何，擷取目前選取項目的索引。|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|擷取可見 （卸除向下） 的清單方塊的下拉式清單方塊的螢幕座標。|  
|[CComboBox::GetDroppedState](#getdroppedstate)|決定清單方塊的下拉式清單方塊是否顯示 （落下）。|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|擷取的最小允許下拉式方塊的下拉式清單方塊部分的寬度。|  
|[CComboBox::GetEditSel](#geteditsel)|取得編輯控制項的下拉式方塊中目前的選取範圍的開始和結束的字元位置。|  
|[CComboBox::GetExtendedUI](#getextendedui)|決定下拉式方塊是否有預設的使用者介面或擴充的使用者介面。|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|傳回下拉式方塊的清單方塊部分可以水平捲動的像素為單位的寬度。|  
|[CComboBox::GetItemData](#getitemdata)|擷取與指定的下拉式方塊項目相關聯的應用程式提供 32 位元值。|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|擷取與指定的下拉式方塊項目相關聯的應用程式提供 32 位元指標。|  
|[CComboBox::GetItemHeight](#getitemheight)|擷取清單項目，在下拉式方塊的高度。|  
|[CComboBox::GetLBText](#getlbtext)|取得字串，請從清單方塊的下拉式方塊。|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|取得清單方塊的下拉式方塊中的字串的長度。|  
|[CComboBox::GetLocale](#getlocale)|擷取下拉式方塊的地區設定識別項。|  
|[CComboBox::GetMinVisible](#getminvisible)|在目前的下拉式方塊的下拉式清單中取得的最小的可見項目數目。|  
|[CComboBox::GetTopIndex](#gettopindex)|下拉式方塊的清單方塊部分中，傳回第一個可見項目的索引。|  
|[CComboBox::InitStorage](#initstorage)|預先配置時項目和下拉式方塊的清單方塊部分中的字串的記憶體的區塊。|  
|[CComboBox::InsertString](#insertstring)|將字串插入下拉式方塊的清單方塊中。|  
|[CComboBox::LimitText](#limittext)|限制使用者可以輸入下拉式方塊的編輯控制項中文字的長度。|  
|[CComboBox::MeasureItem](#measureitem)|若要判斷下拉式方塊的維度，建立主控描繪下拉式方塊時架構呼叫。|  
|[CComboBox::Paste](#paste)|從剪貼簿資料插入目前游標位置的編輯控制項。 資料會插入剪貼簿中包含的資料時，才**CF_TEXT**格式。|  
|[CComboBox::ResetContent](#resetcontent)|移除所有項目從清單方塊和下拉式方塊控制項的編輯。|  
|[CComboBox::SelectString](#selectstring)|搜尋字串清單方塊的下拉式方塊中，如果找到字串，在清單方塊中選取字串，並將字串複製到編輯控制項。|  
|[CComboBox::SetCueBanner](#setcuebanner)|設定下拉式方塊控制項所顯示的提示文字。|  
|[CComboBox::SetCurSel](#setcursel)|選取清單方塊的下拉式方塊中的字串。|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|設定允許下拉式方塊的下拉式清單方塊部分的寬度的最小。|  
|[CComboBox::SetEditSel](#seteditsel)|選取下拉式方塊的編輯控制項中的字元。|  
|[CComboBox::SetExtendedUI](#setextendedui)|選取預設的使用者介面或擴充的使用者介面，下拉式清單方塊具有**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**樣式。|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|設定下拉式方塊的清單方塊部分可以水平捲動的像素為單位的寬度。|  
|[CComboBox::SetItemData](#setitemdata)|設定下拉式方塊中指定的項目相關聯的 32 位元值。|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|設定下拉式方塊中指定的項目相關聯的 32 位元指標。|  
|[CComboBox::SetItemHeight](#setitemheight)|在下拉式方塊或下拉式方塊的編輯控制項 （或靜態文字） 部分的高度設定清單項目的高度。|  
|[CComboBox::SetLocale](#setlocale)|設定下拉式方塊的地區設定識別碼。|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|在目前的下拉式方塊的下拉式清單中設定的最小的可見項目數目。|  
|[CComboBox::SetTopIndex](#settopindex)|會告訴清單方塊下拉式方塊部分顯示具有指定索引的項目上方。|  
|[CComboBox::ShowDropDown](#showdropdown)|顯示或隱藏清單方塊的下拉式方塊具有**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**樣式。|  
  
## <a name="remarks"></a>備註  
 下拉式方塊清單方塊，加上靜態控制項或編輯控制項所組成。 控制項的清單方塊部分隨時都可能會顯示，或當使用者選取下拉式清單旁的箭號控制項可能只有下拉式清單。  
  
 目前選取的項目 （如果有的話） 的清單方塊中會顯示在靜態或編輯控制項。 此外，如果下拉式方塊的下拉式清單樣式，使用者可以在清單中，輸入的起始字元的其中一個項目和清單方塊中，如果可以看見，會反白顯示該初始字元的下一個項目。  
  
 下表比較三個下拉式方塊[樣式](../../mfc/reference/combo-box-styles.md)。  
  
|樣式|當清單方塊是可見的|靜態或編輯控制項|  
|-----------|-------------------------------|-----------------------------|  
|簡單|永遠|Edit|  
|Drop-down|卸除時|Edit|  
|下拉式清單|卸除時|Static|  
  
 您可以建立`CComboBox`從對話方塊範本，或直接在您的程式碼中的物件。 在這兩種情況下，第一次呼叫建構函式`CComboBox`建構`CComboBox`物件，然後呼叫[建立](#create)成員函式來建立控制項並將其附加至`CComboBox`物件。  
  
 如果您想要處理 Windows 通知訊息傳送至其父代下拉式方塊 (通常是一個類別衍生自`CDialog`)，將訊息對應項目和訊息處理常式成員函式加入至每個訊息的父類別。  
  
 每個訊息對應項目都會使用下列格式︰  
  
 **ON_**Notification **(**`id`**,**`memberFxn`**)**  
  
 其中`id`指定傳送通知的下拉式方塊控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 父函式原型如下所示︰  
  
 **afx_msg** `void` `memberFxn` **( );**  
  
 無法預測將會傳送特定通知的順序。 特別是， **CBN_SELCHANGE**之前或之後，可能會發生通知**CBN_CLOSEUP**通知。  
  
 可能的訊息對應項目如下所示︰  
  
- **ON_CBN_CLOSEUP** (Windows 3.1 和更新版本。)清單方塊的下拉式方塊已關閉。 具有下拉式清單方塊不會傳送這個通知訊息[CBS_SIMPLE](../../mfc/reference/combo-box-styles.md)樣式。  
  
- **ON_CBN_DBLCLK**使用者按兩下清單方塊的下拉式方塊中的字串。 使用下拉式清單方塊只會傳送這個通知訊息**CBS_SIMPLE**樣式。 與下拉式方塊的[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)樣式，按兩下不會發生因為只要按一下隱藏清單方塊。  
  
- **ON_CBN_DROPDOWN**即將下拉式清單方塊的下拉式方塊 （可變成可見）。 此通知訊息可能只會針對與下拉式方塊**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**樣式。  
  
- **ON_CBN_EDITCHANGE**使用者採取的動作，可能有變更編輯控制項下拉式方塊部分中的文字。 不同於**CBN_EDITUPDATE**訊息時，此訊息會傳送之後，Windows 會更新畫面。 不會傳送下拉式方塊是否**CBS_DROPDOWNLIST**樣式。  
  
- **ON_CBN_EDITUPDATE**即將顯示變更的文字下拉式方塊中編輯控制項的一部分。 控制項已格式化文字之後，但它會顯示文字之前，會傳送這個通知訊息。 不會傳送下拉式方塊是否**CBS_DROPDOWNLIST**樣式。  
  
- **ON_CBN_ERRSPACE**下拉式方塊無法配置足夠的記憶體，以符合特定要求。  
  
- **ON_CBN_SELENDCANCEL** (Windows 3.1 和更新版本。)指出應該取消使用者的選擇。 使用者按一下的項目，並按一下另一個視窗或隱藏清單方塊的下拉式方塊控制項。 這會傳送通知訊息之前**CBN_CLOSEUP**通知訊息，表示應該忽略使用者的選擇。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**會傳送通知訊息，即使**CBN_CLOSEUP**不會傳送通知訊息 (在與下拉式方塊的情況下為**CBS_SIMPLE**樣式)。  
  
- **ON_CBN_SELENDOK**使用者選取的項目，然後按下 ENTER 鍵或按一下向下鍵來隱藏清單方塊的下拉式方塊。 這會傳送通知訊息之前**CBN_CLOSEUP**訊息，指出該使用者的選取範圍應該被視為有效。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**會傳送通知訊息，即使**CBN_CLOSEUP**不會傳送通知訊息 (在與下拉式方塊的情況下為**CBS_SIMPLE**樣式)。  
  
- **ON_CBN_KILLFOCUS**下拉式方塊正失去輸入的焦點。  
  
- **ON_CBN_SELCHANGE**下拉式方塊的清單方塊中的選擇是即將變更使用者按一下清單方塊中，或使用方向鍵來變更選取範圍的結果。 在處理此訊息時，編輯控制項的下拉式方塊中的文字只擷取透過`GetLBText`或另一個類似的功能。 `GetWindowText`無法使用。  
  
- **ON_CBN_SETFOCUS**下拉式方塊輸入焦點。  
  
 如果您建立`CComboBox`（透過對話方塊資源），對話方塊內的物件`CComboBox`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您內嵌`CComboBox`另一個視窗內物件的物件，您不需要它終結。 如果您建立`CComboBox`物件在堆疊上，它會自動終結。 如果您建立`CComboBox`使用堆積上的物件**新**函式，您必須呼叫**刪除**Windows 下拉式方塊終結時終結該物件上。  
  
 **請注意**如果您想要處理`WM_KEYDOWN`和`WM_CHAR`訊息，您有子類別化下拉式方塊的編輯和清單方塊控制項中，衍生類別，從`CEdit`和`CListBox`，並將這些訊息的處理常式加入至衍生的類別。 如需詳細資訊，請參閱[http://support.microsoft.com/default.aspxscid=kb;en-us;Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667)和[CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-nameaddstringa--ccomboboxaddstring"></a><a name="addstring"></a>Ccombobox:: Addstring  
 將字串加入至下拉式方塊的清單方塊。  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 `lpszString`  
 要加入的 null 結尾字串的指標。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是大於或等於 0，它是以零為起始的索引清單方塊中的字串。 傳回值是**CB_ERR**若發生錯誤，則傳回值是**CB_ERRSPACE**如果空間不足以存放新的字串。  
  
### <a name="remarks"></a>備註  
 如果清單方塊不透過建立[CBS_SORT](../../mfc/reference/combo-box-styles.md)樣式中，字串會新增至清單的結尾。 否則，將字串插入至清單，並排序清單。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 若要插入清單中的特定位置的字串，請使用[InsertString](#insertstring)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&3;](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="a-nameccomboboxa--ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox::CComboBox  
 建構 `CComboBox` 物件。  
  
```  
CComboBox();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&1;](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="a-namecleara--ccomboboxclear"></a><a name="clear"></a>CComboBox::Clear  
 （清除） 會刪除目前選取範圍，如果有的話，編輯控制項的下拉式方塊中。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 刪除目前選取範圍，並放置到剪貼簿已刪除的內容，請使用[剪下](#cut)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&4;](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="a-namecompareitema--ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox::CompareItem  
 由框架呼叫以判斷新的項目已排序的主控描繪下拉式方塊的清單方塊部分中的相對位置。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpCompareItemStruct`  
 長指標[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)結構。  
  
### <a name="return-value"></a>傳回值  
 表示兩個項目中所述的相對位置`COMPAREITEMSTRUCT`結構。 它可以是下列值之一︰  
  
|值|意義|  
|-----------|-------------|  
|– 1|項目 1 排序項目 2 之前。|  
|0|項目 1 和 2 的項目排序相同。|  
|1|項目 1 排序項目 2 之後。|  
  
 請參閱[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)的說明`COMPAREITEMSTRUCT`。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有作用。 如果您建立與主控描繪下拉式方塊**LBS_SORT**樣式，您必須覆寫此成員函式，以協助架構排序的清單方塊中加入新項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&5;](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="a-namecopya--ccomboboxcopy"></a><a name="copy"></a>CComboBox::Copy  
 將目前的選取範圍，複製到剪貼簿中的下拉式方塊的編輯控制項中的任何**CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&6;](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="a-namecreatea--ccomboboxcreate"></a><a name="create"></a>CComboBox::Create  
 建立下拉式方塊，並將它附加`CComboBox`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定下拉式方塊樣式。 套用的任何結合[下拉式方塊樣式](../../mfc/reference/combo-box-styles.md)至方塊。  
  
 `rect`  
 指向的位置和下拉式方塊的大小。 可以是[RECT 結構](../../mfc/reference/rect-structure1.md)或`CRect`物件。  
  
 `pParentWnd`  
 指定下拉式方塊的父視窗 (通常是`CDialog`)。 它不得為**NULL**。  
  
 `nID`  
 指定下拉式方塊控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CComboBox`兩個步驟中的物件。 首先，呼叫建構函式，接著呼叫**建立**，其建立 Windows 下拉式方塊，並將它附加`CComboBox`物件。  
  
 當**建立**執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)下拉式方塊的訊息。  
  
 根據預設，處理這些訊息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式中`CWnd`基底類別。 若要擴充的預設訊息處理，衍生自`CComboBox`、 將訊息對應新增至新的類別，並覆寫先前的訊息處理常式成員函式。 覆寫`OnCreate`，例如，執行所需的初始化新的類別。  
  
 適用於下列[視窗樣式](../../mfc/reference/window-styles.md)至下拉式方塊控制項。 :  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**新增垂直捲動功能的清單方塊中的下拉式方塊  
  
- **WS_HSCROLL**加入的清單方塊的下拉式方塊中的水平捲軸  
  
- **WS_GROUP**控制項群組  
  
- **WS_TABSTOP**納入 tab 鍵順序中的下拉式方塊  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&2;](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="a-namecuta--ccomboboxcut"></a><a name="cut"></a>CComboBox::Cut  
 刪除 （剪下） 目前選取項目，如果在下拉式方塊中的任何編輯控制，並複製到剪貼簿中刪除的文字**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>備註  
 若要刪除目前選取範圍，而不會刪除的文字到剪貼簿，請呼叫[清除](#clear)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&7;](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="a-namedeleteitema--ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox::DeleteItem  
 當使用者從主控描繪刪除項目時，由框架呼叫`CComboBox`物件或終結下拉式方塊。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDeleteItemStruct`  
 Windows 的長指標[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)結構，其中包含已刪除項目的相關資訊。 請參閱[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)的這個結構描述。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫這個函式，視需要重繪下拉式方塊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&8;](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="a-namedeletestringa--ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox::DeleteString  
 刪除項目位置`nIndex`下拉式方塊中。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要刪除之字串的索引。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是大於或等於 0，則清單中的剩餘字串的計數。 傳回值是**CB_ERR**如果`nIndex`指定索引的項目數大於清單中。  
  
### <a name="remarks"></a>備註  
 之後的所有項目`nIndex`現在下移一個位置。 例如，如果下拉式方塊包含兩個項目，刪除第一個項目會導致其餘的項目現在是在第一個位置。 `nIndex`=&0;，第一個位置中的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&9;](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="a-namedira--ccomboboxdir"></a><a name="dir"></a>CComboBox::Dir  
 將下拉式方塊的清單方塊中的檔案名稱或磁碟機的清單。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>參數  
 `attr`  
 可以是任何組合的`enum`值中所述[Getstatus](../../mfc/reference/cfile-class.md#getstatus)或下列值的任何組合︰  
  
- **DDL_READWRITE**讀取或寫入檔案。  
  
- **DDL_READONLY**可以讀取但不是會寫入檔案。  
  
- **DDL_HIDDEN**檔案會被隱藏，並且不會出現在目錄清單。  
  
- **DDL_SYSTEM**檔案是系統檔案。  
  
- **DDL_DIRECTORY**所指定的名稱`lpszWildCard`指定的目錄。  
  
- **DDL_ARCHIVE**在封存檔案。  
  
- **DDL_DRIVES**包含符合指定之名稱的所有磁碟機`lpszWildCard`。  
  
- **DDL_EXCLUSIVE**獨佔的旗標。 如果獨佔的旗標設定時，會列出檔案指定的型別。 否則，會列出指定之型別的的檔案，除了 「 正常 」 的檔案。  
  
 `lpszWildCard`  
 指向檔案規格字串。 字串可以包含萬用字元 (例如，*。\*)。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是大於或等於 0，則加入至清單的最後一個檔名的以零起始的索引。 傳回值是**CB_ERR**若發生錯誤，則傳回值是**CB_ERRSPACE**如果空間不足以存放新的字串。  
  
### <a name="remarks"></a>備註  
 Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&10;](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="a-namedrawitema--ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox::DrawItem  
 當主控描繪下拉式方塊變更的視覺外觀的架構所呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**成員`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)的這個結構描述。  
  
 根據預設，此成員函式沒有作用。 覆寫此成員函式實作繪圖的主控描繪`CComboBox`物件。 此成員函式結束之前，應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&11;](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="a-namefindstringa--ccomboboxfindstring"></a><a name="findstring"></a>CComboBox::FindString  
 找到，但不會選取第一個字串，其中包含指定的前置詞清單方塊的下拉式方塊中。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當到達清單方塊的底部時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 –&1;，如果整個清單方塊開始搜尋。  
  
 `lpszString`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是大於或等於 0，則相符項目的以零起始的索引。 它是**CB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&12;](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="a-namefindstringexacta--ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox::FindStringExact  
 呼叫`FindStringExact`成員函式來尋找第一個清單方塊中的字串 （下拉式方塊），符合指定之字串`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndexStart`  
 指定要搜尋的第一個項目之前的項目以零為起始的索引。 當到達清單方塊的底部時，它會繼續從清單方塊的上方回所指定的項目`nIndexStart`。 如果`nIndexStart`為 –&1;，從一開始便會搜尋整個清單方塊。  
  
 `lpszFind`  
 指向以 null 結束的字串搜尋。 這個字串可以包含完整的檔名，包括副檔名。 搜尋不區分大小寫，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 比對項目的以零起始的索引或**CB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 如果使用下拉式方塊但沒有建立主控描繪樣式[CBS_HASSTRINGS](../../mfc/reference/combo-box-styles.md)樣式，`FindStringExact`會嘗試比對的值的 doubleword 值`lpszFind`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&13;](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="a-namegetcomboboxinfoa--ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo  
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
 此成員函式模擬的功能[CB_GETCOMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775839)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcounta--ccomboboxgetcount"></a><a name="getcount"></a>CComboBox::GetCount  
 呼叫此成員函式可擷取下拉式方塊的清單方塊部分中的項目數。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 項目數目。 傳回的計數會比索引值 （索引以零為起始） 的最後一個項目。 它是**CB_ERR**發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&14;](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="a-namegetcuebannera--ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox::GetCueBanner  
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
|[輸出] `lpszText`|收到提示橫幅文字的緩衝區指標。|  
|[in] `cchText`|緩衝區的大小，`lpszText`參數所指向。|  
  
### <a name="return-value"></a>傳回值  
 在第一個多載， [CString](../../atl-mfc-shared/using-cstring.md)物件，其中包含提示橫幅文字，如果有的話，否則`CString`長度零的物件。  
  
 -或-  
  
 在第二個多載，`true`如果此方法成功，否則`false`。  
  
### <a name="remarks"></a>備註  
 提示文字是輸入區域的下拉式方塊控制項中顯示的提示。 直到使用者提供輸入，會顯示提示文字。  
  
 這個方法會傳送[CB_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775843)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcursela--ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox::GetCurSel  
 呼叫此成員函式，來決定選取哪一個下拉式方塊中的項目。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊的清單方塊中目前選取項目的以零起始的索引或**CB_ERR**如果在不選取任何項目。  
  
### <a name="remarks"></a>備註  
 `GetCurSel`傳回清單中的索引。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&15;](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="a-namegetdroppedcontrolrecta--ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect  
 呼叫`GetDroppedControlRect`成員函式來擷取可見 （卸除） 清單方塊的下拉式清單方塊的螢幕座標。  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>參數  
 *lprect*  
 指向[RECT 結構](../../mfc/reference/rect-structure1.md)要接收的座標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&16;](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="a-namegetdroppedstatea--ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox::GetDroppedState  
 呼叫`GetDroppedState`成員函式來決定是否清單方塊的下拉式清單方塊會顯示 （落下）。  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果清單方塊是可見的。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&17;](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="a-namegetdroppedwidtha--ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth  
 呼叫此函式可擷取的最小的可允許寬度，單位為像素下拉式方塊的清單方塊。  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，最小的可允許寬度，單位為像素。否則， **CB_ERR**。  
  
### <a name="remarks"></a>備註  
 此函式只適用於下拉式方塊和[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)樣式。  
  
 根據預設，可允許下拉式清單方塊的寬度下限為 0。 允許的最小寬度可以藉由呼叫設定[SetDroppedWidth](#setdroppedwidth)。 顯示下拉式方塊的清單方塊部分時，其寬度是較大的可允許的最小寬度或下拉式方塊的寬度。  
  
### <a name="example"></a>範例  
  請參閱範例[SetDroppedWidth](#setdroppedwidth)。  
  
##  <a name="a-namegeteditsela--ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox::GetEditSel  
 取得編輯控制項的下拉式方塊中目前的選取範圍的開始和結束的字元位置。  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 32 位元值，其中包含高序位文字中的選取範圍的結尾之後的低序位字組中的開始位置和未選取第一個字元的位置。 如果此函式可在下拉式方塊而不需要編輯控制項， **CB_ERR**傳回。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&18;](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="a-namegetextendeduia--ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox::GetExtendedUI  
 呼叫`GetExtendedUI`成員函式，以判斷是否下拉式方塊的預設使用者介面或擴充的使用者介面。  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果下拉式方塊已擴充的使用者介面中，為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 擴充的使用者介面可以找出下列方式︰  
  
-   按一下靜態控制項以顯示僅適用於下拉式方塊和清單方塊[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)樣式。  
  
-   按向下鍵顯示清單方塊 （已停用 F4）。  
  
 在靜態控制項中捲動時，停用項目清單是不可見 （箭號會停用索引鍵）。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&19;](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="a-namegethorizontalextenta--ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent  
 擷取從下拉式方塊的下拉式方塊的清單方塊部分可以水平捲動的像素為單位的寬度。  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊的 像素為單位的清單方塊的可捲動的寬度。  
  
### <a name="remarks"></a>備註  
 這是下拉式方塊的清單方塊部分具有水平捲軸時，才適用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&20;](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="a-namegetitemdataa--ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox::GetItemData  
 擷取與指定的下拉式方塊項目相關聯的應用程式提供 32 位元值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含的下拉式方塊的清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 對項目相關聯的 32 位元值或**CB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 32 位元值可以設定與`dwItemData`參數[SetItemData](#setitemdata)成員函式呼叫。 使用`GetItemDataPtr`成員函式，如果要擷取的 32 位元值是指標 ( **void\***)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&21;](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="a-namegetitemdataptra--ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox::GetItemDataPtr  
 擷取與指定的下拉式方塊項目做為指標的應用程式提供 32 位元值 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含的下拉式方塊的清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 擷取是指標，則為 –&1;，如果發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&22;](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="a-namegetitemheighta--ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox::GetItemHeight  
 呼叫`GetItemHeight`成員函式可擷取下拉式方塊中的清單項目的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定下拉式方塊的高度是要擷取的元件。 如果`nIndex`參數為 –&1;，將會擷取的編輯控制項 （或靜態文字） 部分的下拉式方塊的高度。 如果下拉式方塊中含有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md)樣式`nIndex`指定的高度是要擷取之清單項目的以零為起始的索引。 否則，`nIndex`應該設為 0。  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素下拉式方塊中指定的項目。 如果發生錯誤，傳回值是 **CB_ERR** 。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&23;](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="a-namegetlbtexta--ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox::GetLBText  
 取得字串，請從清單方塊的下拉式方塊。  
  
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
 要接收字串緩衝區的指標。 緩衝區必須有足夠的空間，如字串和結束的 null 字元。  
  
 `rString`  
 參考`CString`。  
  
### <a name="return-value"></a>傳回值  
 字串，但不包含結束的 null 字元的長度 （以位元組為單位）。 如果`nIndex`未指定有效的索引，則傳回值是**CB_ERR**。  
  
### <a name="remarks"></a>備註  
 這個成員的第二個形式函式的填滿`CString`物件項目的文字。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&24;](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="a-namegetlbtextlena--ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox::GetLBTextLen  
 取得清單方塊的下拉式方塊中的字串的長度。  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含清單方塊字串之以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 以位元組為單位，但不包含結束的 null 字元字串的長度。 如果`nIndex`未指定有效的索引，則傳回值是**CB_ERR**。  
  
### <a name="example"></a>範例  
  請參閱範例[CComboBox::GetLBText](#getlbtext)。  
  
##  <a name="a-namegetlocalea--ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox::GetLocale  
 擷取使用下拉式方塊的地區設定。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊中的字串，地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 會使用地區設定，例如，以判斷字串排序的下拉式方塊中的排序順序。  
  
### <a name="example"></a>範例  
  請參閱範例[CComboBox::SetLocale](#setlocale)。  
  
##  <a name="a-namegetminvisiblea--ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox::GetMinVisible  
 在目前的下拉式方塊控制項的下拉式清單中取得的最小的可見項目數目。  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的下拉式清單中的可見項目的最小數目。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[CB_GETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettopindexa--ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox::GetTopIndex  
 擷取的下拉式方塊的清單方塊部分中的第一個可見項目以零為起始的索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，在下拉式方塊的清單方塊部分中的第一個可見項目以零為起始索引**CB_ERR**否則。  
  
### <a name="remarks"></a>備註  
 一開始，項目 0 頂端的清單方塊中，但是如果捲動清單方塊中，另一個項目一定在頂端。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&25;](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="a-nameinitstoragea--ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox::InitStorage  
 在下拉式方塊的清單方塊部分中儲存清單方塊項目會配置記憶體。  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>參數  
 `nItems`  
 指定要加入項目數目。  
  
 `nBytes`  
 指定的記憶體數量，以位元組為單位，以配置所需項目的字串。  
  
### <a name="return-value"></a>傳回值  
 如果成功，最大數目的項目之前需要的記憶體配置，否則，下拉式方塊的清單方塊部分可以存放**CB_ERRSPACE**，這表示沒有足夠的記憶體可用。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，才能將大量項目新增到清單方塊部份`CComboBox`。  
  
 只有 Windows 95/98:`wParam`參數是限制為 16 位元值。 這表示清單方塊不能包含超過 32767 個項目。 雖然受限制的項目數，清單方塊中的項目中的總大小只受限於可用的記憶體。  
  
 此函式可協助您加速有大量的項目 (超過 100) 的清單方塊的初始化。 它使用預先配置時讓後續的記憶體數量指定[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函式接受的最短的時間。 您可以使用估計值的參數。 如果增長時，會配置一些額外的記憶體。如果您低估，一般配置使用超過預先配置的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&26;](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="a-nameinsertstringa--ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox::InsertString  
 將字串插入下拉式方塊的清單方塊中。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含要接收字串之清單方塊中位置以零為基底的索引。 如果這個參數為 –1，字串就加入到清單的結尾。  
  
 `lpszString`  
 指向要插入的 null 結尾字串。  
  
### <a name="return-value"></a>傳回值  
 已插入字串之位置以零為基底的索引。 如果發生錯誤，傳回值是 **CB_ERR** 。 如果空間不足，無法存放新的字串，傳回值是 **CB_ERRSPACE** 。  
  
### <a name="remarks"></a>備註  
 不同於[AddString](#addstring)成員函式，`InsertString`成員函式並不會與清單[CBS_SORT](../../mfc/reference/combo-box-styles.md)排序樣式。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&27;](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="a-namelimittexta--ccomboboxlimittext"></a><a name="limittext"></a>CComboBox::LimitText  
 限制使用者可以將編輯控制項的下拉式方塊輸入文字以位元組為單位的長度。  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>參數  
 `nMaxChars`  
 指定使用者可以輸入之文字的長度 （以位元組為單位）。 這個參數是 0，如果文字長度設為 65535 個位元組。  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，非零值。 如果呼叫下拉式方塊樣式[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)或下拉式方塊，而不需要編輯控制項，則傳回值是**CB_ERR**。  
  
### <a name="remarks"></a>備註  
 如果下拉式方塊沒有樣式[CBS_AUTOHSCROLL](../../mfc/reference/combo-box-styles.md)，設定為編輯控制項的大小大於文字限制不會有任何作用。  
  
 `LimitText`只會限制使用者可以輸入的文字。 它已不會影響任何文字編輯控制項中時將訊息傳送時，也不會影響文字字串的清單方塊中選取時，複製到編輯控制項的長度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&28;](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="a-namemeasureitema--ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox::MeasureItem  
 建立主控描繪樣式下拉式方塊時，由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpMeasureItemStruct`  
 長指標[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有作用。 覆寫此成員函式，並填入`MEASUREITEMSTRUCT`結構以通知 Windows 個維度的清單方塊下拉式方塊中。 如果下拉式方塊以建立[CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md)樣式，架構會呼叫此成員函式的清單方塊中的每個項目。 否則，這個成員是只呼叫一次。  
  
 使用**CBS_OWNERDRAWFIXED**中建立主控描繪下拉式方塊樣式[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成員函式`CWnd`涉及進一步程式設計考量。 請參閱[技術附註 14](../../mfc/tn014-custom-controls.md)。  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&29;](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="a-namepastea--ccomboboxpaste"></a><a name="paste"></a>CComboBox::Paste  
 從剪貼簿資料插入下拉式方塊目前游標位置的編輯控制項。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>備註  
 資料會插入剪貼簿中包含的資料時，才**CF_TEXT**格式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&30;](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="a-nameresetcontenta--ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox::ResetContent  
 移除所有項目從清單方塊和下拉式方塊控制項的編輯。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&31;](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="a-nameselectstringa--ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox::SelectString  
 搜尋下拉式方塊的清單方塊中的字串，並找到字串，如果在清單方塊中選取字串，並將其複製編輯控制項。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當到達清單方塊的底部時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 –&1;，如果整個清單方塊開始搜尋。  
  
 `lpszString`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 選取的項目，如果找到字串的以零為起始的索引。 如果搜尋成功，則傳回值是**CB_ERR**且不會變更目前的選取範圍。  
  
### <a name="remarks"></a>備註  
 只有當其起始的字元 （從起點） 符合前置詞字串中的字元，會選取字串。  
  
 請注意，`SelectString`和`FindString`成員函數尋找字串，但`SelectString`成員函式也會選取字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&32;](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="a-namesetcuebannera--ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox::SetCueBanner  
 設定下拉式方塊控制項所顯示的提示文字。  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|[in]*lpszText*|以 null 終止的緩衝區，其中包含提示文字指標。|  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 提示文字是輸入區域的下拉式方塊控制項中顯示的提示。 直到使用者提供輸入，會顯示提示文字。  
  
 這個方法會傳送[CB_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775897)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_combobox`，也就是用來以程式設計方式存取下拉式方塊控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定下拉式方塊控制項的提示橫幅。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="a-namesetcursela--ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox::SetCurSel  
 選取清單方塊的下拉式方塊中的字串。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>參數  
 `nSelect`  
 指定要選取之字串的以零為起始的索引。 如果 –&1;，則會移除任何目前的選取清單方塊中，並且清除編輯控制項。  
  
### <a name="return-value"></a>傳回值  
 成功的訊息時所選取之項目的以零為起始的索引。 傳回值是**CB_ERR**如果`nSelect`大於清單中的項目數或`nSelect`設定為 –&1;，這會清除選取項目。  
  
### <a name="remarks"></a>備註  
 必要時，清單方塊顯示出來的字串 （如果清單方塊會顯示）。 下拉式方塊的編輯控制項中的文字會變更以反映新的選取範圍。 會移除任何前面的選擇清單方塊中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&33;](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="a-namesetdroppedwidtha--ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth  
 呼叫此函式可設定的最小的可允許寬度，單位為像素下拉式方塊的清單方塊。  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 下拉式方塊的 像素為單位的清單方塊的最小的可允許寬度。  
  
### <a name="return-value"></a>傳回值  
 如果成功，新的寬度的清單方塊中，否則**CB_ERR**。  
  
### <a name="remarks"></a>備註  
 此函式只適用於下拉式方塊和[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)樣式。  
  
 根據預設，可允許下拉式清單方塊的寬度下限為 0。 顯示下拉式方塊的清單方塊部分時，其寬度是較大的可允許的最小寬度或下拉式方塊的寬度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&34;](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="a-nameseteditsela--ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox::SetEditSel  
 選取下拉式方塊的編輯控制項中的字元。  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>參數  
 `nStartChar`  
 指定的開始位置。 如果開始位置設定為 –&1;，則會移除任何現有的選取範圍。  
  
 `nEndChar`  
 指定的結束位置。 如果到最後一個設定為 –&1;，則所有文字的起始位置的結束位置選取編輯控制項中的字元。  
  
### <a name="return-value"></a>傳回值  
 如果成員函式成功則為非零否則為 0。 它是**CB_ERR**如果`CComboBox`有[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)樣式，或沒有清單方塊。  
  
### <a name="remarks"></a>備註  
 位置是以零為起始的。 若要選取的編輯控制項的第一個字元，您可以指定 0 的開始位置。 只在選取的最後一個字元之後的字元是結束的位置。 例如，若要選取的編輯控制項的前四個字元，您會使用 0 的開始位置和 4 的結束位置。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控制項不支援這個函式。 如需有關此控制項的詳細資訊，請參閱[ComboBoxEx 控制項](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CComboBox::GetEditSel](#geteditsel)。  
  
##  <a name="a-namesetextendeduia--ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox::SetExtendedUI  
 呼叫`SetExtendedUI`選取預設的使用者介面或下拉式方塊已擴充的使用者介面的成員函式[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)樣式。  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bExtended*  
 指定下拉式方塊是否應該使用擴充的使用者介面或預設的使用者介面。 值為**TRUE**選取擴充使用者介面，而值**FALSE**選取的標準使用者介面。  
  
### <a name="return-value"></a>傳回值  
 **CB_OKAY**如果作業成功，或**CB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 擴充的使用者介面可以找出下列方式︰  
  
-   按一下靜態控制項以顯示僅適用於下拉式方塊和清單方塊**CBS_DROPDOWNLIST**樣式。  
  
-   按向下鍵顯示清單方塊 （已停用 F4）。  
  
 在靜態控制項中捲動時，停用項目清單是不可見 （方向鍵會停用）。  
  
### <a name="example"></a>範例  
  請參閱範例[CComboBox::GetExtendedUI](#getextendedui)。  
  
##  <a name="a-namesethorizontalextenta--ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent  
 設定寬度，單位為像素的下拉式方塊的清單方塊部分可以水平捲動。  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>參數  
 *nExtent*  
 指定的下拉式方塊的清單方塊部分可以水平捲動的像素數目。  
  
### <a name="remarks"></a>備註  
 如果清單方塊的寬度小於此值，水平捲軸的水平捲動清單方塊中的項目。 如果清單方塊的寬度是等於或大於此值，會隱藏水平捲軸或下拉式方塊中含有[CBS_DISABLENOSCROLL](../../mfc/reference/combo-box-styles.md)樣式，停用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&35;](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="a-namesetitemdataa--ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox::SetItemData  
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
 包含要與項目產生關聯的新值。  
  
### <a name="return-value"></a>傳回值  
 **CB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 使用`SetItemDataPtr`32 位元的項目是否為指標的成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&36;](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="a-namesetitemdataptra--ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox::SetItemDataPtr  
 設定為指定的指標下拉式方塊中指定的項目相關聯的 32 位元值 ( **void\***)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含的項目以零為起始索引。  
  
 `pData`  
 包含要與項目產生關聯的指標。  
  
### <a name="return-value"></a>傳回值  
 **CB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 此指標都是有效的生命週期的下拉式方塊中，即使新增或移除項目時，可能會變更下拉式方塊內項目的相對位置。 因此，可以變更方塊內項目的索引，但是，指標都是可靠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&37;](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="a-namesetitemheighta--ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox::SetItemHeight  
 呼叫`SetItemHeight`成員函式中的下拉式方塊或下拉式方塊的編輯控制項 （或靜態文字） 部分的高度設定的清單項目高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定設定的清單項目高度或下拉式方塊的編輯控制項 （或靜態文字） 部分的高度。  
  
 如果下拉式方塊中含有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md)樣式，`nIndex`指定的設定; 否則為其高度的清單項目以零為起始的索引`nIndex`必須是 0 和高度的項目將會設定所有的清單。  
  
 如果`nIndex`為 –&1;，編輯控制項的高度或下拉式方塊的靜態文字部分設定。  
  
 `cyItemHeight`  
 指定的高度，單位為像素所識別的下拉式方塊元件`nIndex`。  
  
### <a name="return-value"></a>傳回值  
 **CB_ERR**如果索引或高度無效，否則為 0。  
  
### <a name="remarks"></a>備註  
 Edit 控制項 （或靜態文字） 的下拉式方塊部分的高度是獨立的清單項目高度設定。 應用程式必須確定 edit 控制項 （或靜態文字） 部分的高度不小於特定清單方塊項目高度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&38;](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="a-namesetlocalea--ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox::SetLocale  
 設定下拉式方塊的地區設定識別碼。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>參數  
 `nNewLocale`  
 要設定的下拉式方塊的新地區設定識別碼 (LCID) 值。  
  
### <a name="return-value"></a>傳回值  
 先前的地區設定識別碼 (LCID) 值的下拉式方塊。  
  
### <a name="remarks"></a>備註  
 如果**SetLocale** ，不會呼叫預設的地區設定從系統取得。 可以修改此系統預設地區設定使用控制台中的地區 （或國際） 應用程式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&39;](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="a-namesetminvisibleitemsa--ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems  
 設定可見的項目數目下限下拉式清單中的目前下拉式方塊控制項。  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iMinVisible`|指定的最小的可見項目數目。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[CB_SETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_combobox`，也就是用來以程式設計方式存取下拉式方塊控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會將 20 個項目插入至下拉式方塊控制項的下拉式清單。 然後它會指定在使用者按下拉箭號時，會顯示最少的 10 個項目。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="a-namesettopindexa--ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox::SetTopIndex  
 可確保特定項目會顯示在下拉式方塊的清單方塊部分。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定清單方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，零或**CB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 系統會將清單方塊捲動直到其中一個所指定的項目`nIndex`會出現在清單頂端或最大的捲軸範圍已達到。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CComboBox #&40;](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="a-nameshowdropdowna--ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox::ShowDropDown  
 顯示或隱藏清單方塊的下拉式方塊具有[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)樣式。  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bShowIt*  
 指定是否要顯示或隱藏的下拉式清單方塊。 值為**TRUE**顯示清單方塊。 值為**FALSE**隱藏清單方塊。  
  
### <a name="remarks"></a>備註  
 根據預設，此樣式的下拉式方塊會顯示清單方塊。  
  
 此成員函式沒有任何作用，以建立下拉式方塊上的[CBS_SIMPLE](../../mfc/reference/combo-box-styles.md)樣式。  
  
### <a name="example"></a>範例  
  請參閱範例[CComboBox::GetDroppedState](#getdroppedstate)。  
  
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

