---
title: "CListBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
dev_langs:
- C++
helpviewer_keywords:
- CListBox class
- list boxes
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 4b1b1963af7740820b1285c3df8724f9ea4332b1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="clistbox-class"></a>CListBox 類別
提供 Windows 清單方塊的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|建構 `CListBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|將字串新增至清單方塊。|  
|[CListBox::CharToItem](#chartoitem)|若要提供自訂的覆寫`WM_CHAR`主控描繪清單方塊中沒有字串處理。|  
|[CListBox::CompareItem](#compareitem)|由架構呼叫以判斷新的項目已排序的主控描繪清單方塊中的位置。|  
|[CListBox::Create](#create)|建立 Windows 清單方塊，並將它附加至`CListBox`物件。|  
|[CListBox::DeleteItem](#deleteitem)|當使用者從主控描繪清單方塊刪除項目時由架構呼叫。|  
|[CListBox::DeleteString](#deletestring)|刪除清單方塊中的字串。|  
|[CListBox::Dir](#dir)|將檔案名稱、 磁碟機，或從目前的目錄加入至清單方塊中。|  
|[CListBox::DrawItem](#drawitem)|當主控描繪清單方塊中變更的視覺外觀時，架構呼叫。|  
|[CListBox::FindString](#findstring)|搜尋字串，以在清單方塊中。|  
|[CListBox::FindStringExact](#findstringexact)|尋找符合指定之字串的第一個清單方塊字串。|  
|[CListBox::GetAnchorIndex](#getanchorindex)|擷取清單方塊中目前的錨定項目以零為起始的索引。|  
|[CListBox::GetCaretIndex](#getcaretindex)|判斷具有焦點矩形，在多重選擇清單方塊中的項目索引。|  
|[CListBox::GetCount](#getcount)|在清單方塊中，傳回字串數目。|  
|[CListBox::GetCurSel](#getcursel)|在清單方塊中，傳回目前所選取字串之以零為起始的索引。|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|傳回清單方塊可以水平捲動的像素為單位的寬度。|  
|[CListBox::GetItemData](#getitemdata)|傳回與清單方塊項目相關聯的 32 位元值。|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|讓指標回到清單方塊項目。|  
|[CListBox::GetItemHeight](#getitemheight)|決定清單方塊中項目的高度。|  
|[CListBox::GetItemRect](#getitemrect)|傳回目前顯示的清單方塊項目的週框。|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|擷取每個資料行的項目數目。|  
|[CListBox::GetLocale](#getlocale)|擷取清單方塊的地區設定識別碼。|  
|[CListBox::GetSel](#getsel)|傳回清單方塊項目的選取狀態。|  
|[CListBox::GetSelCount](#getselcount)|傳回字串的多重選擇清單方塊中目前選取的數字。|  
|[CListBox::GetSelItems](#getselitems)|傳回目前在清單方塊中選取之字串的索引。|  
|[CListBox::GetText](#gettext)|將清單方塊項目複製到緩衝區。|  
|[CListBox::GetTextLen](#gettextlen)|傳回的長度，以位元組為單位的清單方塊項目。|  
|[CListBox::GetTopIndex](#gettopindex)|在清單方塊中會傳回第一個可見字串的索引。|  
|[CListBox::InitStorage](#initstorage)|Preallocates 清單方塊項目和字串的記憶體區塊。|  
|[CListBox::InsertString](#insertstring)|在清單方塊中指定位置插入的字串。|  
|[CListBox::ItemFromPoint](#itemfrompoint)|傳回最接近的點的清單方塊項目的索引。|  
|[CListBox::MeasureItem](#measureitem)|判斷清單方塊維度建立主控描繪清單方塊時由架構呼叫。|  
|[CListBox::ResetContent](#resetcontent)|清除清單方塊中的所有項目。|  
|[CListBox::SelectString](#selectstring)|搜尋並選取單一選取清單方塊中的字串。|  
|[CListBox::SelItemRange](#selitemrange)|選取或取消選取範圍的多重選擇清單方塊中的字串。|  
|[CListBox::SetAnchorIndex](#setanchorindex)|設定在多重選擇清單方塊中，開始的延伸選取範圍的錨點。|  
|[CListBox::SetCaretIndex](#setcaretindex)|在多重選擇清單方塊中指定索引處的項目設定焦點矩形。|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|設定多重資料行的清單方塊的資料行寬度。|  
|[CListBox::SetCurSel](#setcursel)|選取清單方塊字串。|  
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|清單方塊可以水平捲動的像素為單位設定寬度。|  
|[CListBox::SetItemData](#setitemdata)|設定的清單方塊項目相關聯的 32 位元值。|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|清單方塊項目設定的指標。|  
|[CListBox::SetItemHeight](#setitemheight)|在清單方塊中，設定項目的高度。|  
|[CListBox::SetLocale](#setlocale)|設定清單方塊的地區設定識別碼。|  
|[CListBox::SetSel](#setsel)|選取或取消選取清單方塊項目在多重選擇清單方塊中。|  
|[CListBox::SetTabStops](#settabstops)|設定在清單方塊中的定位停駐點位置。|  
|[CListBox::SetTopIndex](#settopindex)|在清單方塊中設定的第一個可見的字串以零為起始的索引。|  
|[CListBox::VKeyToItem](#vkeytoitem)|若要提供自訂的覆寫`WM_KEYDOWN`清單方塊處理**LBS_WANTKEYBOARDINPUT**樣式設定。|  
  
## <a name="remarks"></a>備註  
 清單方塊會顯示項目，例如檔案名稱，使用者可以檢視和選取清單。  
  
 在單一選擇清單方塊中，使用者可以選取一個項目。 在多重選擇清單方塊中，您可以選取範圍的項目。 當使用者選取項目時，它會反白顯示和清單方塊會傳送通知訊息至父視窗。  
  
 從對話方塊範本，或是直接在您的程式碼中，您可以建立清單方塊。 若要直接建立，請建構`CListBox`物件，然後呼叫[建立](#create)成員函式來建立 Windows 清單方塊控制項，並將其附加至`CListBox`物件。 若要使用清單方塊的對話方塊範本中，宣告清單方塊中的變數對話方塊類別，然後使用`DDX_Control`在對話方塊類別的`DoDataExchange`函式，來連接至控制項的成員變數。 （這是為您自動加入您的對話方塊類別的控制變數時。）  
  
 建構可以是單一步驟中的處理序類別，衍生自`CListBox`。 寫入的建構函式在衍生的類別並呼叫**建立**從建構函式內。  
  
 如果您想要處理 Windows 通知訊息傳送至其父代清單方塊 (通常的類別衍生自[CDialog](../../mfc/reference/cdialog-class.md))，將訊息對應項目和訊息處理常式成員函式加入至每個訊息的父類別。  
  
 每個訊息對應項目有下列形式︰  
  
 `ON_Notification( id, memberFxn )`  
  
 其中`id`指定傳送通知的清單方塊控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 在父系的函式原型如下所示︰  
  
 `afx_msg void memberFxn( );`  
  
 以下是一份潛在的訊息對應項目和描述，它們就會傳送到父代的案例︰  
  
- **ON_LBN_DBLCLK**使用者按兩下清單方塊中的字串。 只有清單方塊具有[LBS_NOTIFY](../../mfc/reference/list-box-styles.md)樣式會傳送這項通知訊息。  
  
- **ON_LBN_ERRSPACE**清單方塊無法配置足夠的記憶體可符合要求。  
  
- **ON_LBN_KILLFOCUS**清單方塊正失去輸入的焦點。  
  
- **ON_LBN_SELCANCEL**會取消目前的清單方塊選取。 清單方塊時，才會傳送此訊息**LBS_NOTIFY**樣式。  
  
- **ON_LBN_SELCHANGE**清單方塊中的選取範圍已變更。 如果選取範圍已變更，不會傳送這個通知[CListBox::SetCurSel](#setcursel)成員函式。 此通知只適用於具有之清單方塊**LBS_NOTIFY**樣式。 **LBN_SELCHANGE**會傳送通知訊息的多重選擇清單方塊的使用者按下方向鍵，即使選取範圍不會變更。  
  
- **ON_LBN_SETFOCUS**清單方塊會接收輸入的焦點。  
  
- **ON_WM_CHARTOITEM**主控描繪清單方塊的任何字串接收`WM_CHAR`訊息。  
  
- **ON_WM_VKEYTOITEM**具有的清單方塊**LBS_WANTKEYBOARDINPUT**樣式接收`WM_KEYDOWN`訊息。  
  
 如果您建立`CListBox`物件 （透過對話方塊資源），對話方塊內`CListBox`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CListBox`物件在視窗中，您可能要終結`CListBox`物件。 如果您建立`CListBox`物件在堆疊上，會自動終結。 如果您建立`CListBox`使用堆積上的物件**新**函式，您必須呼叫**刪除**使用者關閉的父視窗時終結該物件上。  
  
 如果您配置任何記憶體`CListBox`物件，請覆寫`CListBox`解構函式來處置的配置。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="addstring"></a>CListBox::AddString  
 將字串新增至清單方塊。  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 `lpszItem`  
 指向以 null 結束的字串被加入。  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的字串以零為起始的索引。 傳回值是**LB_ERR**如果發生錯誤。 傳回的值是**LB_ERRSPACE**如果空間不足，無法使用存放新的字串。  
  
### <a name="remarks"></a>備註  
 如果不使用建立清單方塊[LBS_SORT](../../mfc/reference/list-box-styles.md)樣式，字串會新增至清單的結尾。 否則，字串會插入清單中，而且排序清單。 如果使用清單方塊建立**LBS_SORT**但不是設定樣式[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)樣式，架構會將清單排序一或多個呼叫`CompareItem`成員函式。  
  
 使用[InsertString](#insertstring)以將字串插入清單方塊內的特定位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="chartoitem"></a>CListBox::CharToItem  
 當清單方塊的父視窗收到時由架構呼叫`WM_CHARTOITEM`從清單方塊的訊息。  
  
```  
virtual int CharToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nKey`  
 ANSI 程式碼的使用者輸入的字元。  
  
 `nIndex`  
 目前的清單方塊插入號位置。  
  
### <a name="return-value"></a>傳回值  
 傳回-1 或 2，任何進一步的動作或負的數字的按鍵輸入執行預設動作的清單方塊項目的索引。 預設實作會傳回-1。  
  
### <a name="remarks"></a>備註  
 `WM_CHARTOITEM`收到時，傳送訊息的清單方塊`WM_CHAR`訊息，但只看清單方塊是否符合這些準則的所有︰  
  
-   是主控描繪清單方塊。  
  
-   沒有[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)樣式設定。  
  
-   有一個以上的項目。  
  
 您不應該自行呼叫此函式。 覆寫此函式可提供您自己的自訂處理鍵盤訊息。  
  
 在覆寫中，您必須傳回值來向架構指出您要執行什麼動作。 傳回值為-1 或 2 表示您處理所有層面的選取項目，並不需要任何進一步動作的清單方塊。 再傳回-1 或-2，您無法設定選取項目或移動插入號，或兩者。 若要設定選取範圍，請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移動插入號，請使用[SetCaretIndex](#setcaretindex)。  
  
 等於或大於 0 的傳回值會指定清單方塊中項目的索引，並指出清單方塊應該對指定的項目上的按鍵動作執行預設動作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="clistbox"></a>CListBox::CListBox  
 建構 `CListBox` 物件。  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>備註  
 您建構`CListBox`兩個步驟中的物件。 首先，呼叫建構函式**ClistBox** ，然後呼叫**建立**，其中初始化 Windows 清單方塊，並將它附加至`CListBox`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CListBox::CompareItem  
 由架構呼叫以判斷新的項目已排序的主控描繪清單方塊中的相對位置。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpCompareItemStruct`  
 長指標`COMPAREITEMSTRUCT`結構。  
  
### <a name="return-value"></a>傳回值  
 表示兩個項目中所述的相對位置[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)結構。 它可能是下列值之一︰  
  
|值|意義|  
|-----------|-------------|  
|-1|項目 1 排序項目 2 之前。|  
|0|項目 1 和 2 的項目排序相同。|  
|1|項目 1 排序項目 2 之後。|  
  
 請參閱[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)的說明`COMPAREITEMSTRUCT`結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 如果您建立主控描繪清單方塊**LBS_SORT**樣式，您必須覆寫此成員函式，以協助架構排序加入至清單方塊的新項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="create"></a>CListBox::Create  
 建立 Windows 清單方塊，並將它附加至`CListBox`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定清單方塊的樣式。 套用的任何組合[清單方塊樣式](../../mfc/reference/list-box-styles.md)到方塊。  
  
 `rect`  
 指定清單方塊的大小和位置。 可以是`CRect`物件或`RECT`結構。  
  
 `pParentWnd`  
 指定清單方塊的父視窗 (通常`CDialog`物件)。 它不得為**NULL**。  
  
 `nID`  
 指定清單方塊的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CListBox`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫**建立**，其中初始化 Windows 清單方塊，並將它附加至`CListBox`物件。  
  
 當**建立**執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)清單方塊控制項的訊息。  
  
 這些訊息會由預設的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式中`CWnd`基底類別。 若要擴充的預設訊息處理，衍生自`CListBox`、 將訊息對應新增到新的類別，並覆寫先前的訊息處理常式成員函式。 覆寫`OnCreate`，例如，若要執行所需的初始化新的類別。  
  
 套用下列[視窗樣式](../../mfc/reference/window-styles.md)至清單方塊控制項。  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**將垂直捲軸  
  
- **WS_HSCROLL**新增水平捲軸  
  
- **WS_GROUP**群組控制項  
  
- **WS_TABSTOP**允許這個控制項的定位停駐  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="deleteitem"></a>CListBox::DeleteItem  
 當使用者從主控描繪刪除項目時由架構呼叫`CListBox`物件或終結清單方塊。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDeleteItemStruct`  
 Windows 的長指標[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)結構，其中包含已刪除項目的相關資訊。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫這個函式來進行重繪視主控描繪清單方塊。  
  
 請參閱[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)的說明`DELETEITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="deletestring"></a>CListBox::DeleteString  
 刪除位置中的項目`nIndex`從清單方塊。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要刪除字串之以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 字串清單中所剩餘的計數。 傳回值是**LB_ERR**如果`nIndex`指定索引的項目數大於清單中。  
  
### <a name="remarks"></a>備註  
 之後的所有項目`nIndex`現在下移一個位置。 例如，如果清單方塊包含兩個項目，刪除第一個項目會導致要現在會在第一個位置中的剩餘項目。 `nIndex`= 0，第一個位置中的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="dir"></a>CListBox::Dir  
 將加入的檔案名稱、 磁碟機，或兩者都在清單方塊的清單。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>參數  
 `attr`  
 可以是任何組合的`enum`值中所述**CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus)，或任何組合的下列值︰  
  
|值|意義|  
|-----------|-------------|  
|0x0000|可讀取或寫入檔案。|  
|0x0001|可以讀取但是不會寫入檔案。|  
|0x0002|檔案隱藏的且不會出現在目錄清單中。|  
|0x0004|檔案是系統檔案。|  
|0x0010|所指定的名稱`lpszWildCard`指定的目錄。|  
|0x0020|已封存檔案。|  
|0x4000|包含符合所指定之名稱的所有磁碟機`lpszWildCard`。|  
|0x8000|Exclusive 旗標。 如果設定 exclusive 旗標，會列出指定類型的檔案。 否則，會列出指定之型別的的檔案，除了 「 標準 」 檔案。|  
  
 `lpszWildCard`  
 指向檔案規格字串。 字串可以包含萬用字元 (例如，*。\*)。  
  
### <a name="return-value"></a>傳回值  
 加入至清單的最後一個檔案名稱的以零為起始的索引。 傳回值是**LB_ERR**如果發生錯誤。 傳回的值是**LB_ERRSPACE**空間不足，無法是否可用來儲存新的字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="drawitem"></a>CListBox::DrawItem  
 當主控描繪清單方塊中變更的視覺外觀時，架構呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 長指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**和**itemState**成員`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。  
  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作主控描繪的繪圖`CListBox`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前此成員函式會結束。  
  
 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)的說明`DRAWITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="findstring"></a>CListBox::FindString  
 包含指定的前置詞，而不需要變更清單方塊選取項目在清單方塊中，尋找第一個字串。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到清單方塊底端時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 如果`nStartAfter`為-1，整個清單方塊會從一開始搜尋。  
  
 `lpszItem`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可能包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 相符的項目以零為起始索引或**LB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 使用[SelectString](#selectstring)尋找和選取字串的成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="findstringexact"></a>CListBox::FindStringExact  
 尋找符合指定字串的第一個清單方塊字串`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndexStart`  
 指定要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到清單方塊底端時，它會繼續從清單方塊的上方回所指定的項目`nIndexStart`。 如果`nIndexStart`為-1，整個清單方塊會從一開始搜尋。  
  
 `lpszFind`  
 指向以 null 結束的字串搜尋。 這個字串可以包含完整的檔名，包括副檔名。 搜尋不區分大小寫，因此字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 相符的項目索引或**LB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 如果使用清單方塊但不含建立主控描繪樣式[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)樣式，`FindStringExact`成員函式會嘗試比對的值的 doubleword 值`lpszFind`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="getanchorindex"></a>CListBox::GetAnchorIndex  
 擷取清單方塊中目前的錨定項目以零為起始的索引。  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前錨定項目索引，如果登錄成功。否則**LB_ERR**。  
  
### <a name="remarks"></a>備註  
 在多重選擇清單方塊中，錨定項目是連續的選取項目的區塊中的第一個或最後一個項目。  
  
### <a name="example"></a>範例  
  請參閱範例的[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="getcaretindex"></a>CListBox::GetCaretIndex  
 判斷具有焦點矩形，在多重選擇清單方塊中的項目索引。  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 具有焦點矩形，在清單方塊中的項目以零為起始的索引。 如果清單方塊會是單一選取清單方塊，傳回的值如果有的話，就會為已選取項目的索引。  
  
### <a name="remarks"></a>備註  
 可能還是無法選取項目。  
  
### <a name="example"></a>範例  
  請參閱範例的[CListBox::SetCaretIndex](#setcaretindex)。  
  
##  <a name="getcount"></a>CListBox::GetCount  
 擷取清單方塊中的項目數目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中的項目數或**LB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 傳回的計數是比最後一個項目 （索引以零為起始） 的索引值大一。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="getcursel"></a>CListBox::GetCurSel  
 如果有的話，在單一選取清單方塊中，擷取目前選取的項目，以零為起始的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果它是單一選取清單方塊目前選取之項目的以零為起始的索引。 它是`LB_ERR`如果目前不選取任何項目。  
  
 在多重選擇清單方塊中，具有焦點之項目的索引。  
  
### <a name="remarks"></a>備註  
 請勿呼叫`GetCurSel`多重選擇清單方塊。 使用[CListBox::GetSelItems](#getselitems)改為。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent  
 擷取從清單方塊中，它可以水平捲動的像素寬度。  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 可捲動的清單方塊中，單位為像素寬度。  
  
### <a name="remarks"></a>備註  
 這是清單方塊有水平捲軸時，才適用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="getitemdata"></a>CListBox::GetItemData  
 擷取與指定的清單方塊項目相關聯的應用程式提供 doubleword 值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 清單方塊中指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 項目，與關聯的 32 位元值或**LB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 Doubleword 值`dwItemData`參數[SetItemData](#setitemdata)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="getitemdataptr"></a>CListBox::GetItemDataPtr  
 擷取應用程式提供 32 位元相關聯的值與指定的清單方塊項目，做為指標 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 清單方塊中指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 擷取是指標，則為-1，如果發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="getitemheight"></a>CListBox::GetItemHeight  
 決定清單方塊中項目的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 清單方塊中指定項目的以零為起始的索引。 使用這個參數只有當清單方塊中含有**LBS_OWNERDRAWVARIABLE**樣式; 否則它應該設定為 0。  
  
### <a name="return-value"></a>傳回值  
 高度 （像素為單位的清單方塊中的項目）。 如果清單方塊中含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)樣式，則傳回值是所指定項目的高度`nIndex`。 如果發生錯誤，傳回值是**LB_ERR**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="getitemrect"></a>CListBox::GetItemRect  
 擷取矩形的維度該界限清單方塊項目是目前顯示在清單方塊視窗中。  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
 `lpRect`  
 指定的長指標[RECT 結構](../../mfc/reference/rect-structure1.md)接收項目的清單方塊用戶端座標。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**如果發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="getlistboxinfo"></a>CListBox::GetListBoxInfo  
 擷取每個資料行的項目數目。  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 每個資料行的項目數`CListBox`物件。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getlocale"></a>CListBox::GetLocale  
 擷取清單方塊所使用的地區設定。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的字串，地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 會使用地區設定，例如，以判斷在已排序的清單方塊中的字串的排序次序。  
  
### <a name="example"></a>範例  
  請參閱範例的[CListBox::SetLocale](#setlocale)。  
  
##  <a name="getsel"></a>CListBox::GetSel  
 擷取項目的選取狀態。  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 選取指定的項目; 如果是正數否則，它可以是 0。 傳回值是`LB_ERR`如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式會搭配兩個單一和多重選擇清單方塊。  
  
 若要擷取目前選取的清單方塊項目的索引，使用[CListBox::GetCurSel](#getcursel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="getselcount"></a>CListBox::GetSelCount  
 擷取多重選擇清單方塊中選取的項目的總數。  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中選取項目的計數。 如果清單方塊會是單一選取清單方塊，則傳回值是**LB_ERR**。  
  
### <a name="example"></a>範例  
  請參閱範例的[CListBox::GetSelItems](#getselitems)。  
  
##  <a name="getselitems"></a>CListBox::GetSelItems  
 在多重選擇清單方塊中指定選取之項目的項目編號的整數陣列中填入緩衝區。  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nMaxItems`  
 指定的項目編號要置於緩衝區中的選取項目數目上限。  
  
 `rgIndex`  
 指定緩衝區夠大的整數所指定數目的指標`nMaxItems`。  
  
### <a name="return-value"></a>傳回值  
 項目實際數目會放在緩衝區中。 如果清單方塊會是單一選取清單方塊，則傳回值是`LB_ERR`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="gettext"></a>CListBox::GetText  
 取得字串，從清單方塊。  
  
```  
int GetText(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
void GetText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要擷取之字串的以零為起始的索引。  
  
 `lpszBuffer`  
 指向接收字串的緩衝區。 緩衝區必須有足夠的空間，如字串和結束的 null 字元。 可以事先決定字串的大小，藉由呼叫`GetTextLen`成員函式。  
  
 `rString`  
 對 `CString` 物件的參考。  
  
### <a name="return-value"></a>傳回值  
 字串，但不包括結束的 null 字元的長度 （以位元組為單位）。 如果`nIndex`未指定有效的索引，則傳回值是**LB_ERR**。  
  
### <a name="remarks"></a>備註  
 這個成員的第二個表單函式的填滿`CString`具有字串文字物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="gettextlen"></a>CListBox::GetTextLen  
 清單方塊項目中取得字串的長度。  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定字串之以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 以字元為單位，但不包括結束的 null 字元字串的長度。 如果`nIndex`未指定有效的索引，則傳回值是**LB_ERR**。  
  
### <a name="example"></a>範例  
  請參閱範例的[CListBox::GetText](#gettext)。  
  
##  <a name="gettopindex"></a>CListBox::GetTopIndex  
 擷取清單方塊中的第一個可見項目以零為起始索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，在清單方塊中的第一個可見項目以零為起始索引**LB_ERR**否則。  
  
### <a name="remarks"></a>備註  
 一開始，項目 0 頂端的清單方塊中，但如果捲動清單方塊，另一個項目可能會在頂端。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="initstorage"></a>CListBox::InitStorage  
 配置記憶體來儲存清單方塊項目。  
  
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
 如果成功，最大數目的項目之前需要的記憶體配置，否則，清單方塊可以儲存**LB_ERRSPACE**，這表示沒有足夠的記憶體可用。  
  
### <a name="remarks"></a>備註  
 新增大量項目之前呼叫此函式`CListBox`。  
  
 此函式可協助加速有大量的項目 (超過 100) 的清單方塊的初始化。 它 preallocates 讓後續的記憶體數量指定[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函式接受最短的時間。 您可以使用估計值的參數。 如果增長時，會配置一些額外的記憶體。如果您低估，超過預先配置的量的項目使用一般配置。  
  
 只有 Windows 95/98:`nItems`參數會限制為 16 位元值。 這表示清單方塊不能包含超過 32,767 個項目。 雖然項目數目有限制，在清單方塊中項目的總大小只會受到可用記憶體。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="insertstring"></a>CListBox::InsertString  
 將字串插入至清單方塊。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要插入的字串之位置的以零為起始的索引。 如果這個參數是-1，則會將字串加入至清單的結尾。  
  
 `lpszItem`  
 指向要插入的 null 結尾字串。  
  
### <a name="return-value"></a>傳回值  
 已插入字串之位置以零為基底的索引。 傳回值是**LB_ERR**如果發生錯誤。 傳回的值是**LB_ERRSPACE**如果空間不足，無法使用存放新的字串。  
  
### <a name="remarks"></a>備註  
 不同於[AddString](#addstring)成員函式，`InsertString`不會造成與清單[LBS_SORT](../../mfc/reference/list-box-styles.md)排序樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="itemfrompoint"></a>CListBox::ItemFromPoint  
 決定最接近的指定點的清單方塊項目`pt`。  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 要尋找最接近的項目，指定相對於清單方塊的工作區的左上角的點。  
  
 `bOutside`  
 參考`BOOL`變數會設定為`TRUE`如果`pt`超出最接近的清單方塊項目的工作區`FALSE`如果`pt`在用戶端區域的最接近的清單方塊項目內。  
  
### <a name="return-value"></a>傳回值  
 最接近的項目中指定的點索引`pt`。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來判斷哪一個清單方塊項目上方移動滑鼠游標。  
  
### <a name="example"></a>範例  
  請參閱範例的[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="measureitem"></a>CListBox::MeasureItem  
 建立具有擁有者繪製樣式的清單方塊時由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpMeasureItemStruct`  
 長指標[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，並填寫`MEASUREITEMSTRUCT`結構，以通知 Windows 清單方塊的維度。 如果清單方塊以建立[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)樣式，架構會呼叫此成員函式的清單方塊中的每個項目。 否則，這個成員是只能呼叫一次。  
  
 以進一步了解使用[LBS_OWNERDRAWFIXED](../../mfc/reference/list-box-styles.md)以建立主控描繪清單方塊中的樣式`SubclassDlgItem`成員函式`CWnd`，請參閱[技術附註 14](../../mfc/tn014-custom-controls.md)。  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構**。**  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="resetcontent"></a>CListBox::ResetContent  
 從清單方塊中移除所有項目。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="selectstring"></a>CListBox::SelectString  
 搜尋符合指定的字串中，清單方塊項目和如果找到相符的項目，它會選取項目。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到清單方塊底端時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 如果`nStartAfter`為-1，整個清單方塊會從一開始搜尋。  
  
 `lpszItem`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可能包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 如果搜尋成功選取之項目的索引。 如果搜尋成功，則傳回值是**LB_ERR**且不會變更目前的選取範圍。  
  
### <a name="remarks"></a>備註  
 捲動清單方塊中，如有必要，將選取的項目帶入檢視。  
  
 此成員函式不能與清單方塊具有[LBS_MULTIPLESEL](../../mfc/reference/list-box-styles.md)樣式。  
  
 只有當其初始的字元 （從起點） 符合所指定的字串中的字元，選取一個項目`lpszItem`。  
  
 使用`FindString`成員函式，以尋找字串，而不需選取項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="selitemrange"></a>CListBox::SelItemRange  
 在多重選擇清單方塊中選取多個連續的項目。  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>參數  
 `bSelect`  
 指定如何設定選取範圍。 如果`bSelect`是**TRUE**，字串的選取，而且反白顯示; 如果**FALSE**，反白顯示，會移除，且不會再選取 字串。  
  
 `nFirstItem`  
 指定要設定的第一個項目以零為起始的索引。  
  
 `nLastItem`  
 指定要設定的最後一個項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式只適用於多重選擇清單方塊中。 如果您要在多重選擇清單方塊中選取一個項目，也就是如果`nFirstItem`等於`nLastItem`— 呼叫[SetSel](#setsel)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="setanchorindex"></a>CListBox::SetAnchorIndex  
 設定在多重選擇清單方塊中，開始的延伸選取範圍的錨點。  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定將會是錨點的清單方塊項目以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 在多重選擇清單方塊中，錨定項目是連續的選取項目的區塊中的第一個或最後一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="setcaretindex"></a>CListBox::SetCaretIndex  
 在多重選擇清單方塊中指定索引處的項目設定焦點矩形。  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要接收焦點矩形，清單方塊中的項目以零為起始的索引。  
  
 *bScroll*  
 如果此值為 0，直到可以完全看見捲動項目。 如果此值不是 0，此項目會捲動，直到至少部分顯示。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 如果看不到項目，它會捲動到檢視。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="setcolumnwidth"></a>CListBox::SetColumnWidth  
 在多重資料行的清單方塊中設定像素為單位的所有資料行的寬度 (以建立[LBS_MULTICOLUMN](../../mfc/reference/list-box-styles.md)樣式)。  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>參數  
 `cxWidth`  
 指定像素為單位的所有資料行的寬度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="setcursel"></a>CListBox::SetCurSel  
 選取字串，並捲動到檢視，如有必要。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>參數  
 `nSelect`  
 指定選取字串之以零為起始的索引。 如果`nSelect`為-1，清單方塊設定成有沒有選取項目。  
  
### <a name="return-value"></a>傳回值  
 `LB_ERR`如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 選取新的字串時，清單方塊會反白顯示，移除先前選取的字串。  
  
 此成員函式只適用於單一選擇清單方塊中。  
  
 若要設定或移除選擇多重選擇清單方塊中，使用[CListBox::SetSel](#setsel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent  
 設定寬度，單位為像素的清單方塊可以水平捲動。  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>參數  
 *cxExtent*  
 指定之清單方塊可以水平捲動的像素數目。  
  
### <a name="remarks"></a>備註  
 如果清單方塊的大小小於此值，水平捲軸會水平捲動清單方塊中的項目。 如果清單方塊會比此值較大，則會隱藏水平捲軸。  
  
 若要回應呼叫`SetHorizontalExtent`，清單方塊必須已定義與[WS_HSCROLL](../../mfc/reference/window-styles.md)樣式。  
  
 此成員函式不適用於多重資料行的清單方塊。 若是多重資料行的清單方塊中，呼叫`SetColumnWidth`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="setitemdata"></a>CListBox::SetItemData  
 設定在清單方塊中指定的項目相關聯的 32 位元值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
 `dwItemData`  
 指定要與此項目相關聯的值。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**如果發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="setitemdataptr"></a>CListBox::SetItemDataPtr  
 設定與指定的項目在清單方塊中，會指定的指標相關聯的 32 位元值 ( **void\***)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
 `pData`  
 指定要與此項目相關聯的指標。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 此指標會保持有效存留期之清單方塊中，即使在清單方塊內的項目相對位置可能會變更為新增或移除項目。 因此，可以變更方塊內項目的索引，但指標都可靠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="setitemheight"></a>CListBox::SetItemHeight  
 在清單方塊中，設定項目的高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 清單方塊中指定項目的以零為起始的索引。 使用這個參數只有當清單方塊中含有**LBS_OWNERDRAWVARIABLE**樣式; 否則它應該設定為 0。  
  
 `cyItemHeight`  
 指定高度，單位為像素的項目。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**如果高度的索引無效。  
  
### <a name="remarks"></a>備註  
 如果清單方塊中含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)樣式，此函式會將所指定項目的高度`nIndex`。 否則，此函式會將清單方塊中的所有項目高度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="setlocale"></a>CListBox::SetLocale  
 設定此清單方塊的地區設定識別碼。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>參數  
 `nNewLocale`  
 要設定的清單方塊的新的地區設定識別碼 (LCID) 值。  
  
### <a name="return-value"></a>傳回值  
 此清單方塊上一個地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 如果**SetLocale**不呼叫時，預設的地區設定從系統取得。 可以修改此系統的預設地區設定，使用 [控制台] 的地區 （或國際標準） 的應用程式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="setsel"></a>CListBox::SetSel  
 在多重選擇清單方塊中選取的字串。  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含要設定之字串的以零為起始的索引。 如果-1，選取項目已加入或移除的值而定的所有字串從`bSelect`。  
  
 `bSelect`  
 指定如何設定選取範圍。 如果`bSelect`是`TRUE`，字串的選取，而且反白顯示; 如果`FALSE`，反白顯示，會移除，且不會再選取 字串。 指定的字串的選取，而且預設反白顯示。  
  
### <a name="return-value"></a>傳回值  
 `LB_ERR`如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式只適用於多重選擇清單方塊中。  
  
 若要從單一選取清單方塊選取項目，使用[CListBox::SetCurSel](#setcursel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="settabstops"></a>CListBox::SetTabStops  
 設定在清單方塊中的定位停駐點位置。  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>參數  
 `cxEachStop`  
 定位停駐點會在設定每個`cxEachStop`對話方塊單位。 請參閱*rgTabStops*對話方塊單位的描述。  
  
 `nTabStops`  
 指定清單方塊中的定位停駐點數目。  
  
 `rgTabStops`  
 指向陣列的第一個成員包含在對話方塊單位中的定位停駐點位置的整數。 對話方塊單位是水平或垂直距離。 一個水平對話方塊單位等於目前對話方塊基底寬度單位的四分之一，而且一個垂直對話方塊單位等於目前對話方塊基底高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 **GetDialogBaseUnits** Windows 函式會傳回目前對話方塊基本單位像素為單位。 必須排序定位停駐點，以遞增順序排列;不允許背景索引標籤。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已設定的所有索引標籤。否則便是 0。  
  
### <a name="remarks"></a>備註  
 若要設定定位停駐點為預設大小的 2 對話方塊單位，呼叫此成員函式的無參數的版本。 若要設定定位停駐點 2 以外的大小，呼叫與版本`cxEachStop`引數。  
  
 若要設定定位停駐點大小的陣列，使用的版本與`rgTabStops`和`nTabStops`引數。 定位停駐點將會針對每個值中設定`rgTabStops`，最多指定的數字`nTabStops`。  
  
 若要回應呼叫`SetTabStops`成員函式，清單方塊必須已建立[LBS_USETABSTOPS](../../mfc/reference/list-box-styles.md)樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="settopindex"></a>CListBox::SetTopIndex  
 請確定特定的清單方塊項目會出現。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定清單方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，零或**LB_ERR**如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 系統會將清單方塊捲動直到其中一個所指定的項目`nIndex`會出現在清單頂端或最大捲軸範圍已達到。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="vkeytoitem"></a>CListBox::VKeyToItem  
 當清單方塊的父視窗收到時由架構呼叫`WM_VKEYTOITEM`從清單方塊的訊息。  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nKey`  
 索引鍵的虛擬按鍵碼的使用者按下。 標準虛擬按鍵碼的清單，請參閱 Winuser.h  
  
 `nIndex`  
 目前的清單方塊插入號位置。  
  
### <a name="return-value"></a>傳回值  
 會傳回-2 沒有進一步動作、-1 表示預設動作或為負數來指定要執行預設動作的按鍵輸入清單方塊項目的索引。  
  
### <a name="remarks"></a>備註  
 `WM_VKEYTOITEM`收到時，傳送訊息的清單方塊`WM_KEYDOWN`訊息，但只有是否在清單方塊符合下列兩個︰  
  
-   具有[LBS_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md)樣式設定。  
  
-   有一個以上的項目。  
  
 您不應該自行呼叫此函式。 覆寫此函式可提供您自己的自訂處理鍵盤訊息。  
  
 您必須傳回值來向架構指出您的覆寫執行什麼動作。 傳回值-2 表示應用程式處理所有層面的選取項目，並不需要任何進一步動作的清單方塊。 之前傳回-2，您無法設定選取項目或移動插入號，或兩者。 若要設定選取範圍，請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移動插入號，請使用[SetCaretIndex](#setcaretindex)。  
  
 傳回值為-1 表示清單方塊應該執行的預設動作，以回應按鍵。預設實作會傳回-1。  
  
 等於或大於 0 的傳回值會指定清單方塊中項目的索引，並指出清單方塊應該對指定的項目上的按鍵動作執行預設動作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox # 41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLTEST](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton 類別](../../mfc/reference/cbutton-class.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)   
 [CStatic 類別](../../mfc/reference/cstatic-class.md)

