---
title: "CHeaderCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class
- Windows common controls [C++], CHeaderCtrl
- header controls, CHeaderCtrl class
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
caps.latest.revision: 24
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: faa23ea6f28c2643c9bee090ea150e37d0add97c
ms.lasthandoff: 04/01/2017

---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 類別
提供 Windows 通用標頭控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CHeaderCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|建構 `CHeaderCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|清除所有標頭控制項的篩選。|  
|[CHeaderCtrl::ClearFilter](#clearfilter)|清除標頭控制項的篩選。|  
|[CHeaderCtrl::Create](#create)|建立標題控制項，並將它附加至`CHeaderCtrl`物件。|  
|[Cheaderctrl:: Createdragimage](#createdragimage)|建立標題控制項中的項目影像的透明版本。|  
|[CHeaderCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立標題控制項，並將它附加至`CListCtrl`物件。|  
|[CHeaderCtrl::DeleteItem](#deleteitem)|刪除標題控制項中的項目。|  
|[CHeaderCtrl::DrawItem](#drawitem)|繪製標題控制項的指定項目。|  
|[CHeaderCtrl::EditFilter](#editfilter)|開始編輯指定的篩選條件，標題控制項。|  
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|擷取控制項中的點陣圖邊界的寬度。|  
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|取得目前具有焦點的標題控制項中的項目的識別碼。|  
|[CHeaderCtrl::GetImageList](#getimagelist)|擷取影像清單控制項中的繪圖標頭項目所使用的控制代碼。|  
|[Cheaderctrl:: Getitem](#getitem)|擷取控制項中項目的資訊。|  
|[CHeaderCtrl::GetItemCount](#getitemcount)|擷取控制項中的項目計數。|  
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|標題控制項中取得指定的下拉式按鈕的週框矩形資訊。|  
|[CHeaderCtrl::GetItemRect](#getitemrect)|擷取控制項中的指定項目的週框。|  
|[Cheaderctrl:: Getorderarray](#getorderarray)|擷取由左到右的順序標題控制項中的項目。|  
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|取得目前的標頭控制溢位按鈕的週框矩形。|  
|[CHeaderCtrl::HitTest](#hittest)|決定哪一個標頭項目，如果有的話，位於指定點。|  
|[Cheaderctrl:: Insertitem](#insertitem)|標題控制項中插入新項目。|  
|[CHeaderCtrl::Layout](#layout)|擷取給定矩形內的標頭控制項的位置與大小。|  
|[Cheaderctrl:: Ordertoindex](#ordertoindex)|擷取的項目，其標題控制項中的順序為基礎的索引值。|  
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|標題控制項中設定點陣圖的邊界的寬度。|  
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|設定逾時之間的間隔時間變更發生在篩選條件屬性，且公佈`HDN_FILTERCHANGE`通知。|  
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|將焦點設定至目前的標題控制項中指定的標頭項目。|  
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|變更標頭項目，以表示手動之間的分隔線拖曳和卸除的標頭項目。|  
|[CHeaderCtrl::SetImageList](#setimagelist)|指派至標題控制項的影像清單。|  
|[Cheaderctrl:: Setitem](#setitem)|標題控制項中，設定指定之項目的屬性。|  
|[Cheaderctrl:: Setorderarray](#setorderarray)|設定由左到右的順序的項目控制項中。|  
  
## <a name="remarks"></a>備註  
 標題控制項是一個視窗，通常位於上述一組文字或數字的資料行。 它包含每個欄位的標題，它可以分割成組件。 使用者可以拖曳分隔組件來設定每個資料行寬度的分隔線。 如需標題控制項的圖例，請參閱[標題控制項](http://msdn.microsoft.com/library/windows/desktop/bb775238)。  
  
 這個控制項 (因此`CHeaderCtrl`類別) 僅適用於執行 Windows 95/98、 Windows NT 的版本 3.51 下的程式和更新版本。  
  
 加入 Windows 95/Internet Explorer 4.0 通用控制項的功能包括下列各項︰  
  
-   標頭項目自訂的順序。  
  
-   標頭項目拖放，重新排序的標頭項目。 使用`HDS_DRAGDROP`樣式，當您建立`CHeaderCtrl`物件。  
  
-   標頭資料行文字資料行調整大小期間持續可檢視。 使用`HDS_FULLDRAG`樣式，當您建立`CHeaderCtrl`物件。  
  
-   標頭熱追蹤，它會反白顯示標頭項目，當滑鼠指標停留它。 使用`HDS_HOTTRACK`樣式，當您建立`CHeaderCtrl`物件。  
  
-   影像清單的支援。 標頭項目可以包含儲存在映像`CImageList`物件或文字。  
  
 如需有關使用`CHeaderCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl  
 建構 `CHeaderCtrl` 物件。  
  
```  
CHeaderCtrl();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]  
  
##  <a name="clearallfilters"></a>CHeaderCtrl::ClearAllFilters  
 清除所有標頭控制項的篩選。  
  
```  
BOOL ClearAllFilters();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會實作的 Win32 訊息行為[HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306)資料行值為-1 中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]  
  
##  <a name="clearfilter"></a>CHeaderCtrl::ClearFilter  
 清除標頭控制項的篩選。  
  
```  
BOOL ClearFilter(int nColumn);
```  
  
### <a name="parameters"></a>參數  
 `nColumn`  
 資料行值，指出其清除篩選。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會實作的 Win32 訊息行為[HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]  
  
##  <a name="create"></a>CHeaderCtrl::Create  
 建立標題控制項，並將它附加至`CHeaderCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定標頭控制項的樣式。 如需標頭控制項樣式的說明，請參閱[標頭控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775241)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定標頭控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 指定標頭控制項的父視窗，通常`CDialog`。 它不得為**NULL**。  
  
 `nID`  
 指定標頭控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功，則為非零否則為零。  
  
### <a name="remarks"></a>備註  
 您建構`CHeaderCtrl`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫**建立**，建立標題控制項，並將它附加至`CHeaderCtrl`物件。  
  
 除了標頭控制項樣式中，您可以使用下列常見的控制項樣式判斷標題控制項的定位方式，並調整其大小 (請參閱[通用控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775498)如需詳細資訊):  
  
- `CCS_BOTTOM`使控制項決定本身的父視窗工作區底部的位置，並設定要做為父系相同寬度視窗的寬度。  
  
- `CCS_NODIVIDER`防止繪製控制項的頂端的兩個像素反白顯示。  
  
- `CCS_NOMOVEY`導致控制項調整大小並移動本身水平的但未以垂直方式，以回應`WM_SIZE`訊息。 如果`CCS_NORESIZE`樣式時，不會套用此樣式。 根據預設，標題控制項具有此樣式。  
  
- `CCS_NOPARENTALIGN`防止控制項的上方或底部的父視窗會自動移動。 相反地，控制項會保留它的位置，無論有何變更父視窗內的父視窗大小。 如果`CCS_TOP`或`CCS_BOTTOM`也會使用樣式、 高度會調整為預設值，但寬度與位置維持不變。  
  
- `CCS_NORESIZE`控制項可防止使用的預設寬度和高度，當設定初始大小或新的大小。 相反地，此控制項會使用建立或調整大小要求中指定的高度與寬度。  
  
- `CCS_TOP`使控制項決定本身在父視窗工作區頂端的位置，並設定要做為父系相同寬度視窗的寬度。  
  
 您也可以套用下列視窗樣式至標題控制項 (請參閱[視窗樣式](../../mfc/reference/window-styles.md)如需詳細資訊):  
  
- **WS_CHILD**建立子視窗。 不能與`WS_POPUP`樣式。  
  
- **WS_VISIBLE**建立一開始即可見的視窗。  
  
- **WS_DISABLED**建立視窗一開始停用。  
  
- **WS_GROUP**指定一組控制項所在使用者可以移動一個控制項到下一步 箭號索引鍵的第一個控制項。 所有控制項，以定義**WS_GROUP**樣式之後的第一個控制項必須屬於相同的群組。 下一個控制項與**WS_GROUP**樣式結束樣式的群組，並啟動下一個群組 （也就是說，一個群組結束開始下）。  
  
- **WS_TABSTOP**透過這些使用者可以使用 TAB 鍵移動的控制項的指定任意數目的其中一個。 TAB 鍵移至所指定的下一個控制項的使用者**WS_TABSTOP**樣式。  
  
 如果您想要搭配控制項使用延伸的視窗樣式，呼叫[CreateEx](#createex)而不是**建立**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]  
  
##  <a name="createex"></a>CHeaderCtrl::CreateEx  
 建立的控制項 （子視窗），並與`CHeaderCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸的視窗樣式的清單，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 標題控制項的樣式。 如需標頭控制項樣式的說明，請參閱[標頭控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775241)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 請參閱[建立](#create)其他樣式的清單。  
  
 `rect`  
 若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立，用戶端座標中之視窗`pParentWnd`。  
  
 `pParentWnd`  
 為控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是**建立**套用延伸的視窗樣式，由 Windows 擴充的樣式序言**WS_EX_**。  
  
##  <a name="createdragimage"></a>Cheaderctrl:: Createdragimage  
 建立標題控制項中的項目影像的透明版本。  
  
```  
CImageList* CreateDragImage(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 標題控制項內的項目以零為起始的索引。 指派給此項目影像是透明的映像的基礎。  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，如果成功，否則**NULL**。 傳回的清單包含只有一個映像。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_CREATEDRAGIMAGE](http://msdn.microsoft.com/library/windows/desktop/bb775308)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它被提供來支援標頭項目拖曳和卸除。  
  
 `CImageList`的傳回的指標指向是暫存物件，而且會在下次閒置時間處理刪除的物件。  
  
##  <a name="deleteitem"></a>CHeaderCtrl::DeleteItem  
 刪除標題控制項中的項目。  
  
```  
BOOL DeleteItem(int nPos);
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 指定要刪除的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]  
  
##  <a name="drawitem"></a>CHeaderCtrl::DrawItem  
 當主控描繪標題控制項變更的視覺外觀時，架構呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 指標[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)結構，描述要繪製的項目。  
  
### <a name="remarks"></a>備註  
 **ItemAction**隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。  
  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作主控描繪的繪圖`CHeaderCtrl`物件。  
  
 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前此成員函式會結束。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]  
  
##  <a name="editfilter"></a>CHeaderCtrl::EditFilter  
 開始編輯指定的篩選條件，標題控制項。  
  
```  
BOOL EditFilter(
    int nColumn,  
    BOOL bDiscardChanges);
```  
  
### <a name="parameters"></a>參數  
 `nColumn`  
 若要編輯資料行。  
  
 `bDiscardChanges`  
 如果使用者正在編輯篩選條件的值，指定如何處理使用者的編輯變更時[HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312)傳送訊息。  
  
 指定`true`捨棄使用者所做的變更或`false`接受使用者所做的變更。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會實作的 Win32 訊息行為[HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]  
  
##  <a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin  
 擷取控制項中的點陣圖邊界的寬度。  
  
```  
int GetBitmapMargin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 單位為像素點陣圖邊界的寬度。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_GETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775314)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]  
  
##  <a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem  
 取得目前的標題控制項中具有焦點之項目的索引。  
  
```  
int GetFocusedItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 具有焦點的標題項目以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[HDM_GETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775330)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例示範`SetFocusedItem`和`GetFocusedItem`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 不過，您可以拖曳資料行分隔符號，使資料行是不可見。 下列範例會設定，然後確認 最後一個資料行標頭，為焦點的項目。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="getimagelist"></a>CHeaderCtrl::GetImageList  
 擷取影像清單控制項中的繪圖標頭項目所使用的控制代碼。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_GETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775332)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 `CImageList`的傳回的指標指向是暫存物件，而且會在下次閒置時間處理刪除的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]  
  
##  <a name="getitem"></a>Cheaderctrl:: Getitem  
 擷取相關的標頭控制項項目資訊。  
  
```  
BOOL GetItem(
    int nPos,  
    HDITEM* pHeaderItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 指定要擷取之項目的以零為起始的索引。  
  
 `pHeaderItem`  
 指標[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)接收新項目的結構。 此結構會搭配`InsertItem`和`SetItem`成員函式。 在設定任何旗標**遮罩**項目會確保傳回時正確填入對應的項目中的值。 如果**遮罩**項目設為零，其他結構項目中的值是無意義。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]  
  
##  <a name="getitemcount"></a>CHeaderCtrl::GetItemCount  
 擷取控制項中的項目計數。  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 標頭控制項項目成功; 如果數目否則為-1。  
  
### <a name="example"></a>範例  
  請參閱範例的[CHeaderCtrl::DeleteItem](#deleteitem)。  
  
##  <a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect  
 取得標頭中的項目目前的標頭控制項下拉式按鈕的週框矩形。  
  
```  
BOOL GetItemDropDownRect(
    int iItem,   
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iItem`|其樣式為標頭項目的以零為起始的索引`HDF_SPLITBUTTON`。 如需詳細資訊，請參閱`fmt`隸屬[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)結構。|  
|[輸出] `lpRect`|指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收週框矩形資訊的結構。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果此函式成功。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[HDM_GETITEMDROPDOWNRECT](http://msdn.microsoft.com/library/windows/desktop/bb775339)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例示範`GetItemDropDownRect`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 下列程式碼範例會繪製 3D 矩形位置周圍保留給標頭下拉式按鈕的第一個資料行上。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]  
  
##  <a name="getitemrect"></a>CHeaderCtrl::GetItemRect  
 擷取控制項中的指定項目的週框。  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 標題控制項項目以零為起始的索引。  
  
 `lpRect`  
 位址指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收週框矩形資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會實作的 Win32 訊息行為[HDM_GETITEMRECT](http://msdn.microsoft.com/library/windows/desktop/bb775341)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getorderarray"></a>Cheaderctrl:: Getorderarray  
 擷取由左到右的順序標題控制項中的項目。  
  
```  
BOOL GetOrderArray(
    LPINT piArray,  
    int iCount);
```  
  
### <a name="parameters"></a>參數  
 `piArray`  
 在控制項標頭中，以其出現從左到右的順序接收項目的索引值的緩衝區的位址指標。  
  
 `iCount`  
 標頭控制項項目數目。 必須為非負數。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_GETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775343)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它被提供來支援標頭項目順序。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]  
  
##  <a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect  
 取得目前的標頭控制項的溢位按鈕的週框矩形。  
  
```  
BOOL GetOverflowRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸出] `lpRect`|指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收週框矩形資訊的結構。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果此函式成功。否則， `false`。  
  
### <a name="remarks"></a>備註  
 標頭控制項中包含不可以同時顯示多個項目，如果控制項可以顯示溢位按鈕捲動看不到的項目。 標頭控制項都必須有`HDS_OVERFLOW`和`HDF_SPLITBUTTON`顯示溢位按鈕的樣式。 周框溢位按鈕圍住，且有只時顯示溢位按鈕。 如需詳細資訊，請參閱[標頭控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775241)。  
  
 這個方法會傳送[HDM_GETOVERFLOWRECT](http://msdn.microsoft.com/library/windows/desktop/bb775345)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例示範`GetOverflowRect`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 不過，您可以拖曳資料行分隔符號，使資料行是不可見。 如果看不到某些資料行，此標題控制項繪製溢位按鈕。 下列程式碼範例會繪製 3D 矩形周圍溢位按鈕的位置。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]  
  
##  <a name="hittest"></a>CHeaderCtrl::HitTest  
 決定哪一個標頭項目，如果有的話，位於指定點。  
  
```  
int HitTest(LPHDHITTESTINFO* phdhti);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in、out] `phdhti`|指標[HDHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb775245)結構，以指定要測試的點，並接收測試的結果。|  
  
### <a name="return-value"></a>傳回值  
 標頭項目，如果有的話，在指定的位置以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[HDM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb775349)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例示範`HitTest`方法。 在先前章節中的這個程式碼範例，我們會使用五個資料行建立標題控制項。 不過，您可以拖曳資料行分隔符號，使資料行是不可見。 如果顯示這個範例會報告資料行的索引和-1，如果看不到資料行。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]  
  
##  <a name="insertitem"></a>Cheaderctrl:: Insertitem  
 將新的項目插入至指定索引處的標頭控制項。  
  
```  
int InsertItem(
    int nPos,  
    HDITEM* phdi);
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 要插入之項目之以零起始的索引。 如果值為零，此標題控制項的開頭插入項目。 如果值大於最大值，此項目插入標頭控制項的結尾。  
  
 *phdi*  
 指標[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)結構，其中包含要插入項目的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 的新項目索引否則為-1。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]  
  
##  <a name="layout"></a>CHeaderCtrl::Layout  
 擷取給定矩形內的標頭控制項的位置與大小。  
  
```  
BOOL Layout(HDLAYOUT* pHeaderLayout);
```  
  
### <a name="parameters"></a>參數  
 *pHeaderLayout*  
 指標[HDLAYOUT](http://msdn.microsoft.com/library/windows/desktop/bb775249)結構，其中包含用來設定的大小和位置標頭控制項的資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式用來決定適當的大小，針對新的標頭控制項，以佔用給定的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]  
  
##  <a name="ordertoindex"></a>Cheaderctrl:: Ordertoindex  
 擷取的項目，其標題控制項中的順序為基礎的索引值。  
  
```  
int OrderToIndex(int nOrder) const;  
```  
  
### <a name="parameters"></a>參數  
 *nOrder*  
 從左到右，所出現的標頭控制項中的項目以零為起始的順序。  
  
### <a name="return-value"></a>傳回值  
 項目，其標題控制項中的順序為基礎的索引。 索引會計算從左到右，從 0 開始。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 巨集行為[HDM_ORDERTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb775355)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它被提供來支援標頭項目順序。  
  
##  <a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin  
 標題控制項中設定點陣圖的邊界的寬度。  
  
```  
int SetBitmapMargin(int nWidth);
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 指定寬度邊界四周內現有的標頭控制項的點陣圖的像素為單位。  
  
### <a name="return-value"></a>傳回值  
 單位為像素點陣圖邊界的寬度。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_SETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775357)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]  
  
##  <a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout  
 設定逾時之間的間隔時間變更發生在篩選條件屬性，且公佈[HDN_FILTERCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb775277)通知。  
  
```  
int SetFilterChangeTimeout(DWORD dwTimeOut);
```  
  
### <a name="parameters"></a>參數  
 *dwTimeOut*  
 逾時值，以毫秒為單位。  
  
### <a name="return-value"></a>傳回值  
 要修改篩選控制項的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_SETFILTERCHANGETIMEOUT](http://msdn.microsoft.com/library/windows/desktop/bb775359)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]  
  
##  <a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem  
 將焦點設定至目前的標題控制項中指定的標頭項目。  
  
```  
BOOL SetFocusedItem(int iItem);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iItem`|標頭項目的以零為起始的索引。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[HDM_SETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775361)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例示範`SetFocusedItem`和`GetFocusedItem`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 不過，您可以拖曳資料行分隔符號，使資料行是不可見。 下列範例會設定，然後確認 最後一個資料行標頭，為焦點的項目。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider  
 變更標頭項目，以表示手動之間的分隔線拖曳和卸除的標頭項目。  
  
```  
int SetHotDivider(CPoint pt);  
int SetHotDivider(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 指標的位置。 標題控制項中，反白顯示適當的分割線根據指標的位置。  
  
 `nIndex`  
 反白顯示分割線的索引。  
  
### <a name="return-value"></a>傳回值  
 反白顯示分割線的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_SETHOTDIVIDER](http://msdn.microsoft.com/library/windows/desktop/bb775363)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它被提供來支援標頭項目拖曳和卸除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]  
  
##  <a name="setimagelist"></a>CHeaderCtrl::SetImageList  
 指派至標題控制項的影像清單。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 指標`CImageList`物件，其中包含要指派至標題控制項之影像清單。  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)先前指派給此標題控制項的物件。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[HDM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775365)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 `CImageList`的傳回的指標指向是暫存物件，而且會在下次閒置時間處理刪除的物件。  
  
### <a name="example"></a>範例  
  請參閱範例的[CHeaderCtrl::GetImageList](#getimagelist)。  
  
##  <a name="setitem"></a>Cheaderctrl:: Setitem  
 標題控制項中，設定指定之項目的屬性。  
  
```  
BOOL SetItem(
    int nPos,  
    HDITEM* pHeaderItem);
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 可操作的項目以零為起始的索引。  
  
 `pHeaderItem`  
 指標[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)結構，其中包含新項目的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例的[cheaderctrl:: Getitem](#getitem)。  
  
##  <a name="setorderarray"></a>Cheaderctrl:: Setorderarray  
 設定由左到右的順序的項目控制項中。  
  
```  
BOOL SetOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>參數  
 `iCount`  
 標頭控制項項目數目。  
  
 `piArray`  
 在控制項標頭中，以其出現從左到右的順序接收項目的索引值的緩衝區的位址指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 巨集行為[HDM_SETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775369)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它被提供來支援標頭項目順序。  
  
### <a name="example"></a>範例  
  請參閱範例的[cheaderctrl:: Getorderarray](#getorderarray)。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)   
 [CListCtrl 類別](../../mfc/reference/clistctrl-class.md)   
 [CImageList 類別](../../mfc/reference/cimagelist-class.md)

