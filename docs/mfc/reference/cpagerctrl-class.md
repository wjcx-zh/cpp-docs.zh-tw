---
title: "CPagerCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CPagerCtrl class
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
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
ms.openlocfilehash: 8b8bf05873239f274a9b1285797c01123fe071f7
ms.lasthandoff: 02/24/2017

---
# <a name="cpagerctrl-class"></a>CPagerCtrl 類別
`CPagerCtrl` 類別會封裝 Windows 頁面巡覽區控制項，可以將不符合容器視窗大小的包含視窗捲動到檢視中。  
  
## <a name="syntax"></a>語法  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|建構 `CPagerCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPagerCtrl::Create](#create)|使用指定的樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。|  
|[CPagerCtrl::CreateEx](#createex)|使用指定的延伸樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|啟用或停用轉送[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)包含在目前的頁面巡覽區控制項的視窗訊息。|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|擷取目前的頁面巡覽區控制項的背景色彩。|  
|[CPagerCtrl::GetBorder](#getborder)|擷取目前的頁面巡覽區控制項的框線大小。|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|擷取目前的頁面巡覽區控制項的按鈕大小。|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|擷取目前的頁面巡覽區控制項中指定的按鍵的狀態。|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|擷取[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)目前的頁面巡覽區控制項的介面。|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|擷取目前的頁面巡覽區控制項的捲動位置。|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|指出指定的按鈕，目前的頁面巡覽區控制項是否處於`pressed`狀態。|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|指出指定的按鈕，目前的頁面巡覽區控制項是否處於`grayed`狀態。|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|指出指定的按鈕，目前的頁面巡覽區控制項是否處於`hot`狀態。|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|指出指定的按鈕，目前的頁面巡覽區控制項是否處於`invisible`狀態。|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|指出指定的按鈕，目前的頁面巡覽區控制項是否處於`normal`狀態。|  
|[CPagerCtrl::RecalcSize](#recalcsize)|導致目前的頁面巡覽區控制項重新計算包含視窗的大小。|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|設定目前的頁面巡覽區控制項的背景色彩。|  
|[CPagerCtrl::SetBorder](#setborder)|設定目前的頁面巡覽區控制項的框線大小。|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|設定目前的頁面巡覽區控制項的按鈕大小。|  
|[CPagerCtrl::SetChild](#setchild)|設定目前的頁面巡覽區控制項所包含的視窗。|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|設定目前的頁面巡覽區控制項的捲動位置。|  
  
## <a name="remarks"></a>備註  
 頁面巡覽區控制項是包含是線性和大於所包含的視窗，並可讓您包含的視窗捲動到檢視的另一個視窗的視窗。 頁面巡覽區控制項顯示兩個捲軸按鈕，會自動地消失包含的視窗捲動到最遠的範圍，與否則會重新出現。 您可以建立水平或垂直捲動頁面巡覽區控制項。  
  
 比方說，如果您的應用程式有一個工具列，寬度不足以顯示所有項目，您可以指定頁面巡覽區控制項工具列和使用者能夠捲動到左邊或右邊來存取所有項目工具列。 Microsoft Internet Explorer 版本 4.0 （commctrl.dll 版本 4.71） 介紹頁面巡覽區控制項。  
  
 `CPagerCtrl`類別衍生自[CWnd](../../mfc/reference/cwnd-class.md)類別。 如需詳細資訊和頁面巡覽區控制項的說明，請參閱[頁面巡覽區控制項](http://msdn.microsoft.com/library/windows/desktop/bb760855)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="a-namecpagerctrla--cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl  
 建構 `CPagerCtrl` 物件。  
  
```  
CPagerCtrl();
```  
  
### <a name="remarks"></a>備註  
 使用[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)方法來建立頁面巡覽區控制項，並將其附加至`CPagerCtrl`物件。  
  
##  <a name="a-namecreatea--cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl::Create  
 使用指定的樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwStyle`|位元組合 (OR)[視窗樣式](../../mfc/reference/window-styles.md)和[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)来套用至控制項。|  
|[in] `rect`|參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含用戶端座標中控制項的大小與位置。|  
|[in] `pParentWnd`|指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。 此參數不得為`NULL`。|  
|[in] `nID`|控制項的 ID。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 若要建立頁面巡覽區控制項，宣告`CPagerCtrl`變數，然後呼叫[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)位於變數上的方法。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項產生關聯很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法，將框線粗細設定為 1 個像素。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&1;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namecreateexa--cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl::CreateEx  
 使用指定的延伸樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwExStyle`|若要套用至控制項的延伸樣式的位元組合。 如需詳細資訊，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函式。|  
|[in] `dwStyle`|位元組合 (OR)[視窗樣式](../../mfc/reference/window-styles.md)和[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)来套用至控制項。|  
|[in] `rect`|參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含用戶端座標中控制項的大小與位置。|  
|[in] `pParentWnd`|指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。 此參數不得為`NULL`。|  
|[in] `nID`|控制項的 ID。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 若要建立頁面巡覽區控制項，宣告`CPagerCtrl`變數，然後呼叫[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)位於變數上的方法。  
  
##  <a name="a-nameforwardmousea--cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl::ForwardMouse  
 啟用或停用轉送[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)包含在目前的頁面巡覽區控制項的視窗訊息。  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `bForward`|`true`將滑鼠訊息轉送或`false`將滑鼠訊息無法轉送。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_FORWARDMOUSE](http://msdn.microsoft.com/library/windows/desktop/bb760867)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbordera--cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl::GetBorder  
 擷取目前的頁面巡覽區控制項的框線大小。  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的框線大小，以像素為單位。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760869)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::GetBorder](#getborder)方法來擷取頁面巡覽區控制項的框線的粗細。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&5;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="a-namegetbkcolora--cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl::GetBkColor  
 擷取目前的頁面巡覽區控制項的背景色彩。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，其中包含目前的頁面巡覽區控制項的背景色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760868)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::SetBkColor](#setbkcolor)方法，將頁面巡覽區控制項的背景色彩設定為紅色，而[CPagerCtrl::GetBkColor](#getbkcolor)方法，以確認已進行變更。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&4;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="a-namegetbuttonsizea--cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize  
 擷取目前的頁面巡覽區控制項的按鈕大小。  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前按鈕的大小，單位為像素為單位。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760870)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果頁面巡覽區控制項有`PGS_HORZ`樣式 按鈕的大小會決定頁面巡覽區按鈕的寬度與頁面巡覽區控制項有`PGS_VERT`樣式 按鈕的大小會決定頁面巡覽區按鈕的高度。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。  
  
##  <a name="a-namegetbuttonstatea--cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl::GetButtonState  
 擷取目前的頁面巡覽區控制項中指定的捲軸按鈕的狀態。  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左按鈕和`PGB_BOTTOMORRIGHT`的向右按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`下方的按鈕。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 所指定的按鍵的狀態`iButton`參數。 The state is either `PGF_INVISIBLE`, `PGF_NORMAL`, `PGF_GRAYED`, `PGF_DEPRESSED`, or `PGF_HOT`. 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdroptargeta--cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl::GetDropTarget  
 擷取[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)目前的頁面巡覽區控制項的介面。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IDropTarget`目前的頁面巡覽區控制項的介面。  
  
### <a name="remarks"></a>備註  
 `IDropTarget`是您所實作的介面的其中一個支援您的應用程式中的拖放作業。  
  
 這個方法會傳送[PGM_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb760872)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此方法的呼叫端會負責呼叫`Release`成員[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)介面時不再需要的介面。  
  
##  <a name="a-namegetscrollposa--cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl::GetScrollPos  
 擷取目前的頁面巡覽區控制項的捲動位置。  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的捲動位置，以像素為單位。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760874)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::GetScrollPos](#getscrollpos)方法來擷取目前捲動位置的頁面巡覽區控制項。 如果為零，最左邊的位置，已經不捲動頁面巡覽區控制項的範例會使用[CPagerCtrl::SetScrollPos](#setscrollpos)方法，以將捲軸的位置設定為零。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&7;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="a-nameisbuttondepresseda--cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed  
 表示指定之捲軸按鈕的目前頁面巡覽區控制項是否處於已按下的狀態。  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左按鈕和`PGB_BOTTOMORRIGHT`的向右按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`下方的按鈕。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕是處於已按下狀態;否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 然後它會測試是否會傳回的狀態為`PGF_DEPRESSED`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="a-nameisbuttongrayeda--cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed  
 表示指定之捲軸按鈕的目前頁面巡覽區控制項是否處於灰色的狀態。  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左按鈕和`PGB_BOTTOMORRIGHT`的向右按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`下方的按鈕。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕是處於灰色狀態;否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 然後它會測試是否會傳回的狀態為`PGF_GRAYED`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="a-nameisbuttonhota--cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot  
 表示指定之捲軸按鈕的目前頁面巡覽區控制項是否處於作用中狀態。  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左按鈕和`PGB_BOTTOMORRIGHT`的向右按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`下方的按鈕。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕處於作用中狀態。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 然後它會測試是否會傳回的狀態為`PGF_HOT`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="a-nameisbuttoninvisiblea--cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible  
 表示指定之捲軸按鈕的目前頁面巡覽區控制項是否處於隱藏狀態。  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左按鈕和`PGB_BOTTOMORRIGHT`的向右按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`下方的按鈕。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕是不可見狀態。否則， `false`。  
  
### <a name="remarks"></a>備註  
 Windows 會讓捲軸按鈕以特定方向時則包含的視窗捲動以顯示其最遠由於按一下按鈕進一步無法讓多個 [包含] 視窗中檢視。  
  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 然後它會測試是否會傳回的狀態為`PGF_INVISIBLE`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)方法，以判斷是否頁面巡覽區控制項的左與向右捲動按鈕會顯示。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&6;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="a-nameisbuttonnormala--cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal  
 表示指定之捲軸按鈕的目前頁面巡覽區控制項是否處於正常狀態。  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左按鈕和`PGB_BOTTOMORRIGHT`的向右按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`下方的按鈕。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕處於正常狀態。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 然後它會測試是否會傳回的狀態為`PGF_NORMAL`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="a-namerecalcsizea--cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl::RecalcSize  
 導致目前的頁面巡覽區控制項重新計算包含視窗的大小。  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_RECALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760876)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 因此，會傳送頁面巡覽區控制項[PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864)通知，以取得包含視窗的可捲動的維度。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::RecalcSize](#recalcsize)方法來要求重新計算其大小目前的頁面巡覽區控制項。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&3;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>範例  
 下列範例會使用[訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md)啟用頁面巡覽區控制項，重新計算而不需要執行計算的控制項的父對話方塊大小。 範例衍生`MyPagerCtrl`類別是從[CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)，然後使用訊息對應產生關聯[PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864)通知`OnCalcsize`通知處理常式。 在此範例中，通知處理常式將設定的頁面巡覽區控制項的高度與寬度固定值。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&8;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="a-namesetbkcolora--cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl::SetBkColor  
 設定目前的頁面巡覽區控制項的背景色彩。  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `clrBk`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，其中包含新的頁面巡覽區控制項的背景色彩。|  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，其中包含前一個頁面巡覽區控制項的背景色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760878)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::SetBkColor](#setbkcolor)方法，將頁面巡覽區控制項的背景色彩設定為紅色，而[CPagerCtrl::GetBkColor](#getbkcolor)方法，以確認已進行變更。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&4;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="a-namesetbordera--cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl::SetBorder  
 設定目前的頁面巡覽區控制項的框線大小。  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iBorder`|新框線的大小，單位為像素為單位。 如果`iBorder`參數是負值，框線大小會設為零。|  
  
### <a name="return-value"></a>傳回值  
 先前的框線大小，以像素為單位。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760880)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項產生關聯很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法，將框線粗細設定為 1 個像素。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&1;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namesetbuttonsizea--cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize  
 設定目前的頁面巡覽區控制項的按鈕大小。  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iButtonSize`|新按鈕的大小，單位為像素為單位。|  
  
### <a name="return-value"></a>傳回值  
 先前按鈕的大小，單位為像素為單位。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760886)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果頁面巡覽區控制項有`PGS_HORZ`樣式 按鈕的大小會決定頁面巡覽區按鈕的寬度與頁面巡覽區控制項有`PGS_VERT`樣式 按鈕的大小會決定頁面巡覽區按鈕的高度。 預設按鈕的大小是四分之三的捲軸的寬度，而按鈕的最小大小為 12 個像素。 如需詳細資訊，請參閱[頁面巡覽區控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項產生關聯很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法，將框線粗細設定為 1 個像素。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&1;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namesetchilda--cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl::SetChild  
 設定目前的頁面巡覽區控制項所包含的視窗。  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hwndChild`|包含視窗控制代碼。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETCHILD](http://msdn.microsoft.com/library/windows/desktop/bb760884)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這個方法不會變更父系的包含視窗中，它只會指派給捲動頁面巡覽區控制項的視窗控制代碼。 在大部分情況下，包含的視窗會是頁面巡覽區控制項的子視窗。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項產生關聯很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法，將框線粗細設定為 1 個像素。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&1;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namesetscrollposa--cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl::SetScrollPos  
 設定目前的頁面巡覽區控制項的捲動位置。  
  
```  
void SetScrollPos(int iPos);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iPos`|新的捲動位置，以像素為單位。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760886)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [頁面巡覽區控制項](http://msdn.microsoft.com/library/windows/desktop/bb760855)




