---
title: "CListBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListBox
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f4df970f2df35d399c0c700cf504a76482ad3f6d
ms.lasthandoff: 02/24/2017

---
# <a name="clistbox-class"></a>CListBox 類別
提供 Windows 清單方塊的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|建構 `CListBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|將字串加入至清單方塊。|  
|[CListBox::CharToItem](#chartoitem)|若要提供自訂的覆寫`WM_CHAR`主控描繪清單方塊中沒有字串處理。|  
|[CListBox::CompareItem](#compareitem)|由框架呼叫以判斷新項目的已排序的主控描繪清單方塊中的位置。|  
|[CListBox::Create](#create)|建立 Windows 清單方塊，並將它附加`CListBox`物件。|  
|[CListBox::DeleteItem](#deleteitem)|當使用者從主控描繪清單方塊中刪除項目時，由架構呼叫。|  
|[CListBox::DeleteString](#deletestring)|刪除清單方塊中的字串。|  
|[CListBox::Dir](#dir)|將清單方塊中的檔案名稱、 磁碟機，或同時從目前的目錄。|  
|[CListBox::DrawItem](#drawitem)|當主控描繪清單方塊中變更的視覺外觀的架構所呼叫。|  
|[CListBox::FindString](#findstring)|搜尋字串清單方塊中。|  
|[CListBox::FindStringExact](#findstringexact)|尋找符合指定的字串的第一個清單方塊字串。|  
|[CListBox::GetAnchorIndex](#getanchorindex)|擷取清單方塊中目前的錨點項目以零為起始的索引。|  
|[CListBox::GetCaretIndex](#getcaretindex)|判斷具有焦點矩形多重選擇清單方塊中的項目索引。|  
|[CListBox::GetCount](#getcount)|清單方塊中，傳回字串的數目。|  
|[CListBox::GetCurSel](#getcursel)|清單方塊中，傳回目前選取之字串的以零為起始的索引。|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|傳回清單方塊可以水平捲動的像素為單位的寬度。|  
|[CListBox::GetItemData](#getitemdata)|傳回與清單方塊項目相關聯的 32 位元值。|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|清單方塊項目中傳回的指標。|  
|[CListBox::GetItemHeight](#getitemheight)|決定清單方塊中的項目高度。|  
|[CListBox::GetItemRect](#getitemrect)|傳回目前顯示的清單方塊項目，這個周框。|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|擷取每個資料行的項目數。|  
|[CListBox::GetLocale](#getlocale)|擷取清單方塊的地區設定識別項。|  
|[CListBox::GetSel](#getsel)|傳回的清單方塊項目之選取狀態。|  
|[CListBox::GetSelCount](#getselcount)|傳回多重選擇清單方塊中目前選取的字串數目。|  
|[CListBox::GetSelItems](#getselitems)|傳回字串的清單方塊中目前選取的索引。|  
|[CListBox::GetText](#gettext)|將清單方塊項目複製到緩衝區。|  
|[CListBox::GetTextLen](#gettextlen)|傳回的長度，以位元組為單位的清單方塊項目。|  
|[CListBox::GetTopIndex](#gettopindex)|清單方塊中會傳回第一個可見的字串的索引。|  
|[CListBox::InitStorage](#initstorage)|清單方塊項目和字串的記憶體區塊的預先配置時。|  
|[CListBox::InsertString](#insertstring)|在清單方塊中指定位置插入的字串。|  
|[CListBox::ItemFromPoint](#itemfrompoint)|傳回最接近的點的清單方塊項目索引。|  
|[CListBox::MeasureItem](#measureitem)|建立主控描繪清單方塊來判斷清單方塊的維度時，由架構呼叫。|  
|[CListBox::ResetContent](#resetcontent)|清除所有項目從清單方塊。|  
|[CListBox::SelectString](#selectstring)|搜尋並選取單一選取清單方塊中的字串。|  
|[CListBox::SelItemRange](#selitemrange)|選取或取消選取範圍的多重選擇清單方塊中的字串。|  
|[CListBox::SetAnchorIndex](#setanchorindex)|設定在多重選擇清單方塊中，開始的延伸選取範圍的錨點。|  
|[CListBox::SetCaretIndex](#setcaretindex)|多重選擇清單方塊中指定索引處的項目設定焦點矩形。|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|設定資料行清單方塊的資料行寬度。|  
|[CListBox::SetCurSel](#setcursel)|選取清單方塊的字串。|  
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|設定清單方塊可以水平捲動的像素為單位的寬度。|  
|[CListBox::SetItemData](#setitemdata)|設定清單方塊項目相關聯的 32 位元值。|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|將指標設定為清單方塊項目。|  
|[CListBox::SetItemHeight](#setitemheight)|清單方塊中設定項目的高度。|  
|[CListBox::SetLocale](#setlocale)|設定清單方塊的地區設定識別碼。|  
|[CListBox::SetSel](#setsel)|選取或取消選取清單方塊項目在多重選擇清單方塊中。|  
|[CListBox::SetTabStops](#settabstops)|設定定位停駐點位置的清單方塊中。|  
|[CListBox::SetTopIndex](#settopindex)|清單方塊中設定第一個可見的字串以零起始的索引。|  
|[CListBox::VKeyToItem](#vkeytoitem)|若要提供自訂的覆寫`WM_KEYDOWN`清單方塊處理**LBS_WANTKEYBOARDINPUT**樣式集。|  
  
## <a name="remarks"></a>備註  
 清單方塊會顯示項目，例如檔案名稱，使用者可以檢視和選取的清單。  
  
 在單一選取清單方塊中，使用者可以選取一個項目。 在多重選擇清單方塊中，您可以選取的項目範圍。 當使用者選取項目時，它會反白顯示和清單方塊會傳送通知訊息給父視窗。  
  
 從對話方塊範本，或是直接在您的程式碼中，您可以建立清單方塊。 若要直接建立，建構`CListBox`物件，然後呼叫[建立](#create)成員函式來建立 Windows 清單方塊控制項，並將其附加至`CListBox`物件。 若要使用清單方塊的對話方塊範本中，清單方塊中宣告變數對話方塊類別，然後使用`DDX_Control`在您的對話方塊類別的`DoDataExchange`函式，來連接至控制項成員變數。 （這會為您自動完成您的對話方塊類別中加入的控制項變數時。）  
  
 建構可從衍生類別中的一蹴`CListBox`。 寫入的建構函式在衍生的類別並呼叫**建立**從建構函式內。  
  
 如果您想要處理 Windows 通知訊息傳送至其父代的清單方塊 (通常是一個類別衍生自[CDialog](../../mfc/reference/cdialog-class.md))，將訊息對應項目和訊息處理常式成員函式加入至每個訊息的父類別。  
  
 每個訊息對應項目都會使用下列格式︰  
  
 `ON_Notification( id, memberFxn )`  
  
 其中`id`指定傳送通知的清單方塊控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 父函式原型如下所示︰  
  
 `afx_msg void memberFxn( );`  
  
 下列是可能的訊息對應項目和描述的情況下以它們會傳送至父清單︰  
  
- **ON_LBN_DBLCLK**使用者按兩下清單方塊中的字串。 只有清單方塊具有[LBS_NOTIFY](../../mfc/reference/list-box-styles.md)樣式會傳送這個通知訊息。  
  
- **ON_LBN_ERRSPACE**清單方塊無法配置足夠的記憶體，以滿足要求。  
  
- **ON_LBN_KILLFOCUS**清單方塊失去輸入的焦點。  
  
- **ON_LBN_SELCANCEL**會取消目前的清單方塊選取。 清單方塊時，只會傳送此訊息**LBS_NOTIFY**樣式。  
  
- **ON_LBN_SELCHANGE**清單方塊中的選取範圍已變更。 如果選取範圍變更時，不會傳送這個通知[CListBox::SetCurSel](#setcursel)成員函式。 此通知只適用於清單方塊具有**LBS_NOTIFY**樣式。 **LBN_SELCHANGE**會傳送通知訊息的多重選擇清單方塊的使用者按下方向鍵，即使選取範圍不會變更。  
  
- **ON_LBN_SETFOCUS**清單方塊收到輸入的焦點。  
  
- **ON_WM_CHARTOITEM**已沒有字串為主控描繪清單方塊會收到`WM_CHAR`訊息。  
  
- **ON_WM_VKEYTOITEM**清單方塊**LBS_WANTKEYBOARDINPUT**樣式收到`WM_KEYDOWN`訊息。  
  
 如果您建立`CListBox`（透過對話方塊資源），對話方塊內的物件`CListBox`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CListBox`物件視窗中，您可能必須摧毀`CListBox`物件。 如果您建立`CListBox`物件在堆疊上，它會自動終結。 如果您建立`CListBox`使用堆積上的物件**新**函式，您必須呼叫**刪除**它終結，當使用者關閉的父視窗之物件。  
  
 如果您配置任何記憶體`CListBox`物件，覆寫`CListBox`解構函式配置的處置。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-nameaddstringa--clistboxaddstring"></a><a name="addstring"></a>CListBox::AddString  
 將字串加入至清單方塊。  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 `lpszItem`  
 要加入的 null 結尾字串的指標。  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的字串以零為起始的索引。 傳回值是**LB_ERR**若發生錯誤，則傳回值是**LB_ERRSPACE**如果空間不足以存放新的字串。  
  
### <a name="remarks"></a>備註  
 如果清單方塊不透過建立[LBS_SORT](../../mfc/reference/list-box-styles.md)樣式中，字串會新增至清單的結尾。 否則，將字串插入至清單，並排序清單。 如果使用清單方塊建立**LBS_SORT**樣式而非[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)樣式，架構會將清單排序藉由一或多個呼叫`CompareItem`成員函式。  
  
 使用[InsertString](#insertstring)將清單方塊中指定位置插入的字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&3;](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="a-namechartoitema--clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::CharToItem  
 當清單方塊的父視窗會收到由架構呼叫`WM_CHARTOITEM`從清單方塊的訊息。  
  
```  
virtual int CharToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nKey`  
 使用者輸入的字元 ANSI 程式碼。  
  
 `nIndex`  
 目前的清單方塊插入號位置。  
  
### <a name="return-value"></a>傳回值  
 傳回 – 1 或-2，任何進一步的動作或非負數的數字，以指定要執行預設動作按鍵清單方塊項目的索引。 預設實作會傳回 – 1。  
  
### <a name="remarks"></a>備註  
 `WM_CHARTOITEM`收到時，訊息由清單方塊傳送`WM_CHAR`訊息，但只看清單方塊是否符合所有的準則︰  
  
-   為主控描繪清單方塊。  
  
-   沒有[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)樣式集。  
  
-   有一個以上的項目。  
  
 您絕不應該自行呼叫此函式。 覆寫此函式可提供您自己的自訂處理鍵盤訊息。  
  
 在您覆寫時，您必須傳回要告訴您執行什麼動作架構的值。 傳回值為-1 或-2 表示您處理所有層面的選取項目，並不需要進一步動作的清單方塊。 再傳回 – 1 或-2，您無法設定選取項目或移動插入號，或兩者。 若要設定選取範圍，請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要將插入號，使用[SetCaretIndex](#setcaretindex)。  
  
 等於或大於 0 的傳回值的清單方塊中指定項目的索引，並指出清單方塊應該執行給定的項目上的按鍵動作的預設動作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&4;](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="a-nameclistboxa--clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox  
 建構 `CListBox` 物件。  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>備註  
 您建構`CListBox`兩個步驟中的物件。 首先，呼叫建構函式**ClistBox** ，然後呼叫**建立**，這會初始化 Windows 清單方塊，並將其以附加`CListBox`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&1;](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="a-namecompareitema--clistboxcompareitem"></a><a name="compareitem"></a>CListBox::CompareItem  
 由框架呼叫以判斷新的項目已排序的主控描繪清單方塊中的相對位置。  
  
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
|–1|項目 1 排序項目 2 之前。|  
|0|項目 1 和 2 的項目排序相同。|  
|1|項目 1 排序項目 2 之後。|  
  
 請參閱[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)的說明`COMPAREITEMSTRUCT`結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有作用。 如果您建立主控描繪清單方塊**LBS_SORT**樣式，您必須覆寫此成員函式，以協助架構排序的清單方塊中加入新項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&5;](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="a-namecreatea--clistboxcreate"></a><a name="create"></a>CListBox::Create  
 建立 Windows 清單方塊，並將它附加`CListBox`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定清單方塊的樣式。 套用的任何結合[清單方塊樣式](../../mfc/reference/list-box-styles.md)至方塊。  
  
 `rect`  
 指定清單方塊的大小和位置。 可以是`CRect`物件或`RECT`結構。  
  
 `pParentWnd`  
 指定清單方塊的父視窗 (通常是`CDialog`物件)。 它不得為**NULL**。  
  
 `nID`  
 指定清單方塊控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CListBox`兩個步驟中的物件。 首先，呼叫建構函式，接著呼叫**建立**，這會初始化 Windows 清單方塊，並將其以附加`CListBox`物件。  
  
 當**建立**執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)訊息至清單方塊控制項。  
  
 根據預設，處理這些訊息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式中`CWnd`基底類別。 若要擴充的預設訊息處理，衍生自`CListBox`、 將訊息對應新增至新的類別，並覆寫先前的訊息處理常式成員函式。 覆寫`OnCreate`，例如，執行所需的初始化新的類別。  
  
 適用於下列[視窗樣式](../../mfc/reference/window-styles.md)至清單方塊控制項。  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**新增垂直捲軸  
  
- **WS_HSCROLL**新增水平捲軸  
  
- **WS_GROUP**控制項群組  
  
- **WS_TABSTOP**允許這個控制項的定位停駐  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&2;](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="a-namedeleteitema--clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem  
 當使用者從主控描繪刪除項目時，由框架呼叫`CListBox`物件或終結清單方塊。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDeleteItemStruct`  
 Windows 的長指標[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)結構，其中包含已刪除項目的相關資訊。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫這個函式來重繪視主控描繪清單方塊。  
  
 請參閱[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)的說明`DELETEITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&6;](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="a-namedeletestringa--clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString  
 刪除項目位置`nIndex`從清單方塊。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要刪除之字串的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 在清單中的剩餘字串的計數。 傳回值是**LB_ERR**如果`nIndex`指定索引的項目數大於清單中。  
  
### <a name="remarks"></a>備註  
 之後的所有項目`nIndex`現在下移一個位置。 例如，如果清單方塊包含兩個項目，刪除第一個項目會導致其餘的項目現在是在第一個位置。 `nIndex`=&0;，第一個位置中的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&7;](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="a-namedira--clistboxdir"></a><a name="dir"></a>CListBox::Dir  
 將檔名、 磁碟機，或兩者的清單方塊的清單。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>參數  
 `attr`  
 可以是任何組合的`enum`值中所述**CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus)，或下列值的任何組合︰  
  
|值|意義|  
|-----------|-------------|  
|0x0000|可讀取或寫入檔案。|  
|0x0001|可以讀取但不是會寫入檔案。|  
|0x0002|檔案被隱藏，並且不會出現在目錄清單。|  
|0x0004|檔案是系統檔案。|  
|0x0010|所指定的名稱`lpszWildCard`指定的目錄。|  
|0x0020|已封存檔案。|  
|0x4000|包含符合指定之名稱的所有磁碟機`lpszWildCard`。|  
|0x8000|獨佔的旗標。 如果獨佔的旗標設定時，會列出檔案指定的型別。 否則，會列出指定之型別的的檔案，除了 「 正常 」 的檔案。|  
  
 `lpszWildCard`  
 指向檔案規格字串。 字串可以包含萬用字元 (例如，*。\*)。  
  
### <a name="return-value"></a>傳回值  
 加入至清單的最後一個檔名的以零起始的索引。 傳回值是**LB_ERR**若發生錯誤，則傳回值是**LB_ERRSPACE**如果空間不足以存放新的字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&8;](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="a-namedrawitema--clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem  
 當主控描繪清單方塊中變更的視覺外觀的架構所呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 長指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**和**itemState**成員`DRAWITEMSTRUCT`結構定義繪圖要執行的動作。  
  
 根據預設，此成員函式沒有作用。 覆寫此成員函式實作繪圖的主控描繪`CListBox`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前此成員函式會結束。  
  
 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)的說明`DRAWITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&9;](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="a-namefindstringa--clistboxfindstring"></a><a name="findstring"></a>CListBox::FindString  
 尋找第一個字串，而不需要變更清單方塊選取項目包含指定的前置詞的清單方塊中。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當到達清單方塊的底部時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 如果`nStartAfter`為 –&1;，從一開始便會搜尋整個清單方塊。  
  
 `lpszItem`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可能會包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 比對項目的以零起始的索引或**LB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 使用[SelectString](#selectstring)成員函式來尋找和選取字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&10;](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="a-namefindstringexacta--clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact  
 尋找符合指定之字串的第一個清單方塊字串`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndexStart`  
 指定要搜尋的第一個項目之前的項目以零為起始的索引。 當到達清單方塊的底部時，它會繼續從清單方塊的上方回所指定的項目`nIndexStart`。 如果`nIndexStart`為 –&1;，從一開始便會搜尋整個清單方塊。  
  
 `lpszFind`  
 指向以 null 結束的字串搜尋。 這個字串可以包含完整的檔名，包括副檔名。 搜尋不區分大小寫，因此該字串可以包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 相符的項目索引或**LB_ERR**如果搜尋失敗。  
  
### <a name="remarks"></a>備註  
 如果清單方塊透過建立主控描繪樣式但不含[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)樣式，`FindStringExact`成員函式會嘗試比對的值的 doubleword 值`lpszFind`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&11;](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="a-namegetanchorindexa--clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex  
 擷取目前的清單方塊中的錨點項目以零為起始索引。  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 項目的索引目前錨點，如果登錄成功。否則**LB_ERR**。  
  
### <a name="remarks"></a>備註  
 在多重選擇清單方塊中，錨點的項目是連續的選取項目的區塊中的第一個或最後一個項目。  
  
### <a name="example"></a>範例  
  請參閱範例[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="a-namegetcaretindexa--clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex  
 判斷具有焦點矩形多重選擇清單方塊中的項目索引。  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊具有焦點矩形的項目以零為起始的索引。 如果單一選取清單方塊的清單方塊，如果有任何傳回值為已選取項目的索引。  
  
### <a name="remarks"></a>備註  
 這個項目可能會或可能未選取。  
  
### <a name="example"></a>範例  
  請參閱範例[CListBox::SetCaretIndex](#setcaretindex)。  
  
##  <a name="a-namegetcounta--clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount  
 擷取清單方塊中的項目數。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中的項目數或**LB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 傳回的計數會比索引值 （索引以零為起始） 的最後一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&12;](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="a-namegetcursela--clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel  
 如果有的話，在單一選取清單方塊中會擷取目前選取項目的以零起始的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果它是單一選取清單方塊目前選取項目以零為起始的索引。 它是`LB_ERR`如果目前不選取任何項目。  
  
 在多重選擇清單方塊中，具有焦點之項目的索引。  
  
### <a name="remarks"></a>備註  
 請勿呼叫`GetCurSel`多重選擇清單方塊。 使用[CListBox::GetSelItems](#getselitems)改。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&13;](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="a-namegethorizontalextenta--clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent  
 擷取清單方塊中，它可以水平捲動的像素為單位的寬度。  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中，單位為像素可捲動的寬度。  
  
### <a name="remarks"></a>備註  
 這是清單方塊具有水平捲軸時，才適用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&14;](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="a-namegetitemdataa--clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData  
 擷取與指定的清單方塊項目相關聯的應用程式提供 doubleword 值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 清單方塊中指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 對項目相關聯的 32 位元值或**LB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 Doubleword 值為`dwItemData`參數[SetItemData](#setitemdata)呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&15;](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="a-namegetitemdataptra--clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr  
 擷取與指定的清單方塊項目做為指標的應用程式提供 32 位元值 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 清單方塊中指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 擷取是指標，則為 –&1;，如果發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&16;](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="a-namegetitemheighta--clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight  
 決定清單方塊中的項目高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 清單方塊中指定項目的以零為起始的索引。 使用這個參數只有當清單方塊中含有**LBS_OWNERDRAWVARIABLE**樣式; 否則它應該設定為 0。  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素的清單方塊中的項目。 如果清單方塊中含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)樣式，則傳回值是指定之項目的高度`nIndex`。 如果發生錯誤時，傳回的值是**LB_ERR**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&17;](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="a-namegetitemrecta--clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect  
 擷取矩形的維度繫結清單方塊項目目前顯示在清單方塊視窗中。  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
 `lpRect`  
 指定的長指標[RECT 結構](../../mfc/reference/rect-structure1.md)接收之項目的清單方塊用戶端座標。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&18;](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="a-namegetlistboxinfoa--clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo  
 擷取每個資料行的項目數。  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 每個資料行的項目數`CListBox`物件。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetlocalea--clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale  
 擷取清單方塊所使用的地區設定。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的字串，地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 會使用地區設定，例如，以判斷字串的已排序的清單方塊中的排序順序。  
  
### <a name="example"></a>範例  
  請參閱範例[CListBox::SetLocale](#setlocale)。  
  
##  <a name="a-namegetsela--clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel  
 擷取項目的選取狀態。  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 選取指定的項目; 如果是正數否則，它會是 0。 傳回值是`LB_ERR`發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式搭配兩個單一和多重選擇清單方塊。  
  
 若要擷取目前選取的清單方塊項目的索引，請使用[CListBox::GetCurSel](#getcursel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&19;](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="a-namegetselcounta--clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount  
 擷取多重選擇清單方塊中選取的項目的總數。  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中選取項目的計數。 如果單一選取清單方塊的清單方塊，則傳回值是**LB_ERR**。  
  
### <a name="example"></a>範例  
  請參閱範例[CListBox::GetSelItems](#getselitems)。  
  
##  <a name="a-namegetselitemsa--clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems  
 指定多重選擇清單方塊中的選取項目的項目編號的整數陣列中填入緩衝區。  
  
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
 項目實際數目會放在緩衝區中。 如果單一選取清單方塊的清單方塊，則傳回值是`LB_ERR`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&20;](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="a-namegettexta--clistboxgettext"></a><a name="gettext"></a>CListBox::GetText  
 取得字串，請從清單方塊。  
  
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
 指向接收字串的緩衝區。 緩衝區必須有足夠的空間，如字串和結束的 null 字元。 可以事先判斷字串的大小，藉由呼叫`GetTextLen`成員函式。  
  
 `rString`  
 對 `CString` 物件的參考。  
  
### <a name="return-value"></a>傳回值  
 字串，但不包含結束的 null 字元的長度 （以位元組為單位）。 如果`nIndex`未指定有效的索引，則傳回值是**LB_ERR**。  
  
### <a name="remarks"></a>備註  
 這個成員的第二個形式函式的填滿`CString`具有字串文字物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&21;](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="a-namegettextlena--clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen  
 取得字串的長度，在清單方塊項目。  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定字串之以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 以字元為單位，但不包含結束的 null 字元字串的長度。 如果`nIndex`未指定有效的索引，則傳回值是**LB_ERR**。  
  
### <a name="example"></a>範例  
  請參閱範例[CListBox::GetText](#gettext)。  
  
##  <a name="a-namegettopindexa--clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GetTopIndex  
 擷取清單方塊中第一個可見項目的以零為起始的索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，清單方塊中的第一個可見項目以零為起始索引**LB_ERR**否則。  
  
### <a name="remarks"></a>備註  
 一開始，項目 0 頂端的清單方塊中，但是如果捲動清單方塊中，另一個項目一定在頂端。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&22;](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="a-nameinitstoragea--clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage  
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
 指定的記憶體數量，以位元組為單位，以配置所需項目的字串。  
  
### <a name="return-value"></a>傳回值  
 如果成功，最大數目的項目之前需要的記憶體配置，否則，清單方塊可以存放**LB_ERRSPACE**，這表示沒有足夠的記憶體可用。  
  
### <a name="remarks"></a>備註  
 新增大量的項目之前呼叫此函式`CListBox`。  
  
 此函式可協助您加速有大量的項目 (超過 100) 的清單方塊的初始化。 它使用預先配置時讓後續的記憶體數量指定[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函式接受的最短的時間。 您可以使用估計值的參數。 如果增長時，會配置一些額外的記憶體。如果您低估，一般配置使用超過預先配置的項目。  
  
 只有 Windows 95/98:`nItems`參數是限制為 16 位元值。 這表示清單方塊不能包含超過 32767 個項目。 雖然受限制的項目數，清單方塊中的項目中的總大小只受限於可用的記憶體。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&23;](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="a-nameinsertstringa--clistboxinsertstring"></a><a name="insertstring"></a>CListBox::InsertString  
 將字串插入至清單方塊。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要插入字串的位置以零為起始索引。 如果這個參數為 –1，字串就加入到清單的結尾。  
  
 `lpszItem`  
 指向要插入的 null 結尾字串。  
  
### <a name="return-value"></a>傳回值  
 已插入字串之位置以零為基底的索引。 傳回值是**LB_ERR**若發生錯誤，則傳回值是**LB_ERRSPACE**如果空間不足以存放新的字串。  
  
### <a name="remarks"></a>備註  
 不同於[AddString](#addstring)成員函式，`InsertString`並不會與清單[LBS_SORT](../../mfc/reference/list-box-styles.md)排序樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&24;](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="a-nameitemfrompointa--clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemFromPoint  
 決定最接近指定點的清單方塊項目`pt`。  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 是用來尋找最接近的項目，指定相對於清單方塊的工作區的左上角的點。  
  
 `bOutside`  
 參考`BOOL`變數會設定為`TRUE`如果`pt`超出最接近的清單方塊項目的工作區`FALSE`如果`pt`在用戶端區域的最接近的清單方塊項目內。  
  
### <a name="return-value"></a>傳回值  
 最接近的項目中指定的點索引`pt`。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來判斷哪一個滑鼠游標移的清單方塊項目。  
  
### <a name="example"></a>範例  
  請參閱範例[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="a-namemeasureitema--clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem  
 建立具有主控描繪樣式的清單方塊時，由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpMeasureItemStruct`  
 長指標[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有作用。 覆寫此成員函式，並填入`MEASUREITEMSTRUCT`通知 Windows 清單方塊維度的結構。 如果以建立清單方塊[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)樣式，架構會呼叫此成員函式的清單方塊中的每個項目。 否則，這個成員是只呼叫一次。  
  
 如需進一步使用[LBS_OWNERDRAWFIXED](../../mfc/reference/list-box-styles.md)建立主控描繪清單方塊中的樣式`SubclassDlgItem`成員函式`CWnd`，請參閱[技術附註 14](../../mfc/tn014-custom-controls.md)。  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構**。**  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&25;](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="a-nameresetcontenta--clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent  
 從清單方塊中移除所有項目。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&26;](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="a-nameselectstringa--clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString  
 搜尋符合指定的字串中，清單方塊項目和如果找到相符的項目，它會選取項目。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 `nStartAfter`  
 包含要搜尋的第一個項目之前的項目以零為起始的索引。 當到達清單方塊的底部時，它會繼續從清單方塊的上方回所指定的項目`nStartAfter`。 如果`nStartAfter`為 –&1;，從一開始便會搜尋整個清單方塊。  
  
 `lpszItem`  
 指向以 null 結束的字串，其中包含要搜尋的前置詞。 搜尋是大小寫無關，因此這個字串可能會包含任何大寫和小寫字母。  
  
### <a name="return-value"></a>傳回值  
 如果搜尋成功，所選取項目的索引。 如果搜尋成功，則傳回值是**LB_ERR**且不會變更目前的選取範圍。  
  
### <a name="remarks"></a>備註  
 捲動清單方塊，如有必要，將選取的項目帶入檢視。  
  
 此成員函式不能與清單方塊具有[LBS_MULTIPLESEL](../../mfc/reference/list-box-styles.md)樣式。  
  
 只有當其起始的字元 （從起點） 符合所指定的字串中的字元，選取項目`lpszItem`。  
  
 使用`FindString`成員函式來尋找字串，而不需選取項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&27;](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="a-nameselitemrangea--clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange  
 多重選擇清單方塊中選取多個連續的項目。  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>參數  
 `bSelect`  
 指定如何將選項設定。 如果`bSelect`是**TRUE**，即選取字串，並將其反白顯示; 如果**FALSE**，移除反白顯示的字串不再被選取。  
  
 `nFirstItem`  
 指定要設定的第一個項目以零為起始的索引。  
  
 `nLastItem`  
 指定要設定的最後一個項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式只適用於多重選擇清單方塊中。 如果您需要多重選擇清單方塊中選取一個項目 — 也就是如果`nFirstItem`等於`nLastItem`— 呼叫[SetSel](#setsel)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&28;](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="a-namesetanchorindexa--clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex  
 設定在多重選擇清單方塊中，開始的延伸選取範圍的錨點。  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定會錨點的清單方塊項目以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 在多重選擇清單方塊中，錨點的項目是連續的選取項目的區塊中的第一個或最後一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&29;](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="a-namesetcaretindexa--clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex  
 多重選擇清單方塊中指定索引處的項目設定焦點矩形。  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定要接收焦點矩形的清單方塊中的項目以零為起始的索引。  
  
 *bScroll*  
 如果此值為 0，此項目會捲動，直到可以完全看見。 如果此值不是 0，此項目捲動直到至少部分顯示。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 如果看不到項目，它會捲動到檢視。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&30;](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="a-namesetcolumnwidtha--clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth  
 多重資料行的清單方塊中，像素為單位的所有資料行設定寬度 (以建立[LBS_MULTICOLUMN](../../mfc/reference/list-box-styles.md)樣式)。  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>參數  
 `cxWidth`  
 指定像素為單位的所有資料行的寬度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&31;](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="a-namesetcursela--clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel  
 選取字串，並捲動到檢視，如有必要。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>參數  
 `nSelect`  
 指定要選取之字串的以零為起始的索引。 如果`nSelect`為 –&1;，清單方塊設定為已選取範圍。  
  
### <a name="return-value"></a>傳回值  
 `LB_ERR`如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 選取新的字串時，清單方塊會移除先前選取的字串中的反白顯示。  
  
 此成員函式只適用於單一選取清單方塊中。  
  
 若要設定或移除多重選擇清單方塊中選擇，請使用[CListBox::SetSel](#setsel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&32;](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="a-namesethorizontalextenta--clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent  
 設定寬度，單位為像素的清單方塊可以水平捲動。  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>參數  
 *cxExtent*  
 指定的清單方塊可以水平捲動的像素數目。  
  
### <a name="remarks"></a>備註  
 如果清單方塊的大小比這個值，水平捲軸的水平捲動清單方塊中的項目。 如果清單方塊會比此值較大，則會隱藏水平捲軸。  
  
 若要回應呼叫`SetHorizontalExtent`，清單方塊必須已定義與[WS_HSCROLL](../../mfc/reference/window-styles.md)樣式。  
  
 此成員函式不適用於多個資料行的清單方塊中。 多重資料行的清單方塊中，呼叫`SetColumnWidth`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&33;](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="a-namesetitemdataa--clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData  
 設定清單方塊中指定的項目相關聯的 32 位元值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
 `dwItemData`  
 指定要與項目相關聯的值。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&34;](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="a-namesetitemdataptra--clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr  
 設定為指定的指標的清單方塊中指定的項目相關聯的 32 位元值 ( **void\***)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定項目的以零為起始的索引。  
  
 `pData`  
 指定要與項目相關聯的指標。  
  
### <a name="return-value"></a>傳回值  
 **LB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 此指標都是有效的生命週期的清單方塊中，即使新增或移除項目時，可能會變更的項目在清單方塊內的相對位置。 因此，可以變更方塊內項目的索引，但是，指標都是可靠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&35;](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="a-namesetitemheighta--clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight  
 清單方塊中設定項目的高度。  
  
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
 **LB_ERR**索引或高度是否無效。  
  
### <a name="remarks"></a>備註  
 如果清單方塊中含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)樣式，此函式會將指定之項目的高度`nIndex`。 否則，此函式將清單方塊中設定所有項目的高度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&36;](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="a-namesetlocalea--clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale  
 設定此清單方塊的地區設定識別碼。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>參數  
 `nNewLocale`  
 要設定的清單方塊的新地區設定識別碼 (LCID) 值。  
  
### <a name="return-value"></a>傳回值  
 此清單方塊中先前的地區設定識別碼 (LCID) 值。  
  
### <a name="remarks"></a>備註  
 如果**SetLocale** ，不會呼叫預設的地區設定從系統取得。 可以修改此系統預設地區設定使用控制台中的地區 （或國際） 應用程式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&37;](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="a-namesetsela--clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel  
 多重選擇清單方塊中選取字串。  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含要設定之字串的以零為起始的索引。 如果 –&1;，則選取範圍加入或移除的值而定的所有字串`bSelect`。  
  
 `bSelect`  
 指定如何將選項設定。 如果`bSelect`是`TRUE`，即選取字串，並將其反白顯示; 如果`FALSE`，移除反白顯示的字串不再被選取。 指定的字串被選取，而且預設反白顯示。  
  
### <a name="return-value"></a>傳回值  
 `LB_ERR`如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 此成員函式只適用於多重選擇清單方塊中。  
  
 若要從單一選取清單方塊選取項目，使用[CListBox::SetCurSel](#setcursel)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&38;](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="a-namesettabstopsa--clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabStops  
 設定定位停駐點位置的清單方塊中。  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>參數  
 `cxEachStop`  
 設定定位停駐點在每個`cxEachStop`對話方塊單位。 請參閱*rgTabStops*對話方塊單位的說明。  
  
 `nTabStops`  
 指定清單方塊中的定位停駐點的數目。  
  
 `rgTabStops`  
 包含以對話方塊單位的定位停駐點位置的整數的陣列的第一個成員指標。 對話方塊單位是水平或垂直距離。 一個水平對話方塊單位等於目前對話方塊基底寬度單位的四分之一，和一個垂直對話方塊單位等於目前對話方塊基底高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 **GetDialogBaseUnits** Windows 函式會傳回目前對話方塊基底單位像素為單位。 必須以遞增順序排序定位停駐點不允許回復 索引標籤。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已設定的所有索引標籤。否則為 0。  
  
### <a name="remarks"></a>備註  
 若要設定定位停駐點的預設大小的 2 個對話方塊單位，呼叫此成員函式的無參數的版本。 若要設定定位停駐點到 2 以外的大小，呼叫與版本`cxEachStop`引數。  
  
 若要設定定位停駐點大小的陣列，使用的版本與`rgTabStops`和`nTabStops`引數。 定位停駐點將每個值`rgTabStops`，最多指定的數字`nTabStops`。  
  
 若要回應呼叫`SetTabStops`成員函式，清單方塊，必須已建立[LBS_USETABSTOPS](../../mfc/reference/list-box-styles.md)樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&39;](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="a-namesettopindexa--clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SetTopIndex  
 請確定特定的清單方塊項目會出現。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定清單方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，零或**LB_ERR**發生錯誤。  
  
### <a name="remarks"></a>備註  
 系統會將清單方塊捲動直到其中一個所指定的項目`nIndex`會出現在清單頂端或最大的捲軸範圍已達到。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&40;](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="a-namevkeytoitema--clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem  
 當清單方塊的父視窗會收到由架構呼叫`WM_VKEYTOITEM`從清單方塊的訊息。  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nKey`  
 索引鍵的虛擬程式碼使用者按下。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.  
  
 `nIndex`  
 目前的清單方塊插入號位置。  
  
### <a name="return-value"></a>傳回值  
 傳回 – 2 沒有進一步的動作、 – 1 的預設動作或指定要執行預設動作按鍵清單方塊項目的索引為非負數值。  
  
### <a name="remarks"></a>備註  
 `WM_VKEYTOITEM`收到時，訊息由清單方塊傳送`WM_KEYDOWN`訊息，但只看清單方塊是否符合下列兩個︰  
  
-   具有[LBS_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md)樣式集。  
  
-   有一個以上的項目。  
  
 您絕不應該自行呼叫此函式。 覆寫此函式可提供您自己的自訂處理鍵盤訊息。  
  
 您必須傳回要告訴架構您的覆寫動作的值。 傳回值為-2 表示應用程式處理所有層面的選取項目，並不需要進一步動作的清單方塊。 之前傳回-2，您無法設定選取項目或移動插入號，或兩者。 若要設定選取範圍，請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要將插入號，使用[SetCaretIndex](#setcaretindex)。  
  
 傳回值為-1 表示清單方塊應該執行的預設動作，以回應按鍵。預設實作會傳回 – 1。  
  
 等於或大於 0 的傳回值的清單方塊中指定項目的索引，並指出清單方塊應該執行給定的項目上的按鍵動作的預設動作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CListBox #&41;](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
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

