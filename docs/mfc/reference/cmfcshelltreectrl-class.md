---
title: "CMFCShellTreeCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellTreeCtrl class
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
caps.latest.revision: 30
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
ms.openlocfilehash: cf9c7c3577646895546c443c975a92431194d3f4
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 類別
`CMFCShellTreeCtrl`類別會擴充[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)透過顯示 Shell 項目階層的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快顯功能表。|  
|[CMFCShellTreeCtrl::GetFlags](#getflags)|傳回傳遞至的旗標的組合[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。|  
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|擷取項目的路徑。|  
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|傳回的指標[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件，這搭配`CMFCShellTreeCtrl`物件來建立類似檔案總管的視窗。|  
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|這個視窗的父視窗收到套用到這個視窗的通知訊息時，會呼叫此成員函式。 (覆寫[On_xxx_reflect](../../mfc/reference/cwnd-class.md#onchildnotify)。)|  
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||  
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||  
|[CMFCShellTreeCtrl::Refresh](#refresh)|重新整理，並重新繪製目前`CMFCShellTreeCtrl`物件。|  
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|選取適當的樹狀目錄控制項項目根據提供的 PIDL 或字串路徑。|  
|[CMFCShellTreeCtrl::SetFlags](#setflags)|設定旗標來篩選樹狀目錄的路徑 (類似於使用的旗標`IShellFolder::EnumObjects`)。|  
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|設定目前之間的關聯`CMFCShellTreeCtrl`物件和`CMFCShellListCtrl`物件。|  
  
## <a name="remarks"></a>備註  
 此類別會擴充`CTreeCtrl`藉由啟用您的程式，包括 Windows Shell 項目樹狀結構中的類別。 這個類別可以關聯的`CMFCShellListCtrl`物件來建立完整的 [總管] 視窗。 然後，在樹狀目錄中選取項目將一份 Windows Shell 項目清單中顯示相關聯。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 `CMFCShellTreeCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxshelltreeCtrl.h  
  
## <a name="example"></a>範例  
 下列範例示範如何建立 `CMFCShellTreeCtrl` 類別的物件。 此程式碼片段是一部分[總管範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer #&4;](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer #&5;](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]  
  
##  <a name="a-nameenableshellcontextmenua--cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu  
 啟用快顯功能表。  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值，指定是否啟用快顯功能表。  
  
##  <a name="a-namegetflagsa--cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl::GetFlags  
 傳回設定的旗標[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
DWORD GetFlags() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`設定值，指定目前的旗標的組合。  
  
### <a name="remarks"></a>備註  
 在設定旗標`CMFCShellTreeCtrl`方法傳送[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)每次重新整理的物件。 您可以變更旗標[CMFCShellTreeCtrl::SetFlags](#setflags)方法。  
  
##  <a name="a-namegetitempatha--cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath  
 擷取中的項目路徑[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    HTREEITEM htreeItem = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strPath`  
 字串參數的參考。 方法會寫入此參數中的項目的路徑。  
  
 [in] `htreeItem`  
 方法會擷取此樹狀目錄控制項目的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此方法失敗，`strPath`包含空字串。  
  
 如果您未指定`hTreeItem`，這個方法會嘗試取得目前選取項目的字串。 如果在不選取任何項目和`hTreeItem`是`NULL`，這個方法會失敗。  
  
##  <a name="a-namegetrelatedlista--cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList  
 傳回的指標[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)與此相關聯的物件[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
CMFCShellListCtrl* GetRelatedList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCShellListCtrl`與此樹狀目錄控制項物件相關聯的物件。  
  
### <a name="remarks"></a>備註  
 使用`CMFCShellListCtrl`物件搭配`CMFCShellTreeCtrl`物件時，您可以建立類似檔案總管的視窗。 使用方法[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)關聯兩個類別。 它們會關聯之後，架構會自動更新`CMFCShellListCtrl`如果中的選取範圍`CMFCShellTreeCtrl`變更。  
  
##  <a name="a-nameonchildnotifya--cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnChildNotify(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* pLResult);
```  
  
### <a name="parameters"></a>參數  
 [in] `message`  
 [in] `wParam`  
 [in] `lParam`  
 [in] `pLResult`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameongetitemicona--cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>參數  
 [in] `pItem`  
 [in] `bSelected`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameongetitemtexta--cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>參數  
 [in] `pItem`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerefresha--cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFCShellTreeCtrl::Refresh  
 重新整理，並重新繪製[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來重新整理中所顯示的項目階層`CMFCShellTreeCtrl`。  
  
##  <a name="a-nameselectpatha--cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath  
 選取一個項目中的[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)根據提供的路徑。  
  
```  
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszPath`  
 字串，指定項目的路徑。  
  
 [in] `lpidl`  
 指定的項目 PIDL  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，`E_FAIL`否則。  
  
##  <a name="a-namesetflagsa--cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl::SetFlags  
 設定旗標來篩選樹狀目錄的內容。  
  
```  
void SetFlags(
    DWORD dwFlags,  
    BOOL bRefresh = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwFlags`  
 要設定的旗標。  
  
 [in] `bRefresh`  
 布林值，指定是否`CMFCShellTreeCtrl`應該立即重新整理。  
  
### <a name="remarks"></a>備註  
 `CMFCShellTreeCtrl`通過所有設定旗標為[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。 不同的旗標之值的相關資訊，請參閱[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。  
  
##  <a name="a-namesetrelatedlista--cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList  
 將[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
void SetRelatedList(CMFCShellListCtrl* pShellList);
```  
  
### <a name="parameters"></a>參數  
 [in] `pShellList`  
 指標`CMFCShellListCtrl`物件。  
  
### <a name="remarks"></a>備註  
 這個方法將`CMFCShellListCtrl`與`CMFCShellTreeCtrl`。 這些物件可能會顯示為類似檔案總管的視窗︰ 如果使用者選取的物件在`CMFCShellTreeCtrl`、 相關的項目中的`CMFCShellListCtrl`會自動更新。  
  
 使用方法[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)擷取`CMFCShellListCtrl`聯`CMFCShellTreeCtrl`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)   
 [CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)

