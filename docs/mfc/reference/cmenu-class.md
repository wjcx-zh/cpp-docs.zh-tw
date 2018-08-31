---
title: CMenu 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
dev_langs:
- C++
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c94542fdac3734644771f2659d894d1c8c6f907
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220798"
---
# <a name="cmenu-class"></a>CMenu 類別
Windows `HMENU`的封裝。  
  
## <a name="syntax"></a>語法  
  
```  
class CMenu : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMenu::CMenu](#cmenu)|建構 `CMenu` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMenu::AppendMenu](#appendmenu)|將新的項目附加至這個功能表的尾端。|  
|[CMenu::Attach](#attach)|附加的 Windows 功能表控制代碼`CMenu`物件。|  
|[CMenu::CheckMenuItem](#checkmenuitem)|旁放置核取記號，或從快顯功能表的功能表項目移除核取記號。|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|將功能表項目旁邊的選項按鈕，並從所有其他功能表項目群組中移除的選項按鈕。|  
|[CMenu::CreateMenu](#createmenu)|建立空的功能表，並將它附加至`CMenu`物件。|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|建立空的快顯功能表，並將它附加至`CMenu`物件。|  
|[CMenu::DeleteMenu](#deletemenu)|從功能表中刪除指定的項目。 如果功能表項目具有相關聯的快顯功能表，會終結快顯功能表的控制代碼，並釋放它所使用的記憶體。|  
|[CMenu::DeleteTempMap](#deletetempmap)|刪除暫時`CMenu`所建立的物件`FromHandle`成員函式。|  
|[CMenu::DestroyMenu](#destroymenu)|終結附加到功能表`CMenu`物件，並釋放任何功能表所佔用的記憶體。|  
|[CMenu::Detach](#detach)|中斷連結的 Windows 功能表的控制代碼從`CMenu`物件，並傳回的控制代碼。|  
|[CMenu::DrawItem](#drawitem)|由架構時為主控描繪功能表會變更的視覺外觀的呼叫。|  
|[CMenu::EnableMenuItem](#enablemenuitem)|啟用、 停用，或變暗 （灰色） 的功能表項目。|  
|[CMenu::FromHandle](#fromhandle)|將指標傳回至`CMenu`Windows 功能表控制代碼提供的物件。|  
|[CMenu::GetDefaultItem](#getdefaultitem)|判斷指定的功能表的預設功能表項目。|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|擷取與功能表相關的說明內容識別碼。|  
|[CMenu::GetMenuInfo](#getmenuinfo)|擷取特定的功能表上的資訊。|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|判斷在快顯畫面或最上層功能表中的項目數。|  
|[CMenu::GetMenuItemID](#getmenuitemid)|取得功能表項目位於指定位置的功能表項目識別項。|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|擷取功能表項目相關的資訊。|  
|[CMenu::GetMenuState](#getmenustate)|快顯功能表中，傳回指定的功能表項目或項目數目的狀態。|  
|[CMenu::GetMenuString](#getmenustring)|擷取指定的功能表項目的標籤。|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|傳回`m_hMenu`由此包裝`CMenu`物件。|  
|[CMenu::GetSubMenu](#getsubmenu)|擷取的快顯功能表的指標。|  
|[CMenu::InsertMenu](#insertmenu)|將新的功能表項目插入位於指定位置，將其他項目移下的功能表。|  
|[CMenu::InsertMenuItem](#insertmenuitem)|在功能表中的指定位置中插入新的功能表項目。|  
|[CMenu::LoadMenu](#loadmenu)|從可執行檔載入功能表資源，並將它附加至`CMenu`物件。|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|從功能表中的範本的記憶體載入功能表，並將它附加至`CMenu`物件。|  
|[CMenu::MeasureItem](#measureitem)|由架構呼叫以判斷功能表維度建立主控描繪功能表時。|  
|[CMenu::ModifyMenu](#modifymenu)|變更現有的功能表項目位於指定位置。|  
|[CMenu::RemoveMenu](#removemenu)|從指定的功能表中刪除相關聯的快顯功能表的功能表項目。|  
|[CMenu::SetDefaultItem](#setdefaultitem)|設定指定的功能表的預設功能表項目。|  
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|設定要與功能表關聯的說明內容識別碼。|  
|[CMenu::SetMenuInfo](#setmenuinfo)|設定特定的功能表上的資訊。|  
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|將指定的核取記號點陣圖與功能表項目產生關聯。|  
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|變更功能表項目相關的資訊。|  
|[CMenu::TrackPopupMenu](#trackpopupmenu)|會浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。|  
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|會浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|擷取功能表物件的控制代碼。|  
|[CMenu::operator ！ =](#operator_neq)|判斷兩個功能表物件是否不相等。|  
|[CMenu::operator = =](#operator_eq_eq)|判斷兩個功能表物件是否相等。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|指定附加至 [Windows] 功能表的控制代碼`CMenu`物件。|  
  
## <a name="remarks"></a>備註  
 它提供成員函式建立、 追蹤、 更新和終結功能表。  
  
 建立`CMenu`物件上作為本機堆疊框架，然後呼叫`CMenu`的視需要管理的新功能表中的成員函式。 接下來，呼叫[CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu)將功能表設定為視窗中，緊接著呼叫`CMenu`物件的[卸離](#detach)成員函式。 `CWnd::SetMenu`成員函式設定至新功能表的視窗 功能表，會使視窗重繪以反映功能表變更，並也會傳遞至視窗的功能表的擁有權。 在呼叫`Detach`中斷連結從 HMENU`CMenu`物件，因此，當本機`CMenu`變數超出範圍，`CMenu`物件解構函式不會嘗試終結它不再擁有功能表。 功能表本身會自動終結時終結視窗。  
  
 您可以使用[LoadMenuIndirect](#loadmenuindirect)成員函式來建立範本，以在記憶體中，從功能表，但透過呼叫建立的資源功能表[LoadMenu](#loadmenu)更容易維護和本身的功能表資源可以建立和修改功能表編輯器。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="appendmenu"></a>  CMenu::AppendMenu  
 將新的項目附加至結尾的功能表中。  
  
```  
BOOL AppendMenu(
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL AppendMenu(
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>參數  
 *nFlags*  
 加入至功能表時，請指定新的功能表項目的狀態的相關資訊。 它包含一或多個 「 備註 」 一節中所列的值。  
  
 *nIDNewItem*  
 指定命令識別碼的新功能表項目或者，如果*nFlags*設定為 MF_POPUP，功能表控制代碼 ( `HMENU`) 的快顯功能表。 *NIDNewItem*參數會忽略 （不需要），如果*nFlags*設 MF_SEPARATOR。  
  
 *lpszNewItem*  
 指定新的功能表項目的內容。 *NFlags*參數用來解譯*lpszNewItem*方式如下：  
  
|nFlags|LpszNewItem 的解譯|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|包含應用程式所提供的 32 位元值，應用程式可用來維護功能表項目相關聯的其他資料。 它能處理 WM_MEASUREITEM 和 WM_DRAWITEM 訊息時，應用程式可以使用這個 32 位元值。 值會儲存在`itemData`隨附這些訊息結構的成員。|  
|MF_STRING|包含以 null 終止的字串的指標。 這是預設解譯。|  
|MF_SEPARATOR|*LpszNewItem*參數會被忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`用作功能表項目中的物件。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式可以在程式中設定值，指定功能表項目的狀態*nFlags*。 當*nIDNewItem*指定的快顯功能表中，就會附加 [] 功能表的一部分。 如果該功能表時損毀，也會終結附加的功能表。 附加的功能表應該從已中斷連結`CMenu`物件，以避免衝突。 請注意，MF_STRING 和 MF_OWNERDRAW 不是有效的點陣圖版本`AppendMenu`。  
  
 下列清單將描述可能會在設定的旗標*nFlags*:  
  
- MF_CHECKED 是做為切換 MF_UNCHECKED 放置預設值與核取記號項目旁。 當應用程式會提供核取記號點陣圖 (請參閱[SetMenuItemBitmaps](#setmenuitembitmaps)成員函式)，會顯示"上的核取記號"點陣圖。  
  
- 將做為切換 MF_UNCHECKED 與 MF_CHECKED 移除項目旁的核取記號。 當應用程式會提供核取記號點陣圖 (請參閱`SetMenuItemBitmaps`成員函式)，會顯示 「 關閉的核取記號"點陣圖。  
  
- MF_DISABLED 停用功能表項目，使它無法選取，但不會變暗。  
  
- MF_ENABLED，使其選取，並將它還原從其呈現暗灰色的狀態，可讓功能表項目。  
  
- 無法選取，使其變暗它 MF_GRAYED 會停用功能表項目。  
  
- MF_MENUBARBREAK 置於新行在靜態功能表中，或在新的資料行，在快顯功能表中的項目。 新的快顯功能表欄會隔開垂直分隔線的舊的資料行。  
  
- MF_MENUBREAK 置於新行在靜態功能表中，或在新的資料行，在快顯功能表中的項目。 資料行之間，位於沒有分隔線。  
  
- MF_OWNERDRAW 指定的項目是主控描繪項目。 第一次出現的功能表時，擁有功能表的視窗，就會收到 WM_MEASUREITEM 訊息時，它會擷取的高度和寬度的功能表項目。 WM_DRAWITEM 訊息是傳送時擁有者必須更新的視覺外觀的功能表項目。 此選項不是有效的最上層的功能表項目。  
  
- MF_POPUP 指定功能表項目具有與其相關聯的快顯功能表。 ID 參數指定要與項目相關聯的快顯功能表的控制代碼。 這用於最上層的快顯功能表或階層式的快顯功能表加入快顯功能表項目。  
  
- MF_SEPARATOR 繪製水平分隔線。 只有在快顯功能表中使用。 無法呈現暗灰色，停用，或反白顯示這一行。 會忽略其他參數。  
  
- MF_STRING 指定功能表項目是字元字串。  
  
 下列群組的每個列出互斥，而且無法一起使用的旗標：  
  
- MF_DISABLED、 MF_ENABLED 和 MF_GRAYED  
  
- MF_STRING、 MF_OWNERDRAW、 MF_SEPARATOR 和點陣圖版本  
  
- MF_MENUBARBREAK 和 MF_MENUBREAK  
  
- MF_CHECKED 和 MF_UNCHECKED  
  
 每當在位於功能表視窗變更時 （不論是否顯示視窗），應用程式應該呼叫[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="attach"></a>  CMenu::Attach  
 附加至現有的 Windows 功能表`CMenu`物件。  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 *hMenu*  
 指定 Windows 功能表的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 應該不會呼叫此函式，如果功能表尚未附加至`CMenu`物件。 功能表控制代碼會儲存在`m_hMenu`資料成員。  
  
 如果您想要操作的功能表已經與視窗相關聯，您可以使用[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)函式可取得功能表的控制代碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="checkmenuitem"></a>  CMenu::CheckMenuItem  
 新增核取記號，或移除功能表項目在快顯功能表中的核取記號。  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>參數  
 *nIDCheckItem*  
 指定要檢查功能表項目，由*n*。  
  
 *n*  
 指定如何檢查功能表項目以及如何判斷在功能表中的項目的位置。 *n*參數可以是 MF_CHECKED 或 MF_UNCHECKED 中的結合 MF_BYPOSITION 或 MF_BYCOMMAND 旗標。 使用位元的 OR 運算子，可以結合這些旗標。 它們具有下列意義：  
  
- MF_BYCOMMAND 指定此參數可讓現有的功能表項目的命令識別碼。 這是預設值。  
  
- MF_BYPOSITION 指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。  
  
- MF_CHECKED 是做為切換 MF_UNCHECKED 放置預設值與核取記號項目旁。  
  
- 將做為切換 MF_UNCHECKED 與 MF_CHECKED 移除項目旁的核取記號。  
  
### <a name="return-value"></a>傳回值  
 先前的狀態項目： MF_CHECKED 或 MF_UNCHECKED，或 0xFFFFFFFF 如果功能表項目不存在。  
  
### <a name="remarks"></a>備註  
 *NIDCheckItem*參數會指定要修改的項目。  
  
 *NIDCheckItem*參數可識別將快顯功能表項目，以及功能表項目。 若要檢查的快顯功能表項目，不需要任何特殊步驟。 您無法選取最上層的功能表項目。 位置必須檢查的快顯功能表項目，因為它沒有與其相關聯的功能表項目識別碼。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::GetMenuState](#getmenustate)。  
  
##  <a name="checkmenuradioitem"></a>  CMenu::CheckMenuRadioItem  
 會檢查指定的功能表項目，並讓選項項目。  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 *nIDFirst*  
 指定 (做為 ID 或位移值而定*nFlags*) 選項按鈕群組中的第一個功能表項目。  
  
 *nIDLast*  
 指定 (做為 ID 或位移值而定*nFlags*) 最後一個選項按鈕群組中的功能表項目。  
  
 *nIDItem*  
 指定 (做為 ID 或位移值而定*nFlags*) 將會檢查使用的選項按鈕群組中的項目。  
  
 *nFlags*  
 指定解譯*nIDFirst*， *nIDLast*，並*nIDItem*方式如下：  
  
|nFlags|解譯|  
|------------|--------------------|  
|MF_BYCOMMAND|指定此參數可讓現有的功能表項目的命令識別碼。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 都不設定，這是預設值。|  
|MF_BYPOSITION|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則便是 0  
  
### <a name="remarks"></a>備註  
 在此同時，函式會取消核取相關聯的群組中所有其他功能表項目，並清除這些項目的選項項目型別旗標。 已檢查的項目會顯示使用選項按鈕 （或項目符號） 點陣圖，而不核取記號點陣圖。  
  
### <a name="example"></a>範例  
  範例，請參閱[ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)。  
  
##  <a name="cmenu"></a>  CMenu::CMenu  
 建立空的功能表，並將它附加至`CMenu`物件。  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>備註  
 直到您呼叫其中一個建立或載入的成員函式，才會建立功能表 `CMenu:`  
  
- [CreateMenu](#createmenu)  
  
- [CreatePopupMenu](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [Attach](#attach)  
  
##  <a name="createmenu"></a>  CMenu::CreateMenu  
 會建立一個功能表，並將它附加至`CMenu`物件。  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果已成功; 建立功能表否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表是一開始是空的。 可以使用 [新增] 功能表項目`AppendMenu`或`InsertMenu`成員函式。  
  
 如果功能表指派至 視窗，自動終結時終結視窗。  
  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派至 視窗相關聯的功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="createpopupmenu"></a>  CMenu::CreatePopupMenu  
 建立快顯功能表，並將它附加至`CMenu`物件。  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>傳回值  
 如果已成功建立快顯功能表，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表是一開始是空的。 可以使用 [新增] 功能表項目`AppendMenu`或`InsertMenu`成員函式。 應用程式可以將快顯功能表加入現有的功能表或快顯功能表。 `TrackPopupMenu`可能使用成員函式，這個功能表顯示為浮動的快顯功能表，並追蹤快顯功能表上的選取項目。  
  
 如果功能表指派至 視窗，自動終結時終結視窗。 如果功能表會加入至現有的功能表中，會自動終結時終結該功能表。  
  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派至 視窗相關聯的快顯功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="deletemenu"></a>  CMenu::DeleteMenu  
 從功能表中刪除的項目。  
  
```  
BOOL DeleteMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 *只有*  
 指定的功能表項目會被刪除，由*nFlags*。  
  
 *nFlags*  
 用來解譯*只有*方式如下：  
  
|nFlags|只有的解譯|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定此參數可讓現有的功能表項目的命令識別碼。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 都不設定，這是預設值。|  
|MF_BYPOSITION|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此功能表項目相關聯的快顯功能表上，`DeleteMenu`終結快顯功能表的控制代碼，並釋放快顯功能表所使用的記憶體。  
  
 每當在位於功能表視窗變更時 （不論是否顯示視窗），應用程式必須呼叫[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。  
  
### <a name="example"></a>範例  
  範例，請參閱[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)。  
  
##  <a name="deletetempmap"></a>  CMenu::DeleteTempMap  
 會自動呼叫`CWinApp`閒置時間處理常式中，刪除任何暫存`CMenu`所建立的物件[FromHandle](#fromhandle)成員函式。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>備註  
 `DeleteTempMap` 會附加至暫存的 Windows 功能表物件卸離`CMenu`物件，然後再刪除`CMenu`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="destroymenu"></a>  CMenu::DestroyMenu  
 終結的功能表，然後使用任何 Windows 資源。  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>傳回值  
 如果功能表損毀;，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 從卸離功能表`CMenu`物件終結之前。 Windows`DestroyMenu`函式會自動呼叫`CMenu`解構函式。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="detach"></a>  CMenu::Detach  
 卸離 Windows 功能表`CMenu`物件，並傳回的控制代碼。  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>傳回值  
 控制代碼型別的 HMENU，Windows 功能表上，如果成功，否則為 NULL。  
  
### <a name="remarks"></a>備註  
 `m_hMenu`資料成員設為 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="drawitem"></a>  CMenu::DrawItem  
 由架構時為主控描繪功能表會變更的視覺外觀的呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDrawItemStruct*  
 指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含的所需的繪圖類型的相關資訊。  
  
### <a name="remarks"></a>備註  
 `itemAction`隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 覆寫此成員函式，來實作活動，抽獎獲得主控描繪`CMenu`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前終止此成員函式。  
  
 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)的說明`DRAWITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 下列程式碼是從 MFC [CTRLTEST](../../visual-cpp-samples.md)範例：  
  
 [!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]  
  
##  <a name="enablemenuitem"></a>  CMenu::EnableMenuItem  
 啟用、 停用，或變暗的功能表項目。  
  
```  
UINT EnableMenuItem(
    UINT nIDEnableItem,  
    UINT nEnable);
```  
  
### <a name="parameters"></a>參數  
 *nIDEnableItem*  
 指定功能表項目，若要啟用，由*nEnable*。 快顯功能表項目，以及標準功能表項目，可以指定此參數。  
  
 *nEnable*  
 指定要採取的動作。 它可以是 MF_DISABLED、 MF_ENABLED 或 MF_GRAYED，MF_BYCOMMAND 或 MF_BYPOSITION 的組合。 使用位元的 OR 運算子，可以結合這些值。 這些值具有下列意義：  
  
- MF_BYCOMMAND 指定此參數可讓現有的功能表項目的命令識別碼。 這是預設值。  
  
- MF_BYPOSITION 指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。  
  
- MF_DISABLED 停用功能表項目，使它無法選取，但不會變暗。  
  
- MF_ENABLED，使其選取，並將它還原從其呈現暗灰色的狀態，可讓功能表項目。  
  
- 無法選取，使其變暗它 MF_GRAYED 會停用功能表項目。  
  
### <a name="return-value"></a>傳回值  
 先前的狀態 （MF_DISABLED、 MF_ENABLED 或 MF_GRAYED） 則為-1 無效。  
  
### <a name="remarks"></a>備註  
 [CreateMenu](#createmenu)， [InsertMenu](#insertmenu)， [ModifyMenu](#modifymenu)，以及[LoadMenuIndirect](#loadmenuindirect)成員函式也可以設定狀態 （已啟用，停用，或呈現暗灰色） 的功能表項目。  
  
 使用 MF_BYPOSITION 值需要應用程式使用正確`CMenu`。 如果`CMenu`的功能表列，則受影響的最上層功能表項目 （功能表列中的項目）。 若要設定的位置快顯畫面或巢狀快顯功能表項目的狀態，應用程式必須指定`CMenu`的快顯功能表。  
  
 當應用程式指定 MF_BYCOMMAND 旗標時，Windows 會檢查所有從屬的快顯功能表項目`CMenu`; 因此，除非有重複的功能表項目，使用`CMenu`的功能表列已足夠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]  
  
##  <a name="fromhandle"></a>  CMenu::FromHandle  
 將指標傳回至`CMenu`給功能表中的 Windows 控制代碼的物件。  
  
```  
static CMenu* PASCAL FromHandle(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 *hMenu*  
 功能表 Windows 控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CMenu`這可能是暫時性或永久性。  
  
### <a name="remarks"></a>備註  
 如果`CMenu`物件尚未附加至 Windows 功能表物件，暫時`CMenu`建立物件並將其連結。  
  
 此暫存`CMenu`物件只適用於應用程式必須在其事件迴圈，此時會刪除所有暫存物件中的閒置時間的下一次。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="getdefaultitem"></a>  CMenu::GetDefaultItem  
 判斷指定的功能表的預設功能表項目。  
  
```  
UINT GetDefaultItem(
    UINT gmdiFlags,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *gmdiFlags*  
 值，指定函式如何搜尋功能表項目。 這個參數可以是 none、 一個或下值的組合：  
  
|值|意義|  
|-----------|-------------|  
|GMDI_GOINTOPOPUPS|指定，是否開啟子功能表的其中一個預設項目，函式是在對應的子功能表以遞迴方式搜尋。 如果子功能表會不有任何預設項目，則傳回的值會識別開啟子功能表項目。<br /><br /> 根據預設，函式會傳回第一個預設項目上指定的功能表上，而不論其是否開啟子功能表項目。|  
|GMDI_USEDISABLED|指定函式會傳回預設的項目，即使它已停用。<br /><br /> 根據預設，此函式會略過已停用或灰色項目。|  
  
 *fByPos*  
 值，指定是否要擷取功能表項目的識別項或其位置。 如果此參數為 FALSE，則會傳回識別碼。 否則，傳回的位置。  
  
### <a name="return-value"></a>傳回值  
 如果此函數成功，則傳回的值會是識別碼或功能表項目的位置。 如果函式失敗，傳回的值為-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 函式行為[GetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-getmenudefaultitem)、 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenucontexthelpid"></a>  CMenu::GetMenuContextHelpId  
 擷取識別碼相關聯的內容說明`CMenu`。  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 與目前關聯識別碼的內容說明`CMenu`如果有的話，否則為零。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenuinfo"></a>  CMenu::GetMenuInfo  
 擷取功能表的資訊。  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>參數  
 *lpcmi*  
 指標[MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo)結構包含功能表的資訊。  
  
### <a name="return-value"></a>傳回值  
 值，如果函式成功，傳回的值為非零值;否則，傳回的值為零。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來擷取功能表的相關資訊。  
  
##  <a name="getmenuitemcount"></a>  CMenu::GetMenuItemCount  
 判斷在快顯畫面或最上層功能表中的項目數。  
  
```  
UINT GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，函式的功能表中的項目數否則為-1。  
  
### <a name="example"></a>範例  
  範例，請參閱[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)。  
  
##  <a name="getmenuitemid"></a>  CMenu::GetMenuItemID  
 取得功能表項目所定義的位置上的功能表項目識別項*nPos*。  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>參數  
 *nPos*  
 指定的位置 （以零為起始） 的功能表項目正在擷取其識別碼。  
  
### <a name="return-value"></a>傳回值  
 指定的項目，如果函式成功快顯功能表中項目識別碼。 如果指定的項目 （而不是快顯功能表中的項目） 的快顯功能表，則傳回的值為-1。 如果*nPos*對應分隔符號功能表項目，傳回的值為 0。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenuiteminfo"></a>  CMenu::GetMenuItemInfo  
 擷取功能表項目相關的資訊。  
  
```  
BOOL GetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *uItem*  
 識別項或功能表項目，以取得相關資訊的位置。 此參數的意義取決於值`ByPos`。  
  
 *lpMenuItemInfo*  
 指標[MENUITEMINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuiteminfoa)，如下所述，在 Windows SDK 中，包含功能表的相關資訊。  
  
 *fByPos*  
 值，指定的意義`nIDItem`。 根據預設，`ByPos`為 FALSE，表示該 uItem 是功能表項目識別項。 如果`ByPos`未設定為 FALSE，指出功能表項目位置。  
  
### <a name="return-value"></a>傳回值  
 如果此函數成功，傳回的值為非零值。 如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請使用 Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)、 Windows SDK 中所述。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的行為的 Win32 函式[GetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-getmenuiteminfoa)、 Windows SDK 中所述。 請注意，在 MFC 實作`GetMenuItemInfo`，請勿使用功能表的控制代碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]  
  
##  <a name="getmenustate"></a>  CMenu::GetMenuState  
 快顯功能表中，傳回指定的功能表項目或項目數目的狀態。  
  
```  
UINT GetMenuState(
    UINT nID,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>參數  
 *nID*  
 指定功能表項目識別碼，由*nFlags*。  
  
 *nFlags*  
 指定的本質*nID*。 它可以是下列值之一：  
  
- MF_BYCOMMAND 指定此參數可讓現有的功能表項目的命令識別碼。 這是預設值。  
  
- MF_BYPOSITION 指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。  
  
### <a name="return-value"></a>傳回值  
 值為 0xFFFFFFFF，如果指定的項目不存在。 如果*nId*識別快顯功能表中，高序位位元組包含快顯功能表中的項目數，而低序位位元組會包含相關聯的快顯功能表的功能表旗標。 否則傳回值就是遮罩 （布林值或） 下列清單中的值 (此遮罩描述狀態的功能表項目*nId*識別):  
  
- MF_CHECKED 是做為切換 MF_UNCHECKED 放置預設值與核取記號項目旁。 當應用程式會提供核取記號點陣圖 (請參閱`SetMenuItemBitmaps`成員函式)，會顯示"上的核取記號"點陣圖。  
  
- MF_DISABLED 停用功能表項目，使它無法選取，但不會變暗。  
  
- MF_ENABLED，使其選取，並將它還原從其呈現暗灰色的狀態，可讓功能表項目。 請注意，這個常數的值是 0;使用這個值時，應用程式應該不會針對 0 失敗的測試。  
  
- 無法選取，使其變暗它 MF_GRAYED 會停用功能表項目。  
  
- MF_MENUBARBREAK 置於新行在靜態功能表中，或在新的資料行，在快顯功能表中的項目。 新的快顯功能表欄會隔開垂直分隔線的舊的資料行。  
  
- MF_MENUBREAK 置於新行在靜態功能表中，或在新的資料行，在快顯功能表中的項目。 資料行之間，位於沒有分隔線。  
  
- MF_SEPARATOR 繪製水平分隔線。 只有在快顯功能表中使用。 無法呈現暗灰色，停用，或反白顯示這一行。 會忽略其他參數。  
  
- 將做為切換 MF_UNCHECKED 與 MF_CHECKED 移除項目旁的核取記號。 當應用程式會提供核取記號點陣圖 (請參閱`SetMenuItemBitmaps`成員函式)，會顯示 「 關閉的核取記號"點陣圖。 請注意，這個常數的值是 0;使用這個值時，應用程式應該不會針對 0 失敗的測試。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]  
  
##  <a name="getmenustring"></a>  CMenu::GetMenuString  
 將指定的功能表項目的標籤複製到指定的緩衝區中。  
  
```  
int GetMenuString(
    UINT nIDItem,  
    LPTSTR lpString,  
    int nMaxCount,  
    UINT nFlags) const;  
  
int GetMenuString(
    UINT nIDItem,  
    CString& rString,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>參數  
 *nIDItem*  
 在功能表中，根據的值指定整數識別項的功能表項目或功能表項目的位移*nFlags*。  
  
 *lpString*  
 要接收的標籤緩衝區的指標。  
  
 *rString*  
 參考`CString`接收複製的功能表字串的物件。  
  
 *nMaxCount*  
 指定要複製的標籤的最大長度 （以字元為單位）。 如果標籤是超過中指定的最大*nMaxCount*，額外的字元會被截斷。  
  
 *nFlags*  
 指定解譯*nIDItem*參數。 它可以是下列值之一：  
  
|nFlags|NIDItem 的解譯|  
|------------|-------------------------------|  
|MF_BYCOMMAND|指定此參數可讓現有的功能表項目的命令識別碼。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 都不設定，這是預設值。|  
|MF_BYPOSITION|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
### <a name="return-value"></a>傳回值  
 指定實際的複製到緩衝區，不包括 null 結束字元的字元數。  
  
### <a name="remarks"></a>備註  
 *NMaxCount*參數應該是大於在標籤中，以容納終止字串的 null 字元的字元數的其中一個。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getsafehmenu"></a>  CMenu::GetSafeHmenu  
 傳回由此包裝 HMENU`CMenu`物件或 NULL`CMenu`指標。  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::LoadMenu](#loadmenu)。  
  
##  <a name="getsubmenu"></a>  CMenu::GetSubMenu  
 擷取`CMenu`快顯功能表的物件。  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>參數  
 *nPos*  
 指定包含功能表中的快顯功能表的位置。 位置值開始的第一個功能表項目為 0。 快顯功能表識別碼不能在此函式。  
  
### <a name="return-value"></a>傳回值  
 指標`CMenu`物件，其`m_hMenu`成員包含快顯功能表的控制代碼，如果快顯功能表中指定的位置; 否則為 NULL。 如果`CMenu`物件不存在，則會建立一個暫時。 `CMenu`應該不會儲存傳回的指標。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::TrackPopupMenu](#trackpopupmenu)。  
  
##  <a name="insertmenu"></a>  CMenu::InsertMenu  
 在所指定的位置插入新的功能表項目*只有*並且向下移的功能表中的其他項目。  
  
```  
BOOL InsertMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL InsertMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>參數  
 *只有*  
 指定功能表項目是插入新的功能表項目之前。 *NFlags*參數可以用來解譯*只有*如下：  
  
|nFlags|只有的解譯|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定此參數可讓現有的功能表項目的命令識別碼。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 都不設定，這是預設值。|  
|MF_BYPOSITION|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。 如果*只有*為-1，新的功能表項目會附加至功能表的尾端。|  
  
 *nFlags*  
 指定如何*只有*解譯，並指定新的功能表項目的狀態的相關資訊加入至功能表時。 如需可設定的旗標的清單，請參閱 < [AppendMenu](#appendmenu)成員函式。 若要指定多個值，請使用位元的 OR 運算子結合了 MF_BYCOMMAND 或 MF_BYPOSITION 旗標。  
  
 *nIDNewItem*  
 指定命令識別碼的新功能表項目或者，如果*nFlags*設 MF_POPUP，快顯功能表的功能表控制代碼 (HMENU)。 *NIDNewItem*參數會忽略 （不需要），如果*nFlags*設 MF_SEPARATOR。  
  
 *lpszNewItem*  
 指定新的功能表項目的內容。 *nFlags*可用來解譯*lpszNewItem*如下：  
  
|nFlags|LpszNewItem 的解譯|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|包含應用程式所提供的 32 位元值，應用程式可用來維護功能表項目相關聯的其他資料。 這個 32 位元值是在應用程式可用`itemData`所提供的結構成員[WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem)並[WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem)訊息。 功能表項目最初顯示或變更時，會傳送這些訊息。|  
|MF_STRING|包含以 null 終止的字串的長指標。 這是預設解譯。|  
|MF_SEPARATOR|*LpszNewItem*參數會被忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`用作功能表項目中的物件。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式可以在程式中設定值，指定功能表項目的狀態*nFlags*。  
  
 每當在位於功能表視窗變更時 （不論是否顯示視窗），應用程式應該呼叫`CWnd::DrawMenuBar`。  
  
 當*nIDNewItem*指定的快顯功能表中，它會成為在其中插入 功能表的部分。 如果該功能表被終結時，[插入] 功能表也將被終結。 插入的功能表應該從已中斷連結`CMenu`物件，以避免衝突。  
  
 如果多個文件介面 (MDI) 子視窗最大化的作用中和的應用程式插入至 MDI 應用程式的功能表中呼叫此函式，並指定 MF_BYPOSITION 旗標，功能表快顯功能表插入遠比保留的一個位置預期的。 這是因為使用中的 MDI 子視窗的 [控制] 功能表會插入至 MDI 框架視窗的功能表列的第一個位置。 若要正確地定位 [] 功能表中，應用程式必須將 1 加入至可使用位置值。 應用程式可用來判斷是否有目前作用中的子視窗會最大化 WM_MDIGETACTIVE 訊息。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]  
  
##  <a name="insertmenuitem"></a>  CMenu::InsertMenuItem  
 在功能表中的指定位置中插入新的功能表項目。  
  
```  
BOOL InsertMenuItem(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *uItem*  
 請參閱說明*uItem*中[InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema) Windows SDK 中。  
  
 *lpMenuItemInfo*  
 請參閱說明*lpmii*在`InsertMenuItem`Windows SDK 中。  
  
 *fByPos*  
 請參閱說明*fByPosition*在`InsertMenuItem`Windows SDK 中。  
  
### <a name="remarks"></a>備註  
 此函式會包裝[InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema)、 Windows SDK 中所述。  
  
##  <a name="loadmenu"></a>  CMenu::LoadMenu  
 從應用程式的可執行檔載入功能表資源，並將它附加至`CMenu`物件。  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>參數  
 *lpszResourceName*  
 指向以 null 終止的字串，包含要載入功能表資源的名稱。  
  
 *nIDResource*  
 指定要載入功能表資源的功能表識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 載入功能表資源，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派至 視窗相關聯的功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="loadmenuindirect"></a>  CMenu::LoadMenuIndirect  
 從功能表中的範本的記憶體載入資源，並將它附加至`CMenu`物件。  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>參數  
 *lpMenuTemplate*  
 指向功能表範本 (也就是單一[MENUITEMTEMPLATEHEADER](/windows/desktop/api/winuser/ns-winuser-menuitemtemplateheader)結構以及一或多個集合[MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate)結構)。 如需有關這些兩個結構的詳細資訊，請參閱 Windows SDK。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 載入功能表資源，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表範本是後面接著一或多個集合的標頭[MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate)結構，每個都可能包含一或多個功能表項目和快顯功能表。  
  
 版本號碼應為 0。  
  
 `mtOption`旗標應包含 MF_END，快顯清單中的最後一個項目和主要的清單中的最後一個項目。 請參閱`AppendMenu`其他旗標的成員函式。 `mtId` MF_POPUP 中指定時，必須從 MENUITEMTEMPLATE 結構省略成員`mtOption`。  
  
 MENUITEMTEMPLATE 結構必須是不夠大，所配置的空間`mtString`包含功能表項目，以 null 終止字串的名稱。  
  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派至 視窗相關聯的功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="m_hmenu"></a>  CMenu::m_hMenu  
 指定附加至 [Windows] 功能表的 HMENU 控點`CMenu`物件。  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::LoadMenu](#loadmenu)。  
  
##  <a name="measureitem"></a>  CMenu::MeasureItem  
 建立具有主控描繪樣式的功能表時，由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpMeasureItemStruct*  
 指標`MEASUREITEMSTRUCT`結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，並填寫`MEASUREITEMSTRUCT`結構以通知 Windows 的 [] 功能表的維度。  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 下列程式碼是從 MFC [CTRLTEST](../../visual-cpp-samples.md)範例：  
  
 [!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]  
  
##  <a name="modifymenu"></a>  CMenu::ModifyMenu  
 變更現有的功能表項目所指定的位置*只有*。  
  
```  
BOOL ModifyMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL ModifyMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>參數  
 *只有*  
 指定要變更功能表項目。 *NFlags*參數可以用來解譯*只有*如下：  
  
|nFlags|只有的解譯|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定此參數可讓現有的功能表項目的命令識別碼。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 都不設定，這是預設值。|  
|MF_BYPOSITION|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
 *nFlags*  
 指定如何*只有*解譯，並提供對功能表項目所做變更的相關資訊。 如需可設定的旗標的清單，請參閱 < [AppendMenu](#appendmenu)成員函式。  
  
 *nIDNewItem*  
 指定已修改的功能表項目的其中一個命令識別碼或者，如果*nFlags*設 MF_POPUP，快顯功能表的功能表控制代碼 (HMENU)。 *NIDNewItem*參數會忽略 （不需要），如果*nFlags*設 MF_SEPARATOR。  
  
 *lpszNewItem*  
 指定新的功能表項目的內容。 *NFlags*參數可以用來解譯*lpszNewItem*如下：  
  
|nFlags|LpszNewItem 的解譯|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|包含應用程式所提供的 32 位元值，應用程式可用來維護功能表項目相關聯的其他資料。 它會處理 MF_MEASUREITEM 和 MF_DRAWITEM 時，可供應用程式這個 32 位元值。|  
|MF_STRING|包含的長指標以 null 終止的字串或`CString`。|  
|MF_SEPARATOR|*LpszNewItem*參數會被忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`用作功能表項目中的物件。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式設定中的值會指定新的功能表項目狀態*nFlags*。 如果此函式來取代快顯功能表的功能表項目相關聯，則它會終結舊的快顯功能表，並釋放快顯功能表所使用的記憶體。  
  
 當*nIDNewItem*指定的快顯功能表中，它會成為在其中插入 功能表的部分。 如果該功能表被終結時，[插入] 功能表也將被終結。 插入的功能表應該從已中斷連結`CMenu`物件，以避免衝突。  
  
 每當在位於功能表視窗變更時 （不論是否顯示視窗），應用程式應該呼叫`CWnd::DrawMenuBar`。 若要變更現有的功能表項目的屬性，它會更快速地使用`CheckMenuItem`和`EnableMenuItem`成員函式。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="operator_hmenu"></a>  CMenu::operator HMENU  
 若要擷取的控制代碼使用這個運算子`CMenu`物件。  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的控制代碼`CMenu`物件; 否則為 NULL。  
  
### <a name="remarks"></a>備註  
 您可以使用控制代碼來直接呼叫 Windows Api。  
  
##  <a name="operator_neq"></a>  CMenu::operator ！ =  
 判斷兩個功能表是否以邏輯方式不相等。  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>參數  
 *功能表*  
 A`CMenu`進行比較的物件。  
  
### <a name="remarks"></a>備註  
 在左側功能表物件是否不等於右邊的功能表物件的測試。  
  
##  <a name="operator_eq_eq"></a>  CMenu::operator = =  
 判斷兩個功能表是否在邏輯上相等。  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>參數  
 *功能表*  
 A`CMenu`進行比較的物件。  
  
### <a name="remarks"></a>備註  
 如果在左側的功能表物件的測試 （依據 HMENU 值） 等於右邊的功能表物件。  
  
##  <a name="removemenu"></a>  CMenu::RemoveMenu  
 從功能表中刪除相關聯的快顯功能表的功能表項目。  
  
```  
BOOL RemoveMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 *只有*  
 指定要移除功能表項目。 *NFlags*參數可以用來解譯*只有*如下：  
  
|nFlags|只有的解譯|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定此參數可讓現有的功能表項目的命令識別碼。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 都不設定，這是預設值。|  
|MF_BYPOSITION|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
 *nFlags*  
 指定如何*只有*解譯。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 它不會終結快顯功能表中的控制代碼以便之後可以重複使用的功能表。 應用程式可能會在之前呼叫這個函式，呼叫`GetSubMenu`成員函式來擷取快顯視窗`CMenu`供重複使用的物件。  
  
 每當在位於功能表視窗變更時 （不論是否顯示視窗），應用程式必須呼叫`CWnd::DrawMenuBar`。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setdefaultitem"></a>  CMenu::SetDefaultItem  
 設定指定的功能表的預設功能表項目。  
  
```  
BOOL SetDefaultItem(
    UINT uItem,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *uItem*  
 識別項或新的預設功能表項目或-1 表示沒有預設項目位置。 此參數的意義取決於 windows 7 *fByPos*。  
  
 *fByPos*  
 值，指定的意義*uItem*。 如果此參數為 FALSE 時， *uItem*是功能表項目識別碼。 否則，它是功能表項目位置。  
  
### <a name="return-value"></a>傳回值  
 如果此函數成功，傳回的值為非零值。 如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請使用 Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)、 Windows SDK 中所述。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 函式行為[SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem)、 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setmenucontexthelpid"></a>  CMenu::SetMenuContextHelpId  
 使用的內容說明識別碼相關聯`CMenu`。  
  
```  
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```  
  
### <a name="parameters"></a>參數  
 *dwContextHelpId*  
 內容說明識別碼相關聯`CMenu`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則便是 0  
  
### <a name="remarks"></a>備註  
 在功能表中的所有項目共用這個識別碼，不可能將說明內容識別碼附加至個別的功能表項目。  
  
### <a name="example"></a>範例  
  範例，請參閱[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setmenuinfo"></a>  CMenu::SetMenuInfo  
 設定功能表的資訊。  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>參數  
 *lpcmi*  
 指標[MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo)結構包含功能表的資訊。  
  
### <a name="return-value"></a>傳回值  
 值，如果函式成功，傳回的值為非零值;否則，傳回的值為零。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來設定功能表的特定資訊。  
  
##  <a name="setmenuitembitmaps"></a>  CMenu::SetMenuItemBitmaps  
 關聯的功能表項目中指定的點陣圖。  
  
```  
BOOL SetMenuItemBitmaps(
    UINT nPosition,  
    UINT nFlags,  
    const CBitmap* pBmpUnchecked,  
    const CBitmap* pBmpChecked);
```  
  
### <a name="parameters"></a>參數  
 *只有*  
 指定要變更功能表項目。 *NFlags*參數可以用來解譯*只有*如下：  
  
|nFlags|只有的解譯|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定此參數可讓現有的功能表項目的命令識別碼。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 都不設定，這是預設值。|  
|MF_BYPOSITION|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
 *nFlags*  
 指定如何*只有*解譯。  
  
 *pBmpUnchecked*  
 指定要功能表項目，則不會檢查所使用的點陣圖。  
  
 *pBmpChecked*  
 指定要檢查功能表項目所使用的點陣圖。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表項目是否已核取或取消核取，則 Windows 會顯示功能表項目旁適當的點陣圖。  
  
 如果有任一*pBmpUnchecked*或是*pBmpChecked*是 NULL，則 Windows 會顯示功能表項目對應屬性旁邊的任何內容。 如果這兩個參數都是 NULL，Windows 會使用預設核取記號，核取項目，並取消核取項目時，會移除核取記號。  
  
 功能表終結時，不會終結這些點陣圖;應用程式必須摧毀它們。  
  
 Windows`GetMenuCheckMarkDimensions`函式會擷取預設核取記號，用於功能表項目維度。 應用程式會使用這些值來決定適當的大小，此函式所提供的點陣圖。 取得大小，建立您的點陣圖，然後設定它們。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="setmenuiteminfo"></a>  CMenu::SetMenuItemInfo  
 變更功能表項目相關的資訊。  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *uItem*  
 請參閱說明*uItem*中[SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa) Windows SDK 中。  
  
 *lpMenuItemInfo*  
 請參閱說明*lpmii*在`SetMenuItemInfo`Windows SDK 中。  
  
 *fByPos*  
 請參閱說明*fByPosition*在`SetMenuItemInfo`Windows SDK 中。  
  
### <a name="remarks"></a>備註  
 此函式會包裝[SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa)、 Windows SDK 中所述。  
  
##  <a name="trackpopupmenu"></a>  CMenu::TrackPopupMenu  
 會浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。  
  
```  
BOOL TrackPopupMenu(
    UINT nFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPCRECT lpRect = 0);
```  
  
### <a name="parameters"></a>參數  
 *nFlags*  
 指定螢幕位置和滑鼠位置的旗標。 請參閱[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)取得一份可用的旗標。  
  
 *x*  
 指定螢幕座標中的快顯功能表的水平位置。 值而定*nFlags*參數，功能表可以是靠左對齊、 靠右對齊或置中相對於此位置。  
  
 *y*  
 在畫面上，指定功能表的頂端以螢幕座標的垂直位置。  
  
 *pWnd*  
 識別擁有快顯功能表的視窗。 這個參數不能是 NULL，，即使指定 TPM_NONOTIFY 旗標。 此視窗會收到所有的 WM_COMMAND 訊息，從功能表。 在 Windows 3.1 和更新版本的版本，視窗不會收到 WM_COMMAND 訊息，直到`TrackPopupMenu`傳回。 在 Windows 3.0 中，視窗會收到 WM_COMMAND 訊息之前`TrackPopupMenu`傳回。  
  
 *lpRect*  
 忽略。  
  
### <a name="return-value"></a>傳回值  
 這個方法會傳回呼叫的結果[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) Windows SDK 中。  
  
### <a name="remarks"></a>備註  
 浮動的快顯功能表可以出現在螢幕上的任何位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="trackpopupmenuex"></a>  CMenu::TrackPopupMenuEx  
 會浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。  
  
```  
BOOL TrackPopupMenuEx(
    UINT fuFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPTPMPARAMS lptpm);
```  
  
### <a name="parameters"></a>參數  
 *fuFlags*  
 指定不同的函式，如擴充的功能表。 如需所有值的清單和它們的意義，請參閱[TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex)。  
  
 *x*  
 指定螢幕座標中的快顯功能表的水平位置。  
  
 *y*  
 在畫面上，指定功能表的頂端以螢幕座標的垂直位置。  
  
 *pWnd*  
 視窗擁有快顯功能表，並從 [建立] 功能表中接收訊息的指標。 這個視窗可以是任何視窗，從目前的應用程式，但不能是 NULL。 如果您指定在 TPM_NONOTIFY *fuFlags*參數，此函式不會傳送任何訊息給*pWnd*。 函式必須傳回所指的視窗*pWnd*收到 WM_COMMAND 訊息。  
  
 *lptpm*  
 指標[產生 TPMPARAMS](/windows/desktop/api/winuser/ns-winuser-tagtpmparams)不應該重疊結構，指定功能表的螢幕區域。 這個參數可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 如果您指定在 TPM_RETURNCMD *fuFlags*參數，傳回的值是使用者選取項目的功能表項目識別碼。 如果使用者取消 [] 功能表中，而不需要進行選擇，或發生錯誤時，傳回的值為 0。  
  
 如果您未指定在 TPM_RETURNCMD *fuFlags*參數，傳回的值會是零，如果函式成功，0 失敗。 若要取得延伸錯誤資訊，請呼叫[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>備註  
 浮動的快顯功能表可以出現在螢幕上的任何位置。 如需有關如何建立快顯功能表時，處理錯誤的詳細資訊，請參閱 < [TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLTEST](../../visual-cpp-samples.md)   
 [MFC 範例 DYNAMENU](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)
