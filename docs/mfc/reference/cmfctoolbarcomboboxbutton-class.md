---
title: "CMFCToolBarComboBoxButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxButton class
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
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
ms.openlocfilehash: 43369e8869f9dd58543016bd74547b24fbe183a5
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 類別
包含下拉式方塊控制項的工具列按鈕 ( [CComboBox 類別](../../mfc/reference/ccombobox-class.md))。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|建構 `CMFCToolBarComboBoxButton`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](#additem)|將項目加入至下拉式方塊清單的結尾。|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|將項目加入至下拉式方塊的清單。 在清單中項目的順序由`Compare`。|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|比較兩個項目。 呼叫來排序的項目`AddSortedItems`將加入至下拉式方塊的清單。|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|建立新的編輯控制項的下拉式方塊按鈕。|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|從下拉式方塊清單中刪除項目。|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|傳回包含指定之的字串的項目索引。|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|將指標傳回至下拉式方塊按鈕，並提供指定的命令識別碼。|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|傳回內嵌於下拉式方塊按鈕的下拉式方塊控制項的指標。|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|傳回的項目數下拉式方塊中方塊的清單。|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|尋找下拉式方塊按鈕具有指定的命令識別碼。 傳回的項目數下拉式方塊中的按鈕方塊清單。|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|傳回選取的項目索引下拉式方塊中方塊的清單。|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回所選取項目的索引下拉式方塊中的按鈕方塊的清單。|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|編輯控制項內嵌在下拉式方塊按鈕中傳回的指標。|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|傳回與下拉式方塊中指定之索引相關聯的字串方塊的清單。|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|尋找下拉式方塊按鈕具有指定之的命令 ID，並傳回該按鈕的下拉式方塊的清單中的索引相關聯的字串。|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|傳回與下拉式方塊中指定之索引相關聯的 32 位元值方塊的清單。|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|尋找下拉式方塊按鈕具有指定之的命令 ID，並傳回該按鈕的下拉式方塊的清單中的索引相關聯的 32 位元值。|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|尋找下拉式方塊按鈕具有指定的命令識別碼。 擷取的 32 位元值相關聯的該按鈕，並傳回 32 位元值的指標下拉式方塊的清單中的索引。|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|傳回文字編輯控制項的下拉式方塊。|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|尋找下拉式方塊按鈕具有指定之的命令 ID，並傳回文字編輯控制項的按鈕。|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|決定應用程式中的下拉式方塊按鈕要置中對齊或對齊頂端的工具列。|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|判斷應用程式中的下拉式方塊按鈕是否具有平面外觀。|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|移除所有項目從清單方塊和下拉式方塊控制項的編輯。|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|根據其索引、 32 位元值或字串，下拉式方塊中選取一個項目，並通知有關選項的下拉式方塊控制項。|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|尋找下拉式方塊按鈕具有指定的命令識別碼。 呼叫`SelectItem`按鈕根據其字串、 索引或 32 位元值的下拉式方塊中選取的項目。|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|指定應用程式中的下拉式方塊按鈕會垂直置中或對齊頂端的工具列。|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|設定下拉式清單方塊的高度。|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|指定應用程式中的下拉式方塊按鈕是否具有平面外觀。|  
  
## <a name="remarks"></a>備註  
 若要將下拉式方塊按鈕加入至工具列，請遵循下列步驟︰  
  
 1. 為父工具列資源的按鈕保留假的資源 ID。  
  
 2. 建構`CMFCToolBarComboBoxButton`物件。  
  
 3. 在訊息處理常式中處理`AFX_WM_RESETTOOLBAR`訊息，請使用，以新的下拉式方塊按鈕取代 dummy 按鈕[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 如需詳細資訊，請參閱[逐步解說︰ 將工具列控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 下拉式方塊的工具列按鈕的範例，請參閱範例專案 VisualStudioDemo。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCToolBarComboBoxButton`類別。 此範例顯示如何啟用編輯] 和 [下拉式方塊、 應用程式中設定的垂直位置的下拉式方塊按鈕、 清單方塊的高度時設定下，卸除應用程式、 設定下拉式方塊按鈕的平面樣式外觀和設定的下拉式方塊按鈕的 [編輯] 方塊中的文字。 此程式碼片段是一部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&36;](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo #&37;](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbarcomboboxbutton.h  
  
##  <a name="a-nameadditema--cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComboBoxButton::AddItem  
 將唯一的項目附加至清單方塊。  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszItem`  
 若要新增到清單方塊項目的文字。  
  
 [in] `dwData`  
 與要新增到清單方塊項目相關聯的資料。  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的最後一個項目索引。  
  
### <a name="remarks"></a>備註  
 排序的清單方塊樣式時，請勿使用這個方法。  
  
 如果項目文字已在清單方塊中，新的資料會儲存與現有的項目。 項目的搜尋不區分大小寫。  
  
##  <a name="a-nameaddsorteditema--cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem  
 將項目加入至清單方塊中所定義的順序[比較](#compare)方法。  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszItem`  
 若要新增到清單方塊項目的文字。  
  
 [in] `dwData`  
 與要新增到清單方塊項目相關聯的資料。  
  
### <a name="return-value"></a>傳回值  
 已加入至清單方塊的項目索引。  
  
### <a name="remarks"></a>備註  
 使用此函式項目加入清單方塊，以特定順序。  
  
##  <a name="a-namecanbestretcheda--cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched  
 指出是否可以變更下拉式方塊按鈕的大小。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `TRUE`。  
  
##  <a name="a-namecmfctoolbarcomboboxbuttona--cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 建構[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件。  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 [新增] 按鈕的命令 ID。  
  
 [in] `iImage`  
 [新增] 按鈕相關聯的映像的映像索引。  
  
 [in] `dwStyle`  
 [新增] 按鈕的樣式。  
  
 [in] `iWidth`  
 寬度，單位為像素 [新增] 按鈕。  
  
### <a name="remarks"></a>備註  
 預設寬度是 150 個像素。  
  
 如需工具列按鈕樣式的清單，請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="a-namecleardataa--cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData  
 刪除使用者定義的資料。  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>備註  
 依預設這個方法沒有作用。 如果您想要刪除任何使用者定義的資料，請覆寫這個方法在衍生類別中。  
  
##  <a name="a-namecomparea--cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComboBoxButton::Compare  
 比較兩個字串。  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszItem1`  
 要比較的第一個字串。  
  
 [in] `lpszItem2`  
 要比較的第二個字串。  
  
### <a name="return-value"></a>傳回值  
 值，指出字串之間的區分大小寫編纂關聯性。 下表列出可能的值︰  
  
|值|描述|  
|-----------|-----------------|  
|\<0|第一個字串是否小於第二個。|  
|0|第一個字串值等於第二個。|  
|>0|第一個字串大於第二個。|  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以變更項目在清單方塊中的排序方式。  
  
 比較會區分大小寫。  
  
 會呼叫這個方法只會從[AddSortedItem](#addsorteditem)方法。  
  
##  <a name="a-namecopyfroma--cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom  
 複製指定的狀態`CMFCToolBarComboBoxButton`目前的物件。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
 來源 `CMFCToolBarComboBoxButton` 物件。  
  
##  <a name="a-namecreatecomboa--cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo  
 建立新的下拉式方塊的下拉式方塊按鈕。  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 按鈕的父視窗的指標。  
  
 [in] `rect`  
 下拉式方塊的週框。  
  
### <a name="return-value"></a>傳回值  
 指向新的下拉式方塊如果方法成功。否則， `NULL`。  
  
##  <a name="a-namecreateedita--cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit  
 建立新的編輯方塊的下拉式方塊按鈕。  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 按鈕的父視窗的指標。  
  
 [in] `rect`  
 新的編輯方塊的周框矩形。  
  
 [in] `dwEditStyle`  
 新的編輯方塊控制項樣式。  
  
### <a name="return-value"></a>傳回值  
 指向新的編輯方塊如果方法成功。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 建立新的編輯方塊的下拉式方塊按鈕時，架構會呼叫這個方法。 覆寫此方法以變更如何[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)建立。  
  
##  <a name="a-namedeleteitema--cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem  
 從清單方塊中刪除指定的項目。  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 要刪除的項目以零為起始的索引。  
  
 [in] `dwData`  
 要刪除的項目與相關的資料。  
  
 [in] `lpszText`  
 要刪除之項目的文字。 如果有多個項目具有相同的文字，則會刪除第一個項目。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此項目已位於與已成功刪除。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameduplicatedataa--cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData  
 重複使用者定義的資料。  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>備註  
 依預設這個方法沒有作用。 如果您想要複製任何使用者定義的資料，請覆寫這個方法在衍生類別中。  
  
##  <a name="a-nameenablewindowa--cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow  
 啟用或停用編輯] 和 [下拉式方塊。  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用編輯和下拉式方塊。`FALSE`停用編輯] 和 [下拉式方塊。  
  
### <a name="remarks"></a>備註  
 停用時，這些控制項不能成為使用中，而且不能接受使用者輸入。  
  
##  <a name="a-nameexporttomenubuttona--cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton  
 複製到指定的功能表，使用下拉式方塊按鈕命令的應用程式字串資料表的字串識別碼。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `menuButton`  
 參考功能表按鈕。  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
##  <a name="a-namefinditema--cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem  
 傳回包含指定的字串清單方塊中的第一個項目的索引。  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszText`  
 在清單方塊中搜尋文字。  
  
### <a name="return-value"></a>傳回值  
 項目; 索引或`CB_ERR`如果找不到項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetbycmda--cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd  
 取得指標下拉式方塊按鈕具有指定的命令識別碼。  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 下拉式方塊按鈕的命令 ID。  
  
 [in] `bIsFocus`  
 `TRUE`只搜尋已取得焦點的按鈕。`FALSE`搜尋所有的按鈕。  
  
### <a name="return-value"></a>傳回值  
 指向下拉式方塊按鈕。或`NULL`如果找不到按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcomboboxa--cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox  
 傳回的指標至下拉式方塊下拉式方塊中 按鈕。  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CComboBox 類別](../../mfc/reference/ccombobox-class.md)物件的方法是否成功，否則為`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcontextmenuida--cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID  
 取得下拉式方塊按鈕的捷徑功能表上的資源識別碼。  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>傳回值  
 快顯功能表上的資源 id。  
  
##  <a name="a-namegetcounta--cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount  
 清單方塊中，傳回的項目數。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的項目數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcountalla--cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll  
 取得擁有指定的命令識別碼下拉式方塊按鈕的清單方塊中的項目數  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 下拉式方塊按鈕的命令 ID。  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的項目數否則，`CB_ERR`如果找不到下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcursela--cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel  
 清單方塊中，取得目前選取項目的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中，目前選取項目的索引或`CB_ERR`如果在不選取任何項目。  
  
### <a name="remarks"></a>備註  
 清單方塊索引以零為起始。  
  
##  <a name="a-namegetcurselalla--cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll  
 傳回目前選取項目的索引中的下拉式清單方塊方塊按鈕具有指定的命令識別碼。  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 下拉式方塊按鈕的命令 ID。  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中，目前選取項目的索引否則，`CB_ERR`如果在選取任何項目，或找不到下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
 清單方塊索引以零為起始。  
  
##  <a name="a-namegeteditctrla--cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl  
 讓指標回到編輯方塊下拉式方塊中 按鈕。  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>傳回值  
 變數的指標，此方法成功; 如果在編輯方塊否則， `NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegethwnda--cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd  
 傳回下拉式方塊的視窗控制代碼。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>傳回值  
 視窗控制代碼或`NULL`如果下拉式方塊不是視窗物件相關聯。  
  
##  <a name="a-namegetitema--cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem  
 傳回與清單方塊中的指定索引處的項目關聯的字串。  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 項目; 相關聯字串的指標否則，`NULL`如果索引參數無效，或者索引參數是-1，下拉式方塊中沒有選取項目。  
  
### <a name="remarks"></a>備註  
 索引參數-1 會傳回目前選取之項目的字串。  
  
##  <a name="a-namegetitemalla--cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll  
 傳回具有指定的命令 id。 下拉式方塊按鈕的清單方塊中的指定索引處的項目相關聯的字串  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 下拉式方塊按鈕的命令 ID。  
  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功; 將項目的字串的指標否則，`NULL`索引是無效的如果不是下拉式方塊按鈕，或如果索引為-1 和下拉式方塊中沒有選取項目。  
  
### <a name="remarks"></a>備註  
 索引值為-1 會傳回目前選取之項目的字串。  
  
##  <a name="a-namegetitemdataa--cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData  
 傳回與清單方塊中指定索引處的項目相關聯的資料。  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 與項目; 相關聯的資料或 0，表示項目不存在。  
  
### <a name="remarks"></a>備註  
 索引參數-1 會傳回目前選取的項目相關聯的資料。  
  
##  <a name="a-namegetitemdataalla--cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll  
 傳回具有特定的命令 id。 下拉式方塊按鈕的清單方塊中的特定索引處的項目相關聯的資料  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 下拉式方塊按鈕的命令 ID。  
  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功; 與項目相關聯的資料如果指定的索引不正確，或找不到 CB_ERR 如果下拉式方塊按鈕，否則為 0。  
  
### <a name="remarks"></a>備註  
 索引參數-1 會傳回目前選取的項目相關聯的資料。  
  
##  <a name="a-namegetitemdataptralla--cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 傳回具有特定的命令 id。 下拉式方塊按鈕的清單方塊中的特定索引處的項目相關聯的資料 這項資料會傳回的指標。  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 下拉式方塊按鈕的命令 ID。  
  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指標，此方法成功; 如果相關聯的項目如果發生錯誤，則為-1 或`NULL`如果找不到下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetprompta--cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt  
 傳回下拉式方塊按鈕提示字串。  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>傳回值  
 提示的字串。  
  
### <a name="remarks"></a>備註  
 目前未實作這個方法。  
  
##  <a name="a-namegettexta--cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComboBoxButton::GetText  
 取得文字編輯方塊中。  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [編輯] 方塊中的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettextalla--cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll  
 取得具有指定的命令 id。 下拉式方塊按鈕的編輯方塊中的文字  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 特定的下拉式方塊按鈕的命令 ID。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，[編輯] 方塊中的文字否則， `NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehasfocusa--cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus  
 指出是否下拉式方塊目前具有焦點。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果下拉式方塊目前具有焦點。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法也會傳回`TRUE`如果下拉式方塊的任何子視窗目前具有焦點。  
  
##  <a name="a-nameiscenterverta--cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert  
 傳回應用程式中的下拉式方塊按鈕的垂直位置。  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕置中。，`FALSE`如果按鈕靠上對齊。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisflatmodea--cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode  
 傳回應用程式的下拉式方塊按鈕的平面樣式外觀。  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕具有平面的樣式。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 下拉式方塊按鈕的預設一般樣式是`FALSE.`  
  
##  <a name="a-nameisownerofa--cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf  
 指出指定的控制代碼是否與下拉式方塊按鈕，或其中一個子項目。  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `hwnd`  
 視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果控制代碼相關聯的下拉式方塊按鈕，或其中一個子項目。否則， `FALSE`。  
  
##  <a name="a-nameisribbonbuttona--cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton  
 表示下拉式方塊按鈕是否位在功能區面板上。  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一定是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，此方法一律傳回`FALSE`，這表示下拉式方塊按鈕永遠不會顯示在功能區面板上。  
  
##  <a name="a-nameiswindowvisiblea--cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible  
 傳回的可見性狀態的下拉式方塊按鈕。  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊按鈕的可見性狀態。  
  
##  <a name="a-namenotifycommanda--cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand  
 表示下拉式方塊按鈕是否會處理訊息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>參數  
 [in] `iNotifyCode`  
 與命令相關聯的通知訊息。  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊按鈕是否會處理訊息。  
  
##  <a name="a-nameonaddtocustomizepagea--cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 加入按鈕時，由框架呼叫**自訂**對話方塊。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="a-nameoncalculatesizea--cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize  
 若要計算按鈕的大小架構呼叫。  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 會顯示下拉式方塊按鈕的裝置內容。  
  
 [in] `sizeDefault`  
 下拉式方塊按鈕的預設大小。  
  
 [in] `bHorz`  
 為父工具列停駐狀態。 `TRUE`當工具列水平及`FALSE`當工具列垂直。  
  
### <a name="return-value"></a>傳回值  
 A`SIZE`結構，其中包含的下拉式方塊按鈕，單位為像素尺寸。  
  
##  <a name="a-nameonchangeparentwnda--cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd  
 下拉式方塊按鈕插入新的工具列時，由架構呼叫。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 新的父工具列的指標。  
  
##  <a name="a-nameonclicka--cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick  
 當使用者按一下下拉式方塊按鈕，由架構呼叫。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 下拉式方塊按鈕的父視窗的指標。  
  
 [in] `bDelay`  
 保留供衍生類別中使用。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法會處理事件。，否則， `FALSE`。  
  
##  <a name="a-nameonctlcolora--cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor  
 當使用者變更父工具列色彩設定下拉式方塊按鈕的色彩，由架構呼叫。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 會顯示下拉式方塊按鈕的裝置內容。  
  
 [in] `nCtlColor`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 架構會使用要繪製的下拉式方塊按鈕背景的筆刷的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法也會設定下拉式方塊按鈕的文字色彩。  
  
##  <a name="a-nameondrawa--cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw  
 使用指定的樣式和選項，以繪製下拉式方塊按鈕架構呼叫。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `Pdc`  
 顯示按鈕的裝置內容。  
  
 [in] `rect`  
 [] 按鈕，這個周框。  
  
 [in] `pImages`  
 與按鈕關聯的影像集合。  
  
 [in] `bHorz`  
 為父工具列停駐狀態。 `TRUE`當工具列水平及`FALSE`當工具列垂直。  
  
 [in] `bCustomizeMode`  
 應用程式是否在自訂模式。  
  
 [in] `bHighlight`  
 是否要繪製反白顯示下拉式方塊按鈕。  
  
 [in] `bDrawBorder`  
 是否要繪製下拉式方塊按鈕的框線。  
  
 [in] `bGrayDisabledButtons`  
 `TRUE`若要繪製陰影的已停用的按鈕。`FALSE`使用停用映像的集合。  
  
##  <a name="a-nameondrawoncustomizelista--cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 要繪製下拉式方塊按鈕架構呼叫**命令**窗格**自訂**對話方塊。  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 會顯示下拉式方塊按鈕的裝置內容。  
  
 [in] `rect`  
 下拉式方塊按鈕，這個周框。  
  
 [in] `bSelected`  
 `TRUE`如果下拉式方塊按鈕已選取。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 寬度，單位為像素下拉式方塊按鈕。  
  
##  <a name="a-nameonglobalfontschangeda--cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 若要設定下拉式方塊按鈕字型，應用程式的字型變更時架構呼叫。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="a-nameonmovea--cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove  
 若要變更下拉式方塊按鈕的位置，為父工具列移動時架構呼叫。  
  
```  
virtual void OnMove();
```  
  
##  <a name="a-nameonshowa--cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow  
 當您隱藏或顯示下拉式方塊按鈕時，由架構呼叫。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 是否要隱藏或顯示下拉式方塊按鈕。  
  
##  <a name="a-nameonsizea--cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize  
 若要變更下拉式方塊按鈕的大小，為父工具列的大小變更時架構呼叫。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>參數  
 [in] `iSize`  
 新的下拉式方塊按鈕的寬度。  
  
##  <a name="a-nameonupdatetooltipa--cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip  
 在使用者變更下拉式方塊按鈕的工具提示時，由架構呼叫。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 下拉式方塊按鈕的父視窗的指標。  
  
 [in] `iButtonIndex`  
 下拉式方塊按鈕的識別碼。  
  
 [in] `wndToolTip`  
 與下拉式方塊按鈕的工具提示。  
  
 [in] `str`  
 工具提示文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法會處理事件。，否則， `FALSE`。  
  
##  <a name="a-nameremoveallitemsa--cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems  
 從清單] 和 [編輯方塊中刪除所有項目。  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>備註  
 移除所有項目從清單方塊和下拉式方塊控制項的編輯。  
  
##  <a name="a-nameselectitema--cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem  
 清單方塊中選取項目。  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
 [in] `bNotify`  
 `TRUE`通知下拉式方塊按鈕的選取項目。否則`FALSE`。  
  
 [in] `dwData`  
 清單方塊中的項目與相關的資料。  
  
 [in] `lpszText`  
 清單方塊中項目的文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameselectitemalla--cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll  
 選取一個項目在清單方塊的下拉式方塊按鈕具有指定的命令識別碼。  
  
```  
static BOOL SelectItemAll(
    UINT uiCmd,  
    int iIndex);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    DWORD_PTR dwData);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 包含在清單方塊的下拉式方塊按鈕的命令 ID。  
  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。 -1 值清單方塊中移除任何目前的選取範圍，並清除 [編輯] 方塊。  
  
 [in] `dwData`  
 清單方塊中的項目資料。  
  
 [in] `lpszText`  
 清單方塊中項目的文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameserializea--cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize  
 從封存讀取此物件，或將它寫入至封存檔。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `ar`  
 `CArchive`来序列化物件。  
  
### <a name="remarks"></a>備註  
 在設定`CArchive`物件會決定這個方法會讀取或寫入封存。  
  
##  <a name="a-namesetaccdataa--cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData  
 填入指定`CAccessibilityData`使用下拉式方塊按鈕的協助工具資料的物件。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParent`  
 下拉式方塊按鈕的父視窗。  
  
 [輸出] `data`  
 A`CAccessibilityData`收到下拉式方塊按鈕的協助工具資料的物件。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
##  <a name="a-namesetcenterverta--cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert  
 設定應用程式中的下拉式方塊按鈕的垂直位置。  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bCenterVert`  
 `TRUE`若要置中下拉式方塊按鈕，在工具列中。`FALSE`對齊下拉式方塊按鈕的工具列頂端。  
  
### <a name="remarks"></a>備註  
 根據預設，下拉式方塊按鈕頂端對齊。  
  
##  <a name="a-namesetcontextmenuida--cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID  
 設定下拉式方塊按鈕的捷徑功能表資源識別碼。  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiResID`  
 快顯功能表上的資源 id。  
  
##  <a name="a-namesetdropdownheighta--cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight  
 向下拖曳時，請設定清單方塊的高度。  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>參數  
 [in] `nHeight`  
 像素為單位，清單方塊的高度。  
  
### <a name="remarks"></a>備註  
 預設高度為 150 像素。  
  
##  <a name="a-namesetflatmodea--cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode  
 應用程式中設定下拉式方塊按鈕的平面樣式的外觀。  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bFlat`  
 `TRUE`平面樣式外觀。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 下拉式方塊按鈕的預設一般樣式是`FALSE`。  
  
##  <a name="a-namesetstylea--cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle  
 將指定的樣式設定的下拉式方塊按鈕，並重新繪製控制項，如果未停用。  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `nStyle`  
 位元組合 (OR) 工具列的樣式。  
  
### <a name="remarks"></a>備註  
 如需工具列按鈕樣式的清單，請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="a-namesettexta--cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComboBoxButton::SetText  
 設定編輯方塊的下拉式方塊按鈕的文字。  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszText`  
 其中包含編輯方塊的文字字串的指標。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說︰ 將放在工具列上的控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)




