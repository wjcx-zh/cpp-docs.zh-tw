---
title: "CMenu 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- HMENU
- menus, class
- menus, base class
- menus, creating
- menus, managing
- CMenu class
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
caps.latest.revision: 22
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
ms.openlocfilehash: dcd353bf0be5d23c1782347f54b16a875ed190ed
ms.lasthandoff: 02/24/2017

---
# <a name="cmenu-class"></a>CMenu 類別
Windows `HMENU`的封裝。  
  
## <a name="syntax"></a>語法  
  
```  
class CMenu : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMenu::CMenu](#cmenu)|建構 `CMenu` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMenu::AppendMenu](#appendmenu)|將新的項目附加至這個功能表的結尾。|  
|[CMenu::Attach](#attach)|將附加的 Windows 功能表控制代碼`CMenu`物件。|  
|[CMenu::CheckMenuItem](#checkmenuitem)|將旁的核取記號，或從快顯功能表中功能表項目移除核取記號。|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|將功能表項目旁的選項按鈕，並移除所有其他功能表項目群組中選項按鈕。|  
|[CMenu::CreateMenu](#createmenu)|建立空的功能表，並將它附加`CMenu`物件。|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|建立空的快顯功能表，並將它附加`CMenu`物件。|  
|[CMenu::DeleteMenu](#deletemenu)|從功能表中刪除指定的項目。 如果功能表項目相關聯的快顯功能表上，終結快顯功能表上的控制代碼，並釋放它所使用的記憶體。|  
|[CMenu::DeleteTempMap](#deletetempmap)|刪除任何暫存`CMenu`所建立的物件`FromHandle`成員函式。|  
|[CMenu::DestroyMenu](#destroymenu)|會終結功能表附加至`CMenu`物件，並釋放功能表佔用的記憶體。|  
|[CMenu::Detach](#detach)|從 Windows 功能表處理常式會卸離`CMenu`物件，並傳回控制代碼。|  
|[CMenu::DrawItem](#drawitem)|當主控描繪功能表會變更的視覺外觀的架構所呼叫。|  
|[CMenu::EnableMenuItem](#enablemenuitem)|啟用、 停用，或變暗 （灰色） 的功能表項目。|  
|[CMenu::FromHandle](#fromhandle)|傳回的指標`CMenu`提供 Windows 功能表處理常式物件。|  
|[CMenu::GetDefaultItem](#getdefaultitem)|判斷指定的功能表的預設功能表項目。|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|擷取功能表相關聯的說明內容識別碼。|  
|[CMenu::GetMenuInfo](#getmenuinfo)|擷取特定的功能表上的資訊。|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|決定快顯或最上層功能表項目數目。|  
|[CMenu::GetMenuItemID](#getmenuitemid)|取得功能表項目位於指定位置處的功能表項目識別碼。|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|擷取功能表項目相關的資訊。|  
|[CMenu::GetMenuState](#getmenustate)|傳回指定的功能表項目或項目數目之狀態的快顯功能表中。|  
|[CMenu::GetMenuString](#getmenustring)|擷取指定的功能表項目的標籤。|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|傳回`m_hMenu`包裝此`CMenu`物件。|  
|[CMenu::GetSubMenu](#getsubmenu)|擷取快顯功能表上的指標。|  
|[CMenu::InsertMenu](#insertmenu)|將新的功能表項目插入位於指定位置，將其他項目移下的功能表。|  
|[CMenu::InsertMenuItem](#insertmenuitem)|在功能表中的指定位置處插入新的功能表項目。|  
|[CMenu::LoadMenu](#loadmenu)|從可執行檔載入功能表資源，並將它附加`CMenu`物件。|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|從功能表中的範本記憶體載入功能表，並將其以附加`CMenu`物件。|  
|[CMenu::MeasureItem](#measureitem)|若要判斷功能表維度時，會建立主控描繪功能表架構呼叫。|  
|[CMenu::ModifyMenu](#modifymenu)|變更現有的功能表項目指定的位置。|  
|[CMenu::RemoveMenu](#removemenu)|從指定的功能表中刪除具有相關聯的快顯功能表的功能表項目。|  
|[CMenu::SetDefaultItem](#setdefaultitem)|設定預設功能表項目中指定的功能表。|  
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|設定與功能表相關聯的說明內容識別碼。|  
|[CMenu::SetMenuInfo](#setmenuinfo)|設定特定的功能表上的資訊。|  
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|關聯功能表項目至指定的核取記號點陣圖。|  
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|變更功能表項目相關的資訊。|  
|[CMenu::TrackPopupMenu](#trackpopupmenu)|浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。|  
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|擷取功能表物件的控制代碼。|  
|[CMenu::operator ！ =](#operator_neq)|判斷兩個功能表物件是否不相等。|  
|[CMenu::operator = =](#operator_eq_eq)|判斷兩個功能表物件是否相等。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|指定要附加至 [視窗] 功能表的控制代碼`CMenu`物件。|  
  
## <a name="remarks"></a>備註  
 它提供建立、 追蹤、 更新和終結功能表成員函式。  
  
 建立`CMenu`物件上以本機的堆疊框架，然後呼叫`CMenu`的操作新的功能表上，視成員函式。 接下來，呼叫[CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu)設定功能表視窗，後面緊接著呼叫`CMenu`物件的[卸離](#detach)成員函式。 `CWnd::SetMenu`成員函式到新的功能表設定視窗的功能表，會造成視窗重新繪製，以反映變更的功能表，並傳遞至視窗功能表的擁有權。 若要呼叫**卸離**卸離`HMENU`從`CMenu`物件，因此，當本機`CMenu`變數超出範圍，`CMenu`物件解構函式不會嘗試終結不再擁有的功能表。 當視窗終結時，即會自動終結本身的功能表。  
  
 您可以使用[LoadMenuIndirect](#loadmenuindirect)成員函式來建立範本，以在記憶體中，從功能表但功能表，從資源建立呼叫[LoadMenu](#loadmenu)更容易維護，還可以建立和修改功能表編輯器的功能表資源本身。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="appendmenu"></a>CMenu::AppendMenu  
 將新的項目附加至結尾的功能表。  
  
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
 `nFlags`  
 加入至功能表時，請指定新的功能表項目的狀態資訊。 它包含一或多個 「 備註 」 一節中所列的值。  
  
 `nIDNewItem`  
 指定命令識別碼的新功能表項目或者，如果`nFlags`設為**MF_POPUP**，功能表控制代碼 ( `HMENU`) 的快顯功能表。 `nIDNewItem`參數已忽略 （不需要），如果`nFlags`設為**MF_SEPARATOR**。  
  
 `lpszNewItem`  
 指定新的功能表項目的內容。 `nFlags`參數用來解譯`lpszNewItem`方式如下︰  
  
|nFlags|LpszNewItem 的解譯|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|包含應用程式所提供的 32 位元值，應用程式可用來維護其他功能表項目相關聯的資料。 這個 32 位元值會提供給應用程式在處理時`WM_MEASUREITEM`和`WM_DRAWITEM`訊息。 值會儲存在**itemData**的這些訊息所提供的結構成員。|  
|**MF_STRING**|包含以 null 結束之字串的指標。 這是預設解譯。|  
|**MF_SEPARATOR**|`lpszNewItem`參數已忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`物件，做為功能表項目。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式可以在程式中設定值，指定功能表項目的狀態`nFlags`。 當`nIDNewItem`指定快顯功能表上，它會附加的功能表的一部份。 如果該功能表損毀，也會終結附加的功能表。 附加的功能表應該會中斷`CMenu`物件，以避免衝突。 請注意， **MF_STRING**和`MF_OWNERDRAW`不是有效的點陣圖版本`AppendMenu`。  
  
 下列清單描述可能會在設定的旗標`nFlags`:  
  
- **MF_CHECKED**作為與切換開關**MF_UNCHECKED**加上預設核取記號，項目旁。 當應用程式提供核取記號點陣圖 (請參閱[SetMenuItemBitmaps](#setmenuitembitmaps)成員函式)，會顯示"上的核取記號 」 的點陣圖。  
  
- **MF_UNCHECKED**作為與切換開關**MF_CHECKED**移除項目旁的核取記號。 當應用程式提供核取記號點陣圖 (請參閱`SetMenuItemBitmaps`成員函式)，會顯示 「 核取記號關閉 「 點陣圖。  
  
- **MF_DISABLED**停用功能表項目，使其不選取，但不會變暗。  
  
- `MF_ENABLED`您可以選取，使其還原從呈現暗灰色的狀態，可讓功能表項目。  
  
- **MF_GRAYED**停用功能表項目，使它無法加以選取，而且它變暗。  
  
- **MF_MENUBARBREAK**在靜態功能表或快顯功能表中的新資料行中的新行上放置項目。 以垂直分隔線，將會從舊的資料行分隔新快顯功能表上的資料行。  
  
- **MF_MENUBREAK**在靜態功能表或快顯功能表中的新資料行中的新行上放置項目。 任何分隔線不會在資料行之間。  
  
- `MF_OWNERDRAW`指定的項目是主控描繪項目。 擁有功能表的視窗 功能表上的第一次顯示時，接收`WM_MEASUREITEM`訊息，它會擷取的高度和寬度的功能表項目。 `WM_DRAWITEM`訊息是傳送只要擁有者必須更新視覺外觀的功能表項目。 這個選項不正確的最上層功能表項目。  
  
- **MF_POPUP**指定功能表項目都有與其相關聯的快顯功能表。 ID 參數指定要與項目相關聯的快顯功能表的控制代碼。 這用於最上層的快顯功能表或階層式的快顯功能表加入快顯功能表項目。  
  
- **MF_SEPARATOR**繪製水平分隔線。 只有在快顯功能表中使用。 這一行無法呈現暗灰色，停用，或反白顯示。 會忽略其他參數。  
  
- **MF_STRING**指定功能表項目是字元字串。  
  
 下列群組的每個列出旗標互斥，且不能同時使用︰  
  
- **MF_DISABLED**， `MF_ENABLED`，和**MF_GRAYED**  
  
- **MF_STRING**， `MF_OWNERDRAW`， **MF_SEPARATOR**，和點陣圖版本  
  
- **MF_MENUBARBREAK**和**MF_MENUBREAK**  
  
- **MF_CHECKED**和**MF_UNCHECKED**  
  
 每當 功能表上，位於視窗變更時 （無論顯示在視窗），應用程式應該呼叫[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="attach"></a>CMenu::Attach  
 附加至現有的 Windows 功能表`CMenu`物件。  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 `hMenu`  
 指定 Windows 功能表上的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 應該不會呼叫此函式，如果功能表尚未附加至`CMenu`物件。 功能表控制代碼儲存在`m_hMenu`資料成員。  
  
 如果您想要處理的功能表已與視窗相關聯，您可以使用[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)函式可取得功能表的控制代碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&21;](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="checkmenuitem"></a>CMenu::CheckMenuItem  
 加入核取記號以或從快顯功能表中功能表項目移除核取記號。  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>參數  
 `nIDCheckItem`  
 指定要檢查的功能表項目，由`nCheck`。  
  
 `nCheck`  
 指定如何檢查功能表項目以及如何判斷功能表項目的位置。 `nCheck`參數可以是項目的組合**MF_CHECKED**或**MF_UNCHECKED**與**MF_BYPOSITION**或**MF_BYCOMMAND**旗標。 使用位元 OR 運算子，可以結合這些旗標。 它們具有下列意義︰  
  
- **MF_BYCOMMAND**指定此參數可讓現有的功能表項目的命令 ID。 這是預設值。  
  
- **MF_BYPOSITION**指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。  
  
- **MF_CHECKED**作為與切換開關**MF_UNCHECKED**加上預設核取記號，項目旁。  
  
- **MF_UNCHECKED**作為與切換開關**MF_CHECKED**移除項目旁的核取記號。  
  
### <a name="return-value"></a>傳回值  
 先前的狀態項目︰ **MF_CHECKED**或**MF_UNCHECKED**，或 0xFFFFFFFF 如果功能表項目不存在。  
  
### <a name="remarks"></a>備註  
 `nIDCheckItem`參數會指定要修改的項目。  
  
 `nIDCheckItem`參數可識別快顯功能表項目，以及功能表項目。 若要檢查的快顯功能表項目，不需要任何特殊步驟。 您無法選取最上層功能表項目。 快顯功能表項目必須核取的位置，因為它並沒有與其相關聯的功能表項目識別碼。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::GetMenuState](#getmenustate)。  
  
##  <a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem  
 會檢查指定的功能表項目，並使其選項項目。  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 `nIDFirst`  
 指定 (做為識別碼或位移值而定`nFlags`) 的選項按鈕群組的第一個功能表項目。  
  
 `nIDLast`  
 指定 (做為識別碼或位移值而定`nFlags`) 的選項按鈕群組的最後一個功能表項目。  
  
 `nIDItem`  
 指定 (做為識別碼或位移值而定`nFlags`) 將會檢查使用選項按鈕群組中的項目。  
  
 `nFlags`  
 指定的解譯`nIDFirst`， `nIDLast`，和`nIDItem`方式如下︰  
  
|nFlags|解譯|  
|------------|--------------------|  
|**MF_BYCOMMAND**|指定此參數可讓現有的功能表項目的命令 ID。 這是預設值，如果沒有**MF_BYCOMMAND**或**MF_BYPOSITION**設定。|  
|**MF_BYPOSITION**|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0  
  
### <a name="remarks"></a>備註  
 在此同時，函式會取消選取相關聯的群組中所有其他功能表項目，並清除選項項目型別旗標，這些項目的。 已檢查的項目會顯示使用選項按鈕 （或項目符號） 點陣圖，而不核取記號點陣圖。  
  
### <a name="example"></a>範例  
  請參閱範例[ON_COMMAND_RANGE](http://msdn.microsoft.com/library/c52719fc-dd6e-48c9-af79-383f48d608e0)。  
  
##  <a name="cmenu"></a>CMenu::CMenu  
 建立空的功能表，並將它附加`CMenu`物件。  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>備註  
 您呼叫其中一個的建立或載入成員函式之前，不會建立功能表**CMenu:**  
  
- [CreateMenu](#createmenu)  
  
- [CreatePopupMenu](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [Attach](#attach)  
  
##  <a name="createmenu"></a>CMenu::CreateMenu  
 會建立一個功能表，並將它附加`CMenu`物件。  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功; 建立功能表否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表最初是空的。 功能表項目可以藉由加入`AppendMenu`或`InsertMenu`成員函式。  
  
 如果功能表指派給視窗，它即會自動終結視窗終結時。  
  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派給視窗相關聯的功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&22;](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="createpopupmenu"></a>CMenu::CreatePopupMenu  
 建立快顯功能表，並將它附加`CMenu`物件。  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立快顯功能表。否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表最初是空的。 功能表項目可以藉由加入`AppendMenu`或`InsertMenu`成員函式。 應用程式可以加入現有的功能表或快顯功能表上的快顯功能表。 `TrackPopupMenu`可能使用成員函式，這個功能表顯示為浮動的快顯功能表，並追蹤在快顯功能表選取項目。  
  
 如果功能表指派給視窗，它即會自動終結視窗終結時。 如果功能表會加入至現有的功能表中，會自動終結終結該功能表時。  
  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派給視窗相關聯的快顯功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="deletemenu"></a>CMenu::DeleteMenu  
 從功能表中刪除項目。  
  
```  
BOOL DeleteMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 `nPosition`  
 指定的功能表項目會被刪除，由`nFlags`。  
  
 `nFlags`  
 用來解譯`nPosition`方式如下︰  
  
|nFlags|NPosition 的解譯|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|指定此參數可讓現有的功能表項目的命令 ID。 這是預設值，如果沒有**MF_BYCOMMAND**或**MF_BYPOSITION**設定。|  
|**MF_BYPOSITION**|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果功能表項目相關聯的快顯功能表上，`DeleteMenu`終結快顯功能表上的控制代碼，並釋放快顯功能表上所使用的記憶體。  
  
 每當 功能表上，位於視窗變更時 （無論顯示在視窗），應用程式必須呼叫[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。  
  
### <a name="example"></a>範例  
  請參閱範例[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)。  
  
##  <a name="deletetempmap"></a>CMenu::DeleteTempMap  
 自動呼叫`CWinApp`閒置時間處理常式中，刪除任何暫存`CMenu`所建立的物件[FromHandle](#fromhandle)成員函式。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>備註  
 `DeleteTempMap`中斷連結附加到暫存的 Windows 功能表物件`CMenu`物件，然後再刪除`CMenu`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&23;](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="destroymenu"></a>CMenu::DestroyMenu  
 終結功能表和所使用的任何 Windows 資源。  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果功能表損毀。否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表中斷`CMenu`物件終結之前。 Windows`DestroyMenu`函式會自動呼叫`CMenu`解構函式。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="detach"></a>CMenu::Detach  
 從 [視窗] 功能表會卸離`CMenu`物件，並傳回控制代碼。  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>傳回值  
 類型的控制代碼`HMENU`，以 Windows 功能表上，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 `m_hMenu`資料成員設定為**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&21;](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="drawitem"></a>CMenu::DrawItem  
 當主控描繪功能表會變更的視覺外觀的架構所呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 `itemAction`成員`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 覆寫此成員函式實作繪圖的主控描繪`CMenu`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前終止此成員函式。  
  
 請參閱[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)的說明`DRAWITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 下列程式碼是從 MFC [CTRLTEST](../../visual-cpp-samples.md)範例︰  
  
 [!code-cpp[NVC_MFCWindowing #&24;](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]  
  
##  <a name="enablemenuitem"></a>CMenu::EnableMenuItem  
 啟用、 停用，或變暗的功能表項目。  
  
```  
UINT EnableMenuItem(
    UINT nIDEnableItem,  
    UINT nEnable);
```  
  
### <a name="parameters"></a>參數  
 *nIDEnableItem*  
 指定要啟用功能表項目，由`nEnable`。 這個參數可以指定的快顯功能表項目，以及標準功能表項目。  
  
 `nEnable`  
 指定要採取的動作。 它可以是項目的組合**MF_DISABLED**， `MF_ENABLED`，或**MF_GRAYED**，與**MF_BYCOMMAND**或**MF_BYPOSITION**。 使用位元 OR 運算子，可以結合這些值。 這些值具有下列意義︰  
  
- **MF_BYCOMMAND**指定此參數可讓現有的功能表項目的命令 ID。 這是預設值。  
  
- **MF_BYPOSITION**指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。  
  
- **MF_DISABLED**停用功能表項目，使其不選取，但不會變暗。  
  
- `MF_ENABLED`您可以選取，使其還原從呈現暗灰色的狀態，可讓功能表項目。  
  
- **MF_GRAYED**停用功能表項目，使它無法加以選取，而且它變暗。  
  
### <a name="return-value"></a>傳回值  
 先前的狀態 ( **MF_DISABLED**， `MF_ENABLED`，或**MF_GRAYED**) 則為 –&1;，如果不正確。  
  
### <a name="remarks"></a>備註  
 [CreateMenu](#createmenu)， [InsertMenu](#insertmenu)， [ModifyMenu](#modifymenu)，和[LoadMenuIndirect](#loadmenuindirect)成員函式也可以設定的狀態 （啟用、 停用，或呈現暗灰色） 的功能表項目。  
  
 使用**MF_BYPOSITION**值需要應用程式使用的正確`CMenu`。 如果`CMenu`的功能表列，則受影響的最上層功能表項目 （在功能表列中的項目）。 若要設定的項目狀態的位置快顯或巢狀快顯功能表中，應用程式必須指定`CMenu`的快顯功能表。  
  
 應用程式時指定**MF_BYCOMMAND**旗標，Windows 會檢查所有的快顯功能表項目屬於`CMenu`; 因此，除非有重複的功能表項目，否則使用`CMenu`的功能表列已足夠。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&25;](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CMenu::FromHandle  
 傳回的指標`CMenu`功能表提供的 Windows 控制代碼的物件。  
  
```  
static CMenu* PASCAL FromHandle(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 `hMenu`  
 功能表 Windows 控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CMenu`，可能是暫時性或永久性。  
  
### <a name="remarks"></a>備註  
 如果`CMenu`物件尚未附加至 Windows 功能表物件，暫時`CMenu`會建立並附加物件。  
  
 此暫存`CMenu`物件只適用於應用程式有閒置時間的事件在迴圈中，此時就會刪除所有暫存物件至下一次。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="getdefaultitem"></a>CMenu::GetDefaultItem  
 判斷指定的功能表的預設功能表項目。  
  
```  
UINT GetDefaultItem(
    UINT gmdiFlags,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *gmdiFlags*  
 值，指定函式如何搜尋功能表項目。 這個參數可以是無、 一個或下值的組合︰  
  
|值|意義|  
|-----------|-------------|  
|**GMDI_GOINTOPOPUPS**|指定是否預設的項目後，開啟子功能表，函式可在對應的子功能表以遞迴方式搜尋。 如果子功能表具有預設的項目，則傳回值會識別開啟子功能表項目。<br /><br /> 根據預設，函數會傳回第一個預設項目在指定的功能表上，而不論其是否開啟子功能表項目。|  
|**GMDI_USEDISABLED**|指定函式會傳回預設的項目，即使已停用。<br /><br /> 根據預設，此函式會略過停用或灰色的項目。|  
  
 `fByPos`  
 值，指定是否要擷取功能表項目的識別項或其位置。 如果這個參數是**FALSE**，此識別碼會傳回。 否則，傳回的位置。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，傳回的值是識別碼或功能表項目的位置。 如果函式失敗，傳回值為-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 函式的行為[GetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647976)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId  
 擷取識別碼相關聯的內容說明`CMenu`。  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 識別碼目前與相關聯的內容說明`CMenu`若有的話，否則為零。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenuinfo"></a>CMenu::GetMenuInfo  
 擷取功能表的資訊。  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpcmi`  
 指標[MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575)結構包含功能表的資訊。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，傳回值為非零值;否則，傳回值為零。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來擷取功能表的相關資訊。  
  
##  <a name="getmenuitemcount"></a>CMenu::GetMenuItemCount  
 決定快顯或最上層功能表項目數目。  
  
```  
UINT GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則功能表項目的數目否則為-1。  
  
### <a name="example"></a>範例  
  請參閱範例[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)。  
  
##  <a name="getmenuitemid"></a>CMenu::GetMenuItemID  
 取得功能表項目所定義的位置上的功能表項目識別碼`nPos`。  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 指定的位置 （以零為起始） 的功能表項目正在擷取其識別碼。  
  
### <a name="return-value"></a>傳回值  
 指定的項目，如果函式成功的快顯功能表中的項目識別碼。 如果指定的項目 （而不是快顯功能表中的項目） 的快顯功能表上，則傳回值為 –&1;。 如果`nPos`對應至**分隔符號**功能表項目，則傳回值為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo  
 擷取功能表項目相關的資訊。  
  
```  
BOOL GetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `uItem`  
 識別項或要取得相關資訊之功能表項目的位置。 這個參數的意義取決於值`ByPos`。  
  
 `lpMenuItemInfo`  
 指標[MENUITEMINFO](http://msdn.microsoft.com/library/windows/desktop/ms647578)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，其中包含功能表的相關資訊。  
  
 `fByPos`  
 值，指定的意義`nIDItem`。 根據預設，`ByPos`是**FALSE**，表示該 uItem 是功能表項目識別項。 如果`ByPos`未設定為**FALSE**，表示功能表項目位置。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，傳回的值不是零。 如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，使用 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的行為的 Win32 函式[GetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms647980)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 請注意，在 MFC 實作`GetMenuItemInfo`，請勿使用 功能表上的控制代碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&26;](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]  
  
##  <a name="getmenustate"></a>CMenu::GetMenuState  
 傳回指定的功能表項目或項目數目之狀態的快顯功能表中。  
  
```  
UINT GetMenuState(
    UINT nID,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 指定功能表項目識別碼，由`nFlags`。  
  
 `nFlags`  
 指定的本質`nID`。 它可以是下列值之一︰  
  
- **MF_BYCOMMAND**指定此參數可讓現有的功能表項目的命令 ID。 這是預設值。  
  
- **MF_BYPOSITION**指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。  
  
### <a name="return-value"></a>傳回值  
 值為 0xFFFFFFFF，如果指定的項目不存在。 如果*nId*識別快顯功能表上，高序位位元組包含快顯功能表中的項目數，而低序位位元組包含相關聯的快顯功能表的功能表旗標。 否則傳回值是下列清單中的值 （布林值 OR) 的遮罩 (這個遮罩描述狀態的功能表項目*nId*識別):  
  
- **MF_CHECKED**作為與切換開關**MF_UNCHECKED**加上預設核取記號，項目旁。 當應用程式提供核取記號點陣圖 (請參閱`SetMenuItemBitmaps`成員函式)，會顯示"上的核取記號 」 的點陣圖。  
  
- **MF_DISABLED**停用功能表項目，使其不選取，但不會變暗。  
  
- `MF_ENABLED`您可以選取，使其還原從呈現暗灰色的狀態，可讓功能表項目。 請注意，這個常數的值是 0;使用此值時，應用程式應該不會針對失敗的 0 測試。  
  
- **MF_GRAYED**停用功能表項目，使它無法加以選取，而且它變暗。  
  
- **MF_MENUBARBREAK**在靜態功能表或快顯功能表中的新資料行中的新行上放置項目。 以垂直分隔線，將會從舊的資料行分隔新快顯功能表上的資料行。  
  
- **MF_MENUBREAK**在靜態功能表或快顯功能表中的新資料行中的新行上放置項目。 任何分隔線不會在資料行之間。  
  
- **MF_SEPARATOR**繪製水平分隔線。 只有在快顯功能表中使用。 這一行無法呈現暗灰色，停用，或反白顯示。 會忽略其他參數。  
  
- **MF_UNCHECKED**作為與切換開關**MF_CHECKED**移除項目旁的核取記號。 當應用程式提供核取記號點陣圖 (請參閱`SetMenuItemBitmaps`成員函式)，會顯示 「 核取記號關閉 「 點陣圖。 請注意，這個常數的值是 0;使用此值時，應用程式應該不會針對失敗的 0 測試。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&27;](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]  
  
##  <a name="getmenustring"></a>CMenu::GetMenuString  
 將指定的功能表項目的標籤複製到指定的緩衝區。  
  
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
 `nIDItem`  
 在功能表中，根據的值指定整數識別項的功能表項目或功能表項目的位移`nFlags`。  
  
 `lpString`  
 要接收的標籤緩衝區的指標。  
  
 `rString`  
 參考`CString`要接收複製的功能表字串的物件。  
  
 `nMaxCount`  
 指定要複製的標籤的最大長度 （以字元為單位）。 如果標籤中指定的最大值大於`nMaxCount`，額外的字元會被截斷。  
  
 `nFlags`  
 指定的解譯`nIDItem`參數。 它可以是下列值之一︰  
  
|nFlags|NIDItem 的解譯|  
|------------|-------------------------------|  
|**MF_BYCOMMAND**|指定此參數可讓現有的功能表項目的命令 ID。 這是預設值，如果沒有**MF_BYCOMMAND**或**MF_BYPOSITION**設定。|  
|**MF_BYPOSITION**|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
### <a name="return-value"></a>傳回值  
 指定實際的複製到緩衝區，不包括 null 結束字元的字元數。  
  
### <a name="remarks"></a>備註  
 `nMaxCount`參數應該大於容納 null 字元結束的字串，將標籤中的字元數。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getsafehmenu"></a>CMenu::GetSafeHmenu  
 傳回`HMENU`包裝此`CMenu`物件，或**NULL** `CMenu`指標。  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::LoadMenu](#loadmenu)。  
  
##  <a name="getsubmenu"></a>CMenu::GetSubMenu  
 擷取`CMenu`快顯功能表上的物件。  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 指定的快顯功能表的功能表中所包含的位置。 位置的值從 0，第一個功能表項目。 快顯功能表上的識別項不能在這個函式。  
  
### <a name="return-value"></a>傳回值  
 指標`CMenu`物件，其`m_hMenu`成員包含快顯功能表上的控制代碼，如果快顯功能表上的指定位置中; 否則**NULL**。 如果`CMenu`物件不存在，則會建立一個暫時。 `CMenu`不應儲存傳回的指標。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::TrackPopupMenu](#trackpopupmenu)。  
  
##  <a name="insertmenu"></a>CMenu::InsertMenu  
 在所指定的位置插入新的功能表項目`nPosition`並將其他項目移至下的功能表。  
  
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
 `nPosition`  
 指定新的功能表項目是要插入的功能表項目。 `nFlags`參數可以用來解譯`nPosition`如下︰  
  
|nFlags|NPosition 的解譯|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|指定此參數可讓現有的功能表項目的命令 ID。 這是預設值，如果沒有**MF_BYCOMMAND**或**MF_BYPOSITION**設定。|  
|**MF_BYPOSITION**|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。 如果`nPosition`為 –&1;，新的功能表項目會附加至 功能表的結束。|  
  
 `nFlags`  
 指定如何`nPosition`解譯，並指定新的功能表項目的狀態的相關資訊加入至功能表時。 如需可能設定的旗標的清單，請參閱[AppendMenu](#appendmenu)成員函式。 若要指定多個值，使用位元 OR 運算子結合它們與**MF_BYCOMMAND**或**MF_BYPOSITION**旗標。  
  
 `nIDNewItem`  
 指定命令識別碼的新功能表項目或者，如果`nFlags`設為**MF_POPUP**，功能表控制代碼 ( `HMENU`) 的快顯功能表。 `nIDNewItem`參數已忽略 （不需要），如果`nFlags`設為**MF_SEPARATOR**。  
  
 `lpszNewItem`  
 指定新的功能表項目的內容。 `nFlags`可以用來解譯`lpszNewItem`如下︰  
  
|nFlags|LpszNewItem 的解譯|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|包含應用程式所提供的 32 位元值，應用程式可用來維護其他功能表項目相關聯的資料。 這個 32 位元值是在應用程式可以使用**itemData**所提供的結構成員[WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925)和[WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923)訊息。 功能表項目最初顯示或變更時，會傳送這些訊息。|  
|**MF_STRING**|包含以 null 終止的字串長度的指標。 這是預設解譯。|  
|**MF_SEPARATOR**|`lpszNewItem`參數已忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`物件，做為功能表項目。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式可以在程式中設定值，指定功能表項目的狀態`nFlags`。  
  
 每當 功能表上，位於視窗變更時 （無論顯示在視窗），應用程式應該呼叫`CWnd::DrawMenuBar`。  
  
 當`nIDNewItem`指定快顯功能表上，它會成為的功能表插入它的部分。 如果該功能表損毀時，[插入] 功能表也會終結。 插入的功能表應該會中斷`CMenu`物件，以避免衝突。  
  
 如果多個文件介面 (MDI) 子視窗最大化作用中，應用程式中插入快顯功能表到 MDI 應用程式的功能表呼叫此函式，並指定**MF_BYPOSITION**旗標，功能表會插入一個向左比預期的位置。 這是因為使用中的 MDI 子視窗的 [控制] 功能表會插入至 MDI 框架視窗的功能表列的第一個位置。 若要正確放置功能表，應用程式必須加入要使用的位置值 1。 應用程式可以使用**WM_MDIGETACTIVE**訊息，以判斷是否要最大化目前作用中的子視窗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&28;](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]  
  
##  <a name="insertmenuitem"></a>CMenu::InsertMenuItem  
 在功能表中的指定位置處插入新的功能表項目。  
  
```  
BOOL InsertMenuItem(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `uItem`  
 請參閱說明`uItem`中[InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpMenuItemInfo`  
 請參閱說明`lpmii`中**InsertMenuItem**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `fByPos`  
 請參閱說明`fByPosition`中**InsertMenuItem**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此函式會包裝[InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="loadmenu"></a>CMenu::LoadMenu  
 從應用程式的可執行檔載入功能表資源，並將它附加`CMenu`物件。  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>參數  
 `lpszResourceName`  
 指向以 null 結束的字串，其中包含要載入的功能表資源名稱。  
  
 `nIDResource`  
 指定要載入功能表資源功能表的識別碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功; 載入功能表資源否則為 0。  
  
### <a name="remarks"></a>備註  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派給視窗相關聯的功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&29;](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect  
 從功能表範本在記憶體中載入資源，並將其以附加`CMenu`物件。  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>參數  
 *lpMenuTemplate*  
 指向功能表範本 (即單一[MENUITEMTEMPLATEHEADER](http://msdn.microsoft.com/library/windows/desktop/ms647583)結構和一個或多個集合[MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581)結構)。 如需有關這些兩個結構的詳細資訊，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功; 載入功能表資源否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表範本是由標頭以及其後的一或多個集合[MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581)結構，其中每一個可能包含一個或多個功能表項目和快顯功能表。  
  
 版本號碼應為 0。  
  
 **MtOption**旗標應該包括**MF_END**快顯清單中的最後一個項目和主要清單中的最後一個項目。 請參閱`AppendMenu`其他旗標的成員函式。 **MtId**成員必須被省略， **MENUITEMTEMPLATE**結構時**MF_POPUP**中指定**mtOption**。  
  
 配置的空間**MENUITEMTEMPLATE**結構必須夠大的**mtString**包含檔案名稱以 null 結尾字串的功能表項目。  
  
 結束之前，應用程式必須釋放系統資源，如果功能表未指派給視窗相關聯的功能表。 應用程式藉由呼叫釋放功能表[DestroyMenu](#destroymenu)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&30;](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="m_hmenu"></a>CMenu::m_hMenu  
 指定`HMENU`控制代碼的 Windows 功能表附加至`CMenu`物件。  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::LoadMenu](#loadmenu)。  
  
##  <a name="measureitem"></a>CMenu::MeasureItem  
 建立主控描繪樣式功能表時，由架構呼叫。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpMeasureItemStruct`  
 指標`MEASUREITEMSTRUCT`結構。  
  
### <a name="remarks"></a>備註  
 根據預設，此成員函式沒有作用。 覆寫此成員函式，並填入`MEASUREITEMSTRUCT`結構以通知視窗功能表的維度。  
  
 請參閱[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)的說明`MEASUREITEMSTRUCT`結構。  
  
### <a name="example"></a>範例  
 下列程式碼是從 MFC [CTRLTEST](../../visual-cpp-samples.md)範例︰  
  
 [!code-cpp[NVC_MFCWindowing #&31;](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]  
  
##  <a name="modifymenu"></a>CMenu::ModifyMenu  
 變更現有的功能表項目所指定的位置`nPosition`。  
  
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
 `nPosition`  
 指定要變更功能表項目。 `nFlags`參數可以用來解譯`nPosition`如下︰  
  
|nFlags|NPosition 的解譯|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|指定此參數可讓現有的功能表項目的命令 ID。 這是預設值，如果沒有**MF_BYCOMMAND**或**MF_BYPOSITION**設定。|  
|**MF_BYPOSITION**|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
 `nFlags`  
 指定如何`nPosition`解譯，並提供對功能表項目所做變更的相關資訊。 如需可能設定的旗標的清單，請參閱[AppendMenu](#appendmenu)成員函式。  
  
 `nIDNewItem`  
 指定已修改的功能表項目的其中一個命令識別碼或者，如果`nFlags`設為**MF_POPUP**，功能表控制代碼 ( `HMENU`) 的快顯功能表。 `nIDNewItem`參數已忽略 （不需要），如果`nFlags`設為**MF_SEPARATOR**。  
  
 `lpszNewItem`  
 指定新的功能表項目的內容。 `nFlags`參數可以用來解譯`lpszNewItem`如下︰  
  
|nFlags|LpszNewItem 的解譯|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|包含應用程式所提供的 32 位元值，應用程式可用來維護其他功能表項目相關聯的資料。 這個 32 位元值會提供給應用程式在處理時**MF_MEASUREITEM**和**MF_DRAWITEM**。|  
|**MF_STRING**|包含以 null 結束的字串，或寫入的長指標`CString`。|  
|**MF_SEPARATOR**|`lpszNewItem`參數已忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`物件，做為功能表項目。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式設定的值指定新的功能表項目狀態`nFlags`。 如果此函式來取代快顯功能表的功能表項目相關聯，它會破壞舊的快顯功能表，並釋放的記憶體供快顯功能表。  
  
 當`nIDNewItem`指定快顯功能表上，它會成為的功能表插入它的部分。 如果該功能表損毀時，[插入] 功能表也會終結。 插入的功能表應該會中斷`CMenu`物件，以避免衝突。  
  
 每當 功能表上，位於視窗變更時 （無論顯示在視窗），應用程式應該呼叫`CWnd::DrawMenuBar`。 若要變更現有的功能表項目的屬性，會更快速地使用`CheckMenuItem`和`EnableMenuItem`成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="operator_hmenu"></a>CMenu::operator HMENU  
 使用這個運算子來擷取的控制代碼`CMenu`物件。  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的控制代碼`CMenu`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 若要直接呼叫 Windows Api，您可以使用控制代碼。  
  
##  <a name="operator_neq"></a>CMenu::operator ！ =  
 判斷兩個功能表是否以邏輯方式不相等。  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>參數  
 `menu`  
 A`CMenu`比較的物件。  
  
### <a name="remarks"></a>備註  
 測試是否不等於右邊的功能表物件左邊的功能表物件。  
  
##  <a name="operator_eq_eq"></a>CMenu::operator = =  
 判斷兩個功能表是否邏輯上相等。  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>參數  
 `menu`  
 A`CMenu`比較的物件。  
  
### <a name="remarks"></a>備註  
 測試在左邊的功能表物件是否相等 (的`HMENU`值) 到右邊的功能表物件。  
  
##  <a name="removemenu"></a>CMenu::RemoveMenu  
 從功能表中刪除具有相關聯的快顯功能表的功能表項目。  
  
```  
BOOL RemoveMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 `nPosition`  
 指定要移除功能表項目。 `nFlags`參數可以用來解譯`nPosition`如下︰  
  
|nFlags|NPosition 的解譯|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|指定此參數可讓現有的功能表項目的命令 ID。 這是預設值，如果沒有**MF_BYCOMMAND**或**MF_BYPOSITION**設定。|  
|**MF_BYPOSITION**|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
 `nFlags`  
 指定如何`nPosition`解譯。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 它不會終結的控制代碼快顯功能表上，因此可以重複使用的功能表。 應用程式可能會呼叫之前呼叫此函數，`GetSubMenu`成員函式，以取得快顯視窗`CMenu`重複使用的物件。  
  
 每當 功能表上，位於視窗變更時 （無論顯示在視窗），應用程式必須呼叫`CWnd::DrawMenuBar`。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setdefaultitem"></a>CMenu::SetDefaultItem  
 設定預設功能表項目中指定的功能表。  
  
```  
BOOL SetDefaultItem(
    UINT uItem,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `uItem`  
 識別項或新的預設功能表項目或沒有預設的項目 1 的位置。 這個參數的意義取決於值`fByPos`。  
  
 `fByPos`  
 值，指定的意義`uItem`。 如果這個參數是**FALSE**，`uItem`是功能表項目識別碼。 否則，就是功能表項目位置。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，傳回的值不是零。 如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，使用 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 函式的行為[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId  
 使用的內容說明識別碼相關聯`CMenu`。  
  
```  
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```  
  
### <a name="parameters"></a>參數  
 `dwContextHelpId`  
 內容說明識別碼相關聯`CMenu`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0  
  
### <a name="remarks"></a>備註  
 在功能表中的所有項目共用這個識別碼，就不可能將說明內容識別碼附加至個別的功能表項目。  
  
### <a name="example"></a>範例  
  請參閱範例[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setmenuinfo"></a>CMenu::SetMenuInfo  
 設定 功能表上的資訊。  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>參數  
 `lpcmi`  
 指標[MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575)結構包含功能表的資訊。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，傳回值為非零值;否則，傳回值為零。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可設定 功能表上的特定資訊。  
  
##  <a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps  
 關聯功能表項目至指定的點陣圖。  
  
```  
BOOL SetMenuItemBitmaps(
    UINT nPosition,  
    UINT nFlags,  
    const CBitmap* pBmpUnchecked,  
    const CBitmap* pBmpChecked);
```  
  
### <a name="parameters"></a>參數  
 `nPosition`  
 指定要變更功能表項目。 `nFlags`參數可以用來解譯`nPosition`如下︰  
  
|nFlags|NPosition 的解譯|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|指定此參數可讓現有的功能表項目的命令 ID。 這是預設值，如果沒有**MF_BYCOMMAND**或**MF_BYPOSITION**設定。|  
|**MF_BYPOSITION**|指定此參數可讓現有的功能表項目的位置。 第一個項目位於位置 0。|  
  
 `nFlags`  
 指定如何`nPosition`解譯。  
  
 `pBmpUnchecked`  
 指定要使用未檢查的功能表項目的點陣圖。  
  
 `pBmpChecked`  
 指定要簽入的功能表項目所使用的點陣圖。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 功能表項目是否已核取或取消核取，Windows 會顯示功能表項目旁適當的點陣圖。  
  
 如果`pBmpUnchecked`或`pBmpChecked`是**NULL**，則 Windows 會顯示任何內容旁邊的功能表項目對應的屬性。 如果兩個參數都**NULL**，當項目會檢查和移除核取記號，若未選取項目時，Windows 會使用預設核取記號。  
  
 功能表終結時，不會終結這些點陣圖。應用程式必須摧毀它們。  
  
 Windows **GetMenuCheckMarkDimensions**函式會擷取預設核取記號，功能表項目使用的維度。 應用程式會使用這些值來判斷適當的大小，此函式所提供的點陣圖。 取得大小，建立您的點陣圖，然後設定它們。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&32;](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing #&33;](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo  
 變更功能表項目相關的資訊。  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `uItem`  
 請參閱說明`uItem`中[SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpMenuItemInfo`  
 請參閱說明`lpmii`中**SetMenuItemInfo**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `fByPos`  
 請參閱說明`fByPosition`中**SetMenuItemInfo**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此函式會包裝[SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="trackpopupmenu"></a>CMenu::TrackPopupMenu  
 浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。  
  
```  
BOOL TrackPopupMenu(
    UINT nFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPCRECT lpRect = 0);
```  
  
### <a name="parameters"></a>參數  
 `nFlags`  
 指定螢幕位置和滑鼠位置的旗標。 請參閱[TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002)可用旗標的清單。  
  
 *x*  
 指定螢幕座標中的快顯功能表上的水平位置。 值而定`nFlags`參數，功能表可以靠左對齊、 靠右對齊或置中，相對於此位置。  
  
 *y*  
 在畫面上指定螢幕座標中的功能表頂端的垂直位置。  
  
 `pWnd`  
 識別擁有快顯功能表上的視窗。 這個參數不能**NULL**，即使**TPM_NONOTIFY**指定旗標。 此視窗會收到所有**WM_COMMAND**  功能表上的訊息。 在 Windows 3.1 和更新版本中，視窗不會收到**WM_COMMAND**訊息直到`TrackPopupMenu`傳回。 在 Windows 3.0 中，視窗接收到**WM_COMMAND**訊息之前`TrackPopupMenu`傳回。  
  
 `lpRect`  
 忽略。  
  
### <a name="return-value"></a>傳回值  
 這個方法會傳回呼叫結果[TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 浮動的快顯功能表可以出現在螢幕上的任何位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&34;](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx  
 浮動的快顯功能表顯示在指定的位置，並追蹤的項目在快顯功能表。  
  
```  
BOOL TrackPopupMenuEx(
    UINT fuFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPTPMPARAMS lptpm);
```  
  
### <a name="parameters"></a>參數  
 `fuFlags`  
 指定不同的函式的擴充的功能表。 所有值的清單及它們的意義，請參閱[TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003)。  
  
 *x*  
 指定螢幕座標中的快顯功能表上的水平位置。  
  
 *y*  
 在畫面上指定螢幕座標中的功能表頂端的垂直位置。  
  
 `pWnd`  
 視窗快顯功能表與接收的訊息，從 [建立] 功能表上的指標。 這個視窗可以是任何視窗從目前的應用程式，但不能是**NULL**。 如果您指定**TPM_NONOTIFY**中`fuFlags`參數，此函式不會傳送任何訊息給`pWnd`。 函數必須傳回指向視窗`pWnd`接收**WM_COMMAND**訊息。  
  
 *lptpm*  
 指標[產生 TPMPARAMS](http://msdn.microsoft.com/library/windows/desktop/ms647586)結構，指定螢幕的功能表區域不應該重疊。 這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果您指定**TPM_RETURNCMD**中`fuFlags`參數，則傳回值是使用者選取項目的功能表項目識別碼。 如果使用者取消功能表而不進行選取，或發生錯誤，則傳回值為 0。  
  
 如果您未指定**TPM_RETURNCMD**中`fuFlags`參數，則傳回值是零，如果函式成功，0 失敗。 若要取得擴充的錯誤資訊，呼叫[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>備註  
 浮動的快顯功能表可以出現在螢幕上的任何位置。 如需有關如何建立快顯功能表時處理錯誤的詳細資訊，請參閱[TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLTEST](../../visual-cpp-samples.md)   
 [MFC 範例 DYNAMENU](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)

