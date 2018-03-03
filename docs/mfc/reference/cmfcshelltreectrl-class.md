---
title: "CMFCShellTreeCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 727b0032687ed22692f07f9b5e9e5fe8b2813071
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 類別
`CMFCShellTreeCtrl`類別會擴充[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)透過顯示 Shell 項目階層。  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>語法  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快顯功能表。|  
|[CMFCShellTreeCtrl::GetFlags](#getflags)|傳回傳遞給的旗標的組合[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。|  
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|擷取的項目路徑。|  
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|將指標傳回至[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件與此搭配使用時，`CMFCShellTreeCtrl`物件來建立類似檔案總管的視窗。|  
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|此視窗的父視窗收到此視窗的通知訊息時，會呼叫此成員函式。 (覆寫[On_xxx_reflect](../../mfc/reference/cwnd-class.md#onchildnotify)。)|  
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||  
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||  
|[CMFCShellTreeCtrl::Refresh](#refresh)|重新整理，並重新繪製目前`CMFCShellTreeCtrl`物件。|  
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|選取提供的 PIDL 或字串路徑為基礎的適當的樹狀目錄控制項目。|  
|[CMFCShellTreeCtrl::SetFlags](#setflags)|設定旗標來篩選樹狀目錄路徑 (類似於使用的旗標`IShellFolder::EnumObjects`)。|  
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|設定目前之間的關聯`CMFCShellTreeCtrl`物件和`CMFCShellListCtrl`物件。|  
  
## <a name="remarks"></a>備註  
 這個類別會擴充`CTreeCtrl`藉由啟用您的程式，包括 Windows Shell 項目樹狀目錄中的類別。 這個類別可以與相關聯`CMFCShellListCtrl`物件以建立完整的 [總管] 視窗。 然後，選取項目樹狀目錄中將會顯示 Windows Shell 項目清單關聯的清單。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 `CMFCShellTreeCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxshelltreeCtrl.h  
  
## <a name="example"></a>範例  
 下列範例示範如何建立 `CMFCShellTreeCtrl` 類別的物件。 此程式碼片段是部分[總管範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu  
 啟用快顯功能表。  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 布林值，指定是否啟用快顯功能表。  
  
##  <a name="getflags"></a>CMFCShellTreeCtrl::GetFlags  
 傳回設定的旗標[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
DWORD GetFlags() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`設定值，指定目前的旗標的組合。  
  
### <a name="remarks"></a>備註  
 在設定的旗標`CMFCShellTreeCtrl`方法傳送[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)每當重新整理物件。 您可以變更的旗標與[CMFCShellTreeCtrl::SetFlags](#setflags)方法。  
  
##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath  
 擷取的路徑中的項目[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    HTREEITEM htreeItem = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strPath`  
 字串參數的參考。 方法會寫入此參數中的項目的路徑。  
  
 [輸入] `htreeItem`  
 方法會擷取此樹狀目錄控制項目的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此方法失敗，`strPath`包含空字串。  
  
 如果您未指定`hTreeItem`，這個方法會嘗試取得目前選取項目的字串。 如果不選取任何項目和`hTreeItem`是`NULL`，此方法失敗。  
  
##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList  
 將指標傳回至[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)與此相關聯的物件[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
CMFCShellListCtrl* GetRelatedList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCShellListCtrl`與此樹狀目錄控制項物件相關聯的物件。  
  
### <a name="remarks"></a>備註  
 使用`CMFCShellListCtrl`物件搭配`CMFCShellTreeCtrl`物件，您可以建立類似檔案總管的視窗。 使用方法[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)使兩個類別。 與其相關聯之後，架構會自動更新`CMFCShellListCtrl`如果中的選取範圍`CMFCShellTreeCtrl`變更。  
  
##  <a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify  

  
```  
virtual BOOL OnChildNotify(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* pLResult);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `message`  
 [輸入] `wParam`  
 [輸入] `lParam`  
 [輸入] `pLResult`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon  

  
```  
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pItem`  
 [輸入] `bSelected`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText  

  
```  
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pItem`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="refresh"></a>CMFCShellTreeCtrl::Refresh  
 重新整理，並重新繪製[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>備註  
 呼叫此方法以重新整理中所顯示的項目階層架構`CMFCShellTreeCtrl`。  
  
##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath  
 選取的項目中[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)根據提供的路徑。  
  
```  
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszPath`  
 字串，指定項目的路徑。  
  
 [輸入] `lpidl`  
 指定的項目 PIDL  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，`E_FAIL`否則。  
  
##  <a name="setflags"></a>CMFCShellTreeCtrl::SetFlags  
 設定旗標來篩選樹狀目錄路徑。  
  
```  
void SetFlags(
    DWORD dwFlags,  
    BOOL bRefresh = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dwFlags`  
 要設定的旗標。  
  
 [輸入] `bRefresh`  
 布林值，指定是否`CMFCShellTreeCtrl`應該立即重新整理。  
  
### <a name="remarks"></a>備註  
 `CMFCShellTreeCtrl`通過所有設定旗標為[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。 不同的旗標之值的相關資訊，請參閱[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。  
  
##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList  
 將[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件。  
  
```  
void SetRelatedList(CMFCShellListCtrl* pShellList);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pShellList`  
 指標`CMFCShellListCtrl`物件。  
  
### <a name="remarks"></a>備註  
 這個方法將`CMFCShellListCtrl`與`CMFCShellTreeCtrl`。 這些物件可能會顯示類似檔案總管的視窗為： 如果使用者選取中的物件`CMFCShellTreeCtrl`、 相關的項目中的`CMFCShellListCtrl`會自動更新。  
  
 使用方法[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)擷取`CMFCShellListCtrl`聯`CMFCShellTreeCtrl`。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)   
 [CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)
