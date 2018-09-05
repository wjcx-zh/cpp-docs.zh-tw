---
title: CListBox 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f67107b17f304c5a9c4d6f68d68797370502065
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761179"
---
# <a name="clistbox-class"></a>CListBox 類別
提供 Windows 清單方塊的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|建構 `CListBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|將字串加入至清單方塊中。|  
|[CListBox::CharToItem](#chartoitem)|覆寫，以提供自訂的 WM_CHAR 為主控描繪清單方塊沒有字串處理。|  
|[CListBox::CompareItem](#compareitem)|由架構呼叫以判斷新的項目已排序的主控描繪清單方塊中的位置。|  
|[CListBox::Create](#create)|建立 Windows 清單方塊，並將它附加至`CListBox`物件。|  
|[CListBox::DeleteItem](#deleteitem)|當使用者從主控描繪清單方塊刪除項目時，由架構呼叫。|  
|[CListBox::DeleteString](#deletestring)|從清單方塊中，刪除字串。|  
|[CListBox::Dir](#dir)|將檔案名稱、 磁碟機，或從目前的目錄加入至清單方塊中。|  
|[CListBox::DrawItem](#drawitem)|當主控描繪清單方塊中變更的視覺外觀時，架構呼叫。|  
|[Clistbox:: Findstring](#findstring)|搜尋清單方塊中的字串。|  
|[CListBox::FindStringExact](#findstringexact)|尋找符合指定的字串的第一個清單方塊字串。|  
|[CListBox::GetAnchorIndex](#getanchorindex)|擷取清單方塊中目前的錨點項目的以零為起始的索引。|  
|[CListBox::GetCaretIndex](#getcaretindex)|判斷具有焦點矩形的多重選擇清單方塊中的項目索引。|  
|[CListBox::GetCount](#getcount)|清單方塊中，傳回字串的數目。|  
|[CListBox::GetCurSel](#getcursel)|清單方塊中，會傳回目前所選字串之以零為起始索引。|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|傳回在清單方塊可以水平捲動的像素的寬度。|  
|[CListBox::GetItemData](#getitemdata)|傳回清單方塊項目相關聯的 32 位元值。|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|讓指標回到清單方塊項目。|  
|[CListBox::GetItemHeight](#getitemheight)|判斷清單方塊中的項目的高度。|  
|[CListBox::GetItemRect](#getitemrect)|傳回目前顯示的清單方塊項目的週框。|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|擷取每個資料行的項目數。|  
|[CListBox::GetLocale](#getlocale)|擷取清單方塊的地區設定識別碼。|  
|[CListBox::GetSel](#getsel)|傳回的清單方塊項目之選取狀態。|  
|[CListBox::GetSelCount](#getselcount)|傳回目前選取的多重選擇清單方塊中的字串數目。|  
|[CListBox::GetSelItems](#getselitems)|傳回目前在清單方塊中選取之字串的索引。|  
|[CListBox::GetText](#gettext)|將清單方塊項目複製到緩衝區。|  
|[CListBox::GetTextLen](#gettextlen)|傳回的長度，以位元組為單位的清單方塊項目。|  
|[CListBox::GetTopIndex](#gettopindex)|清單方塊中，會傳回第一個顯示字串的索引。|  
|[CListBox::InitStorage](#initstorage)|會預先配置清單方塊項目和字串的記憶體的區塊。|  
|[CListBox::InsertString](#insertstring)|清單方塊中的特定位置插入的字串。|  
|[CListBox::ItemFromPoint](#itemfrompoint)|傳回最接近點的清單方塊項目的索引。|  
|[CListBox::MeasureItem](#measureitem)|若要判斷清單方塊的維度建立主控描繪清單方塊時，由架構呼叫。|  
|[CListBox::ResetContent](#resetcontent)|清除清單方塊中的所有項目。|  
|[CListBox::SelectString](#selectstring)|搜尋並選取單一選取清單方塊中的字串。|  
|[CListBox::SelItemRange](#selitemrange)|選取或取消選取範圍，以複選清單方塊中的字串。|  
|[CListBox::SetAnchorIndex](#setanchorindex)|設定在多重選擇清單方塊中，若要開始以擴充的選取的錨點。|  
|[CListBox::SetCaretIndex](#setcaretindex)|多重選擇清單方塊中，指定索引處的項目設定焦點矩形。|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|設定多重資料行的清單方塊的資料行寬度。|  
|[CListBox::SetCurSel](#setcursel)|選取清單方塊的字串。|  
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|設定在清單方塊可以水平捲動的像素的寬度。|  
|[CListBox::SetItemData](#setitemdata)|設定清單方塊項目相關聯的 32 位元值。|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|清單方塊項目設定的指標。|  
|[CListBox::SetItemHeight](#setitemheight)|清單方塊中，設定項目的高度。|  
|[CListBox::SetLocale](#setlocale)|設定清單方塊的地區設定識別碼。|  
|[CListBox::SetSel](#setsel)|選取或取消選取多重選擇清單方塊中的清單方塊項目。|  
|[CListBox::SetTabStops](#settabstops)|設定清單方塊中的定位停駐點位置。|  
|[CListBox::SetTopIndex](#settopindex)|清單方塊中設定的第一個可見的字串以零為起始的索引。|  
|[CListBox::VKeyToItem](#vkeytoitem)|覆寫，以提供自訂的 WM_KEYDOWN LBS_WANTKEYBOARDINPUT 設定樣式的清單方塊處理。|  
  
## <a name="remarks"></a>備註  
 清單方塊會顯示一份項目，例如檔案名稱，使用者可以檢視和選取。  
  
 在單一選取清單方塊中，使用者可以選取一個項目。 在多重選擇清單方塊中，您可以選取的項目範圍。 當使用者選取項目時，它會反白顯示和清單方塊會將通知訊息傳送至父視窗。  
  
 從對話方塊範本，或是直接在您的程式碼中，您可以建立一個清單方塊。 若要直接建立，建構`CListBox`物件，然後呼叫[建立](#create)成員函式來建立 Windows 清單方塊控制項，並將其附加至`CListBox`物件。 若要使用的對話方塊範本中的清單方塊，清單方塊中宣告變數對話方塊類別，然後使用`DDX_Control`在您的對話方塊類別的`DoDataExchange`函式來連線至控制項的成員變數。 （這是為了自動控制變數加入您的對話方塊類別時。）  
  
 建構可以是單一步驟中的處理序類別，衍生自`CListBox`。 寫入的建構函式在衍生的類別並呼叫`Create`從建構函式內。  
  
 如果您想要處理的清單方塊傳送給其父代的 Windows 通知訊息 (通常是從衍生的類別[CDialog](../../mfc/reference/cdialog-class.md))，將訊息對應項目和訊息處理常式成員函式新增至每個訊息的父類別。  
  
 每個訊息對應項目都會使用下列格式：  
  
 `ON_Notification( id, memberFxn )`  
  
 何處`id`指定傳送通知的清單方塊控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 父代的函式原型如下所示：  
  
 `afx_msg void memberFxn( );`  
  
 以下是一份潛在的訊息對應項目並在其中它們就會傳送到父代的案例的描述：  
  
- ON_LBN_DBLCLK 使用者按兩下清單方塊中的字串。 僅有的清單方塊[LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式會傳送此通知訊息。  
  
- ON_LBN_ERRSPACE 清單方塊無法配置足夠的記憶體，以滿足要求。  
  
- ON_LBN_KILLFOCUS 清單方塊正失去輸入的焦點。  
  
- ON_LBN_SELCANCEL 取消目前的清單方塊選取項目。 當清單方塊具有 LBS_NOTIFY 樣式時，才會傳送此訊息。  
  
- ON_LBN_SELCHANGE 清單方塊中選取項目已變更。 如果選取項目已變更，不會傳送此通知[CListBox::SetCurSel](#setcursel)成員函式。 此通知僅適用於具有 LBS_NOTIFY 樣式的清單方塊。 LBN_SELCHANGE 通知訊息會傳送多重選擇清單方塊，使用者按下方向鍵，即使選取範圍不會變更。  
  
- ON_LBN_SETFOCUS 清單方塊會收到輸入的焦點。  
  
- ON_WM_CHARTOITEM 有沒有任何主控描繪清單方塊中，會收到 WM_CHAR 訊息。  
  
- LBS_WANTKEYBOARDINPUT 樣式 ON_WM_VKEYTOITEM 的清單方塊中，會收到 WM_KEYDOWN 訊息。  
  
 如果您建立`CListBox` 對話方塊中 （透過對話方塊資源），物件`CListBox`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CListBox`物件內的視窗中，您可能需要終結`CListBox`物件。 如果您建立`CListBox`物件在堆疊上，它會自動終結。 如果您建立`CListBox`使用堆積上的物件**新**函式，您必須呼叫**刪除**終結它，當使用者關閉父視窗物件。  
  
 如果您配置任何記憶體`CListBox`物件，覆寫`CListBox`解構函式來進行處置的配置。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="addstring"></a>  CListBox::AddString  
 將字串加入至清單方塊中。  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 *lpszItem*  
 指向以 null 結束的字串，會加入。  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的字串以零為起始的索引。 如果發生錯誤，傳回的值會為 LB_ERR如果空間不足無法存放新的字串，傳回的值會是 LB_ERRSPACE。  
  
### <a name="remarks"></a>備註  
 如果清單方塊不以建立[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，字串會新增至清單的結尾。 否則，字串插入至清單中，而且排序清單。 是否使用 LBS_SORT 樣式建立的清單方塊而非[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，framework 排序清單由一或多個呼叫`CompareItem`成員函式。  
  
 使用[InsertString](#insertstring)將清單方塊內的特定位置插入的字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="chartoitem"></a>  CListBox::CharToItem  
 當清單方塊的父視窗收到 WM_CHARTOITEM 訊息在清單方塊中，由架構呼叫。  
  
```  
virtual int CharToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nKey*  
 ANSI 程式碼的使用者所輸入的字元。  
  
 *nIndex*  
 目前的清單方塊的插入號位置。  
  
### <a name="return-value"></a>傳回值  
 傳回-1 或 2，任何進一步的動作或非負數的數字，指定要執行預設動作的按鍵輸入清單方塊項目的索引。 預設實作會傳回-1。  
  
### <a name="remarks"></a>備註  
 當它收到 WM_CHAR 訊息，但只有在清單方塊符合這些準則的所有清單方塊所傳送 WM_CHARTOITEM 訊息：  
  
-   是主控描繪清單方塊。  
  
-   沒有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式集。  
  
-   具有至少一個項目。  
  
 您永遠不應該自己呼叫這個函式。 覆寫此函式可提供您自己的自訂處理鍵盤訊息。  
  
 在您的覆寫中，您必須傳回值來向架構指出您已執行哪些動作。 傳回值為-1 或 2 表示您處理選取的項目的所有層面，並不需要任何進一步的動作清單方塊。 再傳回-1 或-2，您可以設定選取項目或移動插入號，或兩者。 若要設定選取項目，請使用[SetCurSel](#setcursel)或是[SetSel](#setsel)。 若要移動插入號，請使用[SetCaretIndex](#setcaretindex)。  
  
 大於或等於 0 的傳回值的清單方塊中指定的項目索引，並指出清單方塊應該執行的預設動作，在指定的項目上的按鍵輸入。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="clistbox"></a>  CListBox::CListBox  
 建構 `CListBox` 物件。  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>備註  
 您建構`CListBox`兩個步驟中的物件。 首先，呼叫建構函式`ClistBox`，然後呼叫`Create`，其中初始化 Windows 清單方塊，並將它附加至`CListBox`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="compareitem"></a>  CListBox::CompareItem  
 由架構呼叫以判斷新的項目已排序的主控描繪清單方塊中的相對位置。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpCompareItemStruct*  
 長指標`COMPAREITEMSTRUCT`結構。  
  
### <a name="return-value"></a>傳回值  
 指出兩個項目中所述的相對位置[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)結構。 它可能是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|-1|項目 1 排序項目 2 之前。|  
|0|項目 1 和 2 的項目排序相同。|  
|1|項目 2 之後，排序項目 1。|  
  
 請參閱[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)的說明`COMPAREITEMSTRUCT`結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 如果您建立主控描繪清單方塊的 LBS_SORT 樣式時，您必須覆寫此成員函式，以協助架構排序新的項目加入至清單方塊中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="create"></a>  CListBox::Create  
 建立 Windows 清單方塊，並將它附加至`CListBox`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *cheaderctrl:: Create*  
 指定清單方塊的樣式。 套用的任何組合[清單方塊樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)至方塊。  
  
 *rect*  
 指定清單方塊的大小和位置。 可以是`CRect`物件或`RECT`結構。  
  
 *pParentWnd*  
 指定清單方塊的父視窗 (通常`CDialog`物件)。 它必須不是 NULL。  
  
 *nID*  
 指定清單方塊的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CListBox`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫`Create`，其中初始化 Windows 清單方塊，並將它附加至`CListBox`物件。  
  
 當`Create`執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，並[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)清單方塊控制項的訊息。  
  
 根據預設，處理這些訊息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，以及[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式在 `CWnd`基底類別。 若要擴充的預設訊息處理，衍生的類別`CListBox`、 將訊息對應新增至新的類別，並覆寫先前的訊息處理常式成員函式。 覆寫`OnCreate`，例如，若要執行的新類別所需的初始設定。  
  
 套用下列[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)至清單方塊控制項。  
  
- WS_CHILD 一律  
  
- WS_VISIBLE 通常  
  
- WS_DISABLED 很少  
  
- WS_VSCROLL 若要新增 垂直捲軸  
  
- WS_HSCROLL 若要新增 水平捲軸  
  
- WS_GROUP 群組控制項  
  
- WS_TABSTOP，以允許這個控制項定位停駐點  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="deleteitem"></a>  CListBox::DeleteItem  
 由架構呼叫，當使用者刪除的項目從主控描繪`CListBox`物件或終結清單方塊。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDeleteItemStruct*  
 Windows 的長指標[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)結構，包含已刪除的項目相關的資訊。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫這個函式來重繪視主控描繪清單方塊。  
  
 請參閱[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)的說明`DELETEITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="deletestring"></a>  CListBox::DeleteString  
 刪除位置中的項目*nIndex*從清單方塊。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定要刪除之字串的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 在清單中所剩餘的字串數目。 如果，則傳回的值為 LB_ERR *nIndex*指定索引的項目數大於清單中。  
  
### <a name="remarks"></a>備註  
 之後的所有項目*nIndex*現在向下移動一個位置。 比方說，如果清單方塊包含兩個項目，刪除第一個項目會導致要現在是在第一個位置中的其餘項目。 *nIndex*= 0 中的第一個位置的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="dir"></a>  CListBox::Dir  
 加入檔案名稱、 磁碟機，或兩者都為清單方塊的清單。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>參數  
 *attr*  
 可以是任意的組合**enum**值中所述`CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus)，或任何組合的下列值：  
  
|值|意義|  
|-----------|-------------|  
|0x0000|可讀取或寫入檔案。|  
|0x0001|可以讀取但不是會寫入至檔案。|  
|0x0002|檔案隱藏的而且沒有出現在目錄清單中。|  
|0x0004|檔案是系統檔案。|  
|0x0010|所指定的名稱*lpszWildCard*指定的目錄。|  
|0x0020|封存的檔案。|  
|0x4000|包含符合指定之名稱的所有磁碟機*lpszWildCard*。|  
|0x8000|獨佔的旗標。 如果設定專屬的旗標，會列出指定類型的檔案。 否則會列出指定型別的的檔案，除了 「 正常 」 的檔案。|  
  
 *lpszWildCard*  
 指向檔案規格字串。 字串可以包含萬用字元 (例如，*。\*)。  
  
### <a name="return-value"></a>傳回值  
 最後一個新增至清單的檔名的以零起始的索引。 如果發生錯誤，傳回的值會為 LB_ERR如果空間不足無法存放新的字串，傳回的值會是 LB_ERRSPACE。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="drawitem"></a>  CListBox::DrawItem  
 當主控描繪清單方塊中變更的視覺外觀時，架構呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDrawItemStruct*  
 長指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含的所需的繪圖類型的相關資訊。  
  
### <a name="remarks"></a>備註  
 `itemAction`並`itemState`的成員`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。  
  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作活動，抽獎獲得主控描繪`CListBox`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前此成員函式會結束。  
  
 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)的說明`DRAWITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="findstring"></a>  Clistbox:: Findstring  
 尋找第一個字串，而不需要變更清單方塊選取項目包含指定的前置詞的清單方塊中。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>參數  
 *nStartAfter*  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到底部的清單方塊中時，它會繼續從清單方塊的上方回到指定的項目*nStartAfter*。 如果*nStartAfter*為-1，整個清單方塊會從一開始搜尋。  
  
 *lpszItem*  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋會是大小寫無關，因此這個字串可能包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 相符的項目或如果搜尋成功 LB_ERR 的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 使用[SelectString](#selectstring)尋找和選取字串的成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="findstringexact"></a>  CListBox::FindStringExact  
 尋找符合指定之字串的第一個清單方塊字串*lpszFind*。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndexStart*  
 指定要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到底部的清單方塊中時，它會繼續從清單方塊的上方回到指定的項目*nIndexStart*。 如果*nIndexStart*為-1，整個清單方塊會從一開始搜尋。  
  
 *lpszFind*  
 指向以 null 結束的字串搜尋。 此字串可以包含完整的檔名，包括副檔名。 搜尋不區分大小寫，因此字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 相符的項目或如果搜尋成功 LB_ERR 的索引。  
  
### <a name="remarks"></a>備註  
 如果使用清單方塊但建立主控描繪樣式[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式`FindStringExact`成員函式會嘗試比對的值 doubleword 值*lpszFind*。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex  
 擷取清單方塊中目前的錨點項目的以零為起始的索引。  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前錨點項目的索引，如果登錄成功。否則 LB_ERR。  
  
### <a name="remarks"></a>備註  
 在多重選擇清單方塊中，錨點項目是連續的選取項目的區塊中的第一個或最後一個項目。  
  
### <a name="example"></a>範例  
  範例，請參閱[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex  
 判斷具有焦點矩形的多重選擇清單方塊中的項目索引。  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊具有焦點矩形的項目以零為起始的索引。 如果清單方塊會是單一選取清單方塊，如果有任何傳回的值為已選取項目的索引。  
  
### <a name="remarks"></a>備註  
 項目可能會或可能未選取。  
  
### <a name="example"></a>範例  
  範例，請參閱[CListBox::SetCaretIndex](#setcaretindex)。  
  
##  <a name="getcount"></a>  CListBox::GetCount  
 擷取清單方塊中的項目數。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中或 LB_ERR 發生錯誤的項目數目。  
  
### <a name="remarks"></a>備註  
 傳回的計數是一個大於索引值的最後一個項目 （索引以零為起始）。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="getcursel"></a>  CListBox::GetCurSel  
 如果有的話，單一選取清單方塊中，擷取目前選取的項目，為起始的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的項目，如果它是單一選取清單方塊的以零為起始的索引。 如果目前未不選取任何項目，它就會是 LB_ERR。  
  
 在多重選擇清單方塊中，具有焦點之項目的索引。  
  
### <a name="remarks"></a>備註  
 請勿呼叫`GetCurSel`多重選擇清單方塊。 使用[CListBox::GetSelItems](#getselitems)改。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="gethorizontalextent"></a>  CListBox::GetHorizontalExtent  
 擷取從清單方塊的寬度，以供它可以是水平捲動的像素為單位。  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中，像素為單位的可捲動的寬度。  
  
### <a name="remarks"></a>備註  
 這是清單方塊有水平捲軸時，才適用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="getitemdata"></a>  CListBox::GetItemData  
 擷取指定的清單方塊項目相關聯的應用程式提供 doubleword 值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 在清單方塊中指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果發生錯誤相關聯的項目或 LB_ERR 32 位元值。  
  
### <a name="remarks"></a>備註  
 Doubleword 值*dwItemData*的參數[SetItemData](#setitemdata)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr  
 擷取應用程式所提供的 32 位元值，而此一做為指標指定的清單方塊項目相關聯 (**void** <strong>\*</strong>)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 在清單方塊中指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果發生錯誤，請擷取是指標，則為-1。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="getitemheight"></a>  CListBox::GetItemHeight  
 判斷清單方塊中的項目的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 在清單方塊中指定項目的以零為起始的索引。 此參數在清單方塊中含有 LBS_OWNERDRAWVARIABLE 樣式; 時，才會使用否則，它應該設定為 0。  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素的清單方塊中的項目。 如果清單方塊中含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，則傳回值是所指定項目的高度*nIndex*。 如果發生錯誤，則傳回的值會是 LB_ERR。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="getitemrect"></a>  CListBox::GetItemRect  
 擷取矩形的維度的界限清單方塊項目目前顯示在清單方塊 視窗中。  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定項目的以零為起始的索引。  
  
 *lpRect*  
 指定的長指標[RECT 結構](../../mfc/reference/rect-structure1.md)接收項目的清單方塊用戶端座標。  
  
### <a name="return-value"></a>傳回值  
 LB_ERR 發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo  
 擷取每個資料行的項目數。  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 每個資料行的項目數`CListBox`物件。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬[LB_GETLISTBOXINFO](/windows/desktop/Controls/lb-getlistboxinfo)訊息、 Windows SDK 中所述。  
  
##  <a name="getlocale"></a>  CListBox::GetLocale  
 擷取清單方塊所使用的地區設定。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的字串，地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 使用地區設定是，比方說，若要判斷已排序的清單方塊中字串的排序次序。  
  
### <a name="example"></a>範例  
  範例，請參閱[CListBox::SetLocale](#setlocale)。  
  
##  <a name="getsel"></a>  CListBox::GetSel  
 擷取項目的選取狀態。  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果指定的項目已選取;，正數否則，它會是 0。 如果發生錯誤時，傳回的值將為 LB_ERR。  
  
### <a name="remarks"></a>備註  
 此成員函式搭配兩個單一和多重選擇清單方塊。  
  
 若要擷取目前選取的清單方塊項目的索引，請使用[CListBox::GetCurSel](#getcursel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="getselcount"></a>  CListBox::GetSelCount  
 擷取多重選擇清單方塊中選取的項目總數。  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中選取的項目數目。 如果清單方塊會是單一選取清單方塊，則傳回的值會是 LB_ERR。  
  
### <a name="example"></a>範例  
  範例，請參閱[CListBox::GetSelItems](#getselitems)。  
  
##  <a name="getselitems"></a>  CListBox::GetSelItems  
 多重選擇清單方塊中指定選取之項目的項目編號的整數陣列中填入緩衝區。  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nMaxItems*  
 指定選取的項目編號要放置在緩衝區中的項目數目上限。  
  
 *rgIndex*  
 指定的緩衝區不夠大，所指定的整數數目的指標*nMaxItems*。  
  
### <a name="return-value"></a>傳回值  
 實際數目的項目放到緩衝區。 如果清單方塊會是單一選取清單方塊，則傳回值是`LB_ERR`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="gettext"></a>  CListBox::GetText  
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
 *nIndex*  
 指定要擷取之字串的以零為起始的索引。  
  
 *lpszBuffer*  
 要接收字串之緩衝區的點。 緩衝區必須有足夠的空間，如字串和結束的 null 字元。 可以事先判斷字串的大小，藉由呼叫`GetTextLen`成員函式。  
  
 *rString*  
 對 `CString` 物件的參考。  
  
### <a name="return-value"></a>傳回值  
 字串，但不包含終止的 null 字元的長度 （以位元組為單位）。 如果*nIndex*未指定有效的索引，則傳回值是 LB_ERR。  
  
### <a name="remarks"></a>備註  
 這個成員的第二種形式的函式會填滿`CString`具有字串文字物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="gettextlen"></a>  CListBox::GetTextLen  
 取得字串的長度，在清單方塊項目。  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定字串之以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 以字元為單位，但不包含終止的 null 字元字串的長度。 如果*nIndex*未指定有效的索引，則傳回值是 LB_ERR。  
  
### <a name="example"></a>範例  
  範例，請參閱[CListBox::GetText](#gettext)。  
  
##  <a name="gettopindex"></a>  CListBox::GetTopIndex  
 擷取的清單方塊中的第一個可見項目以零為起始的索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，清單方塊中的第一個可見項目以零為起始索引 LB_ERR，否則為。  
  
### <a name="remarks"></a>備註  
 一開始，項目 0 頂端的清單方塊中，但如果捲動清單方塊，另一個項目可能會在頂端。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="initstorage"></a>  CListBox::InitStorage  
 儲存清單方塊項目會配置記憶體。  
  
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
 如果成功，清單方塊可以儲存在記憶體重新配置之前的項目最大數目是有需要否則為 LB_ERRSPACE，這表示沒有足夠記憶體可供使用。  
  
### <a name="remarks"></a>備註  
 新增大量的項目之前呼叫此函式`CListBox`。  
  
 此函式可協助加速有大量的項目 (超過 100) 的清單方塊的初始化。 它會預先配置的指定讓後續的記憶體數量[AddString](#addstring)， [InsertString](#insertstring)，並[Dir](#dir)函式接受最短的時間。 您可以使用估計值的參數。 如果在增長時，會配置一些額外的記憶體;如果您低估，一般配置使用超過預先配置的量的項目。  
  
 Windows 95/98 只： *nItems*參數會限制為 16 位元值。 這表示清單方塊不能包含超過 32,767 個項目。 雖然項目數目有限制，總大小的清單方塊中的項目只會受到可用記憶體。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="insertstring"></a>  CListBox::InsertString  
 將字串插入至清單方塊。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定插入至字串位置的以零為起始的索引。 如果這個參數是-1，則會將字串加入至清單的結尾。  
  
 *lpszItem*  
 指向要插入的 null 結尾字串。  
  
### <a name="return-value"></a>傳回值  
 已插入字串之位置以零為基底的索引。 如果發生錯誤，傳回的值會為 LB_ERR如果空間不足無法存放新的字串，傳回的值會是 LB_ERRSPACE。  
  
### <a name="remarks"></a>備註  
 不同於[AddString](#addstring)成員函式`InsertString`不會造成與清單[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)排序樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint  
 決定最接近指定點的清單方塊項目*pt*。  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>參數  
 *太平洋時間*  
 要尋找最接近的項目，指定相對於清單方塊的用戶端區域左上角的點。  
  
 *bOutside*  
 參考會設為 TRUE 的 BOOL 變數*pt*超出工作區的最接近的清單方塊項目，false *pt*的最接近的清單方塊項目在用戶端區域內。  
  
### <a name="return-value"></a>傳回值  
 最接近的項目中指定點的索引*pt*。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來判斷在滑鼠游標移哪一個清單方塊項目。  
  
### <a name="example"></a>範例  
  範例，請參閱[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="measureitem"></a>  CListBox::MeasureItem  
 建立具有主控描繪樣式的清單方塊時，由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpMeasureItemStruct*  
 長指標[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，並填寫`MEASUREITEMSTRUCT`結構以通知 Windows 清單方塊的維度。 如果清單方塊以建立[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，架構會呼叫此成員函式的清單方塊中的每個項目。 否則，這個成員是只呼叫一次。  
  
 如需使用的進一步資訊[LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)以建立主控描繪清單方塊中的樣式`SubclassDlgItem`成員函式`CWnd`，請參閱中的討論[技術附註 14](../../mfc/tn014-custom-controls.md).  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="resetcontent"></a>  CListBox::ResetContent  
 從清單方塊中移除所有項目。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="selectstring"></a>  CListBox::SelectString  
 搜尋清單方塊項目符合指定的字串，以及如果找到相符的項目，則它會選取項目。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 *nStartAfter*  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當搜尋到底部的清單方塊中時，它會繼續從清單方塊的上方回到指定的項目*nStartAfter*。 如果*nStartAfter*為-1，整個清單方塊會從一開始搜尋。  
  
 *lpszItem*  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋會是大小寫無關，因此這個字串可能包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 如果搜尋成功，所選取項目的索引。 如果搜尋成功，則傳回值是 LB_ERR 並不會變更目前的選取範圍。  
  
### <a name="remarks"></a>備註  
 捲動清單方塊，如有必要，將選取的項目帶入檢視。  
  
 此成員函式不能搭配具有的清單方塊[LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式。  
  
 只有當其起始的字元 （從起點） 符合所指定的字串中的字元，選取項目*lpszItem*。  
  
 使用`FindString`成員函式，若要尋找的字串，而不需選取項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="selitemrange"></a>  CListBox::SelItemRange  
 多重選擇清單方塊中選取多個連續的項目。  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>參數  
 *bSelect*  
 指定如何設定選取項目。 如果*bSelect*為 TRUE，即選取字串，並將其反白顯示; 如果為 FALSE，移除反白顯示的字串不會再選取。  
  
 *nFirstItem*  
 指定要設定的第一個項目以零為起始的索引。  
  
 *nLastItem*  
 指定要設定的最後一個項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 LB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式只適用於多重選擇清單方塊中。 如果您要在多重選擇清單方塊中選取一個項目 — 也就是，如果*nFirstItem*等於*nLastItem* — 呼叫[SetSel](#setsel)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex  
 設定在多重選擇清單方塊中，若要開始以擴充的選取的錨點。  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定將會是錨點的清單方塊項目以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 在多重選擇清單方塊中，錨點項目是連續的選取項目的區塊中的第一個或最後一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex  
 多重選擇清單方塊中，指定索引處的項目設定焦點矩形。  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定要接收焦點矩形，在清單方塊中的項目以零為起始的索引。  
  
 *bScroll*  
 如果此值為 0，直到可以完全看見捲動項目。 如果此值不是 0，此項目捲動直到至少部分可見。  
  
### <a name="return-value"></a>傳回值  
 LB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 如果看不到項目，它被捲動檢視。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth  
 多重資料行的清單方塊中設定像素為單位的所有資料行的寬度 (以建立[LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式)。  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>參數  
 *cxWidth*  
 指定像素為單位的所有資料行的寬度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="setcursel"></a>  CListBox::SetCurSel  
 選取字串，並捲動到檢視，如有必要。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>參數  
 *n 請選取*  
 指定要選取字串之以零為起始索引。 如果*n 請選取*為-1，清單方塊設定成有沒有選取項目。  
  
### <a name="return-value"></a>傳回值  
 LB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 選取新的字串時，清單方塊會從先前選取的字串移除反白顯示。  
  
 此成員函式只能用於單一選取清單方塊中。  
  
 若要設定或移除複選清單方塊中的選取項目，使用[CListBox::SetSel](#setsel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="sethorizontalextent"></a>  CListBox::SetHorizontalExtent  
 設定寬度，單位為像素的清單方塊可以水平捲動。  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>參數  
 *cxExtent*  
 指定的清單方塊可以水平捲動的像素數。  
  
### <a name="remarks"></a>備註  
 如果清單方塊的大小小於此值，水平捲軸會水平捲動清單方塊中的項目。 如果清單方塊一樣大，或大於此值，則會隱藏水平捲軸。  
  
 呼叫以回應`SetHorizontalExtent`，清單方塊必須已有定義[WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles)樣式。  
  
 此成員函式不適用於多重資料行的清單方塊。 若是多重資料行的清單方塊中，呼叫`SetColumnWidth`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="setitemdata"></a>  CListBox::SetItemData  
 設定清單方塊中指定的項目相關聯的 32 位元值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定項目的以零為起始的索引。  
  
 *dwItemData*  
 指定要與項目相關聯的值。  
  
### <a name="return-value"></a>傳回值  
 LB_ERR 發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr  
 設定為指定的指標清單方塊中指定的項目相關聯的 32 位元值 ( **void** <strong>\*</strong>)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定項目的以零為起始的索引。  
  
 *pData*  
 指定要與項目相關聯的指標。  
  
### <a name="return-value"></a>傳回值  
 LB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 此指標會保持有效存留期內的清單方塊中，即使新增或移除項目時，可能會變更的項目在清單方塊內的相對位置。 因此，在方塊內項目的索引可能會變更，但，指標都是可靠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="setitemheight"></a>  CListBox::SetItemHeight  
 清單方塊中，設定項目的高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 在清單方塊中指定項目的以零為起始的索引。 此參數在清單方塊中含有 LBS_OWNERDRAWVARIABLE 樣式; 時，才會使用否則，它應該設定為 0。  
  
 *cyItemHeight*  
 指定高度，單位為像素的項目。  
  
### <a name="return-value"></a>傳回值  
 如果是無效的索引或高度，LB_ERR。  
  
### <a name="remarks"></a>備註  
 如果清單方塊中含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，此函式會設定所指定項目的高度*nIndex*。 否則，此函式會設定所有項目的高度清單方塊中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="setlocale"></a>  CListBox::SetLocale  
 設定此清單方塊的地區設定識別碼。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>參數  
 *nNewLocale*  
 要設定的清單方塊的新地區設定識別碼 (LCID) 值。  
  
### <a name="return-value"></a>傳回值  
 此清單方塊上一個地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 如果`SetLocale`不呼叫時，預設的地區設定從系統取得。 此系統預設地區設定可以修改使用 [控制台] 的區域 （或國際） 的應用程式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="setsel"></a>  CListBox::SetSel  
 多重選擇清單方塊中選取一個字串。  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 包含要設定的字串以零為起始的索引。 如果為-1，選取項目加入或移除的值而定的所有字串*bSelect*。  
  
 *bSelect*  
 指定如何設定選取項目。 如果*bSelect*為 TRUE，即選取字串，並將其反白顯示; 如果為 FALSE，移除反白顯示的字串不會再選取。 已選取指定的字串，並反白顯示的預設值。  
  
### <a name="return-value"></a>傳回值  
 LB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式只適用於多重選擇清單方塊中。  
  
 若要從單一選取清單方塊中選取項目，請使用[CListBox::SetCurSel](#setcursel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="settabstops"></a>  CListBox::SetTabStops  
 設定清單方塊中的定位停駐點位置。  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>參數  
 *cxEachStop*  
 在設定定位停駐點，會每隔*cxEachStop*對話方塊單位。 請參閱*rgTabStops*對話方塊單位的描述。  
  
 *nTabStops*  
 指定在清單方塊中的定位停駐點數目。  
  
 *rgTabStops*  
 指向陣列的第一個成員包含在對話方塊單位中的定位停駐點位置的整數。 對話方塊單位是水平或垂直距離。 一個水平對話方塊單位等於目前對話方塊基底寬度單位的四分之一，而且一個垂直對話方塊單位等於目前對話方塊基底的高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 `GetDialogBaseUnits` Windows 函式會傳回目前對話方塊基底的單位像素為單位。 定位停駐點必須以遞增順序排序不允許反向索引標籤。  
  
### <a name="return-value"></a>傳回值  
 如果已設定的所有索引標籤，為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 若要設定定位停駐點的預設大小的 2 個對話方塊單位，呼叫此成員函式的無參數的版本。 若要設定定位停駐點到 2 以外的大小，呼叫的版本與*cxEachStop*引數。  
  
 若要設定定位停駐點大小的陣列，使用的版本與*rgTabStops*並*nTabStops*引數。 將設定中每個值的定位停駐點*rgTabStops*，最多指定數目*nTabStops*。  
  
 呼叫以回應`SetTabStops`成員函式，在清單方塊必須已建立[LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="settopindex"></a>  CListBox::SetTopIndex  
 請確定特定的清單方塊項目會出現。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 指定清單方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，為零或 LB_ERR 發生錯誤。  
  
### <a name="remarks"></a>備註  
 系統會將清單方塊捲動直到其中一個所指定的項目*nIndex*會出現在清單頂端或最大捲軸範圍已達到。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem  
 當清單方塊的父視窗收到 WM_VKEYTOITEM 訊息在清單方塊中，由架構呼叫。  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nKey*  
 索引鍵的虛擬按鍵碼使用者按下。 如需標準虛擬按鍵碼的清單，請參閱 Winuser.h  
  
 *nIndex*  
 目前的清單方塊的插入號位置。  
  
### <a name="return-value"></a>傳回值  
 傳回-2 沒有進一步的動作、-1 表示預設的動作或為負數來指定要執行的按鍵輸入的預設動作的清單方塊項目的索引。  
  
### <a name="remarks"></a>備註  
 WM_VKEYTOITEM 訊息所傳送的清單方塊中，當它收到 WM_KEYDOWN 訊息，但只有在清單方塊會符合下列兩個：  
  
-   已[LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式集。  
  
-   具有至少一個項目。  
  
 您永遠不應該自己呼叫這個函式。 覆寫此函式可提供您自己的自訂處理鍵盤訊息。  
  
 您必須傳回值，來告知架構您的覆寫執行什麼動作。 傳回值-2 表示應用程式處理的選取項目所有層面，並不需要任何進一步的動作清單方塊。 之前傳回-2，您可以設定選取項目或移動插入號，或兩者。 若要設定選取項目，請使用[SetCurSel](#setcursel)或是[SetSel](#setsel)。 若要移動插入號，請使用[SetCaretIndex](#setcaretindex)。  
  
 傳回值為-1 表示清單方塊應該執行的預設動作，以回應按鍵輸入。預設實作會傳回-1。  
  
 大於或等於 0 的傳回值的清單方塊中指定的項目索引，並指出清單方塊應該執行的預設動作，在指定的項目上的按鍵輸入。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
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
