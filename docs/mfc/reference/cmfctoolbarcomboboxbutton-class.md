---
title: CMFCToolBarComboBoxButton 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ddfa4d26ed0a4328714fbd1a921fe7c204ca3752
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377362"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 類別
包含下拉式方塊控制項的工具列按鈕 ( [CComboBox 類別](../../mfc/reference/ccombobox-class.md))。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|建構 `CMFCToolBarComboBoxButton`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](#additem)|將項目加入至下拉式方塊清單的結尾。|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|將項目加入至下拉式方塊的清單。 所指定的清單中的項目順序`Compare`。|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|比較兩個項目。 呼叫以排序的項目`AddSortedItems`將加入至下拉式方塊的清單。|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|建立新的編輯控制項的下拉式方塊按鈕。|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|從下拉式方塊的清單中刪除項目。|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|傳回包含指定之字串的項目索引。|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|讓指標回到下拉式方塊按鈕，並提供指定的命令識別碼。|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|傳回內嵌於下拉式方塊按鈕下拉式方塊控制項的指標。|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|在下拉式方塊中方塊的清單傳回的項目數。|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|尋找下拉式方塊按鈕具有指定的命令識別碼。 傳回的項目數下拉式方塊中該按鈕方塊清單。|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|在下拉式方塊中方塊的清單傳回選取之項目的索引。|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回選取之項目的索引下拉式方塊中的該按鈕方塊清單。|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|傳回的指標會內嵌在下拉式方塊按鈕之編輯控制項。|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|傳回在下拉式方塊中指定的索引相關聯的字串方塊的清單。|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回該按鈕的下拉式方塊的清單中的索引相關聯的字串。|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|傳回在下拉式方塊中指定的索引相關聯的 32 位元值方塊的清單。|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回該按鈕的下拉式方塊的清單中的索引相關聯的 32 位元值。|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|尋找下拉式方塊按鈕具有指定的命令識別碼。 擷取的 32 位元值相關聯的該按鈕，然後傳回 32 位元值的指標下拉式方塊的清單中的索引。|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|從下拉式方塊編輯控制項中傳回的文字。|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回編輯控制項，該按鈕的文字。|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|判斷應用程式中的下拉式方塊按鈕會置中對齊或對齊頂端的工具列。|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|判斷應用程式中的下拉式方塊按鈕是否有平面外觀。|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|移除所有項目從清單方塊，並編輯下拉式方塊控制項。|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|根據其索引、 32 位元值或字串，下拉式方塊中選取的項目，並通知下拉式方塊控制項選取項目有關。|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|尋找下拉式方塊按鈕具有指定的命令識別碼。 呼叫`SelectItem`按鈕根據其字串、 索引或 32 位元值的下拉式方塊中選取的項目。|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|指定應用程式中的下拉式方塊按鈕是垂直置中或與工具列的頂端對齊。|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|設定下拉式清單方塊的高度。|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|指定應用程式中的下拉式方塊按鈕是否有平面外觀。|  
  
## <a name="remarks"></a>備註  
 若要將下拉式方塊按鈕加入至工具列，請遵循下列步驟：  
  
 1. 為父工具列資源的按鈕保留假的資源 ID。  
  
 2. 建構`CMFCToolBarComboBoxButton`物件。  
  
 3. 在訊息處理常式來處理`AFX_WM_RESETTOOLBAR`訊息，請使用新的下拉式方塊按鈕取代 dummy 按鈕[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 如需詳細資訊，請參閱[逐步解說： 將工具列控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 如需下拉式方塊工具列按鈕的範例，請參閱範例專案 VisualStudioDemo。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCToolBarComboBoxButton`類別。 此範例示範如何啟用編輯和下拉式方塊、 應用程式中設定的垂直位置的下拉式方塊按鈕、 清單方塊的高度設定向下拖曳時、 應用程式中設定的下拉式方塊按鈕的平面樣式外觀並設定在編輯方塊的下拉式方塊按鈕的文字。 此程式碼片段是部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>  CMFCToolBarComboBoxButton::AddItem  
 將唯一的項目附加至清單方塊。  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszItem`  
 項目加入至清單方塊的文字。  
  
 [輸入] `dwData`  
 與要加入至清單方塊項目相關聯的資料。  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的最後一個項目索引。  
  
### <a name="remarks"></a>備註  
 當排序的清單方塊樣式時，請勿使用這個方法。  
  
 如果項目文字已經在清單方塊中，新的資料會儲存與現有的項目。 項目的搜尋不區分大小寫。  
  
##  <a name="addsorteditem"></a>  CMFCToolBarComboBoxButton::AddSortedItem  
 將項目加入至清單方塊中所定義的順序[比較](#compare)方法。  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszItem`  
 項目加入至清單方塊的文字。  
  
 [輸入] `dwData`  
 與要加入至清單方塊項目相關聯的資料。  
  
### <a name="return-value"></a>傳回值  
 已加入至清單方塊項目的索引。  
  
### <a name="remarks"></a>備註  
 使用此函式項目加入清單方塊，以特定順序。  
  
##  <a name="canbestretched"></a>  CMFCToolBarComboBoxButton::CanBeStretched  
 指出是否可以變更下拉式方塊按鈕的大小。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `TRUE`。  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>  CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 建構[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件。  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiID`  
 [新增] 按鈕的命令識別碼。  
  
 [輸入] `iImage`  
 [新增] 按鈕相關聯的映像的映像索引。  
  
 [輸入] `dwStyle`  
 [新增] 按鈕的樣式。  
  
 [輸入] `iWidth`  
 寬度 （以像素的 [新增] 按鈕）。  
  
### <a name="remarks"></a>備註  
 預設寬度是 150 個像素。  
  
 如需工具列按鈕樣式的清單，請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData  
 刪除使用者定義的資料。  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>備註  
 依預設這個方法沒有任何作用。 如果您想要刪除任何使用者定義的資料，請覆寫這個方法在衍生類別中。  
  
##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare  
 比較兩個字串。  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszItem1`  
 要比較的第一個字串。  
  
 [輸入] `lpszItem2`  
 要比較的第二個字串。  
  
### <a name="return-value"></a>傳回值  
 值，指出字串之間的區分大小寫的字典編撰關聯性。 下表列出可能的值：  
  
|值|描述|  
|-----------|-----------------|  
|\<0|第一個字串是否小於第二個。|  
|0|第一個字串值等於第二個。|  
|>0|第一個字串大於第二個。|  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以變更項目在清單方塊中的排序方式。  
  
 比較會區分大小寫。  
  
 這個方法只會從呼叫[AddSortedItem](#addsorteditem)方法。  
  
##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom  
 複製指定的狀態`CMFCToolBarComboBoxButton`目前的物件。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `src`  
 來源 `CMFCToolBarComboBoxButton` 物件。  
  
##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo  
 建立新的下拉式方塊的下拉式方塊按鈕。  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParent`  
 按鈕的父視窗的指標。  
  
 [輸入] `rect`  
 下拉式方塊的週框。  
  
### <a name="return-value"></a>傳回值  
 指向新的下拉式方塊如果該方法成功。否則， `NULL`。  
  
##  <a name="createedit"></a>  CMFCToolBarComboBoxButton::CreateEdit  
 建立新的編輯方塊的下拉式方塊按鈕。  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParent`  
 按鈕的父視窗的指標。  
  
 [輸入] `rect`  
 新的編輯方塊的週框。  
  
 [輸入] `dwEditStyle`  
 新的編輯方塊控制項樣式。  
  
### <a name="return-value"></a>傳回值  
 新的指標編輯方塊，如果該方法成功。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 建立新的編輯方塊的下拉式方塊按鈕時，架構會呼叫這個方法。 覆寫此方法以變更如何[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)建立。  
  
##  <a name="deleteitem"></a>  CMFCToolBarComboBoxButton::DeleteItem  
 從清單方塊中刪除指定的項目。  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 要刪除的項目以零為起始的索引。  
  
 [輸入] `dwData`  
 要刪除的項目與相關的資料。  
  
 [輸入] `lpszText`  
 要刪除之項目的文字。 如果有多個項目具有相同的文字，則會刪除第一個項目。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果項目已位於，而且已成功刪除;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData  
 重複的項目使用者定義的資料。  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>備註  
 依預設這個方法沒有任何作用。 如果您想要複製的任何使用者定義資料，請覆寫這個方法在衍生類別中。  
  
##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow  
 啟用或停用編輯] 和 [下拉式方塊。  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE` 若要啟用編輯和下拉式方塊。`FALSE`停用編輯] 和 [下拉式方塊。  
  
### <a name="remarks"></a>備註  
 停用時，這些控制項不能成為使用中，而且不能接受使用者輸入。  
  
##  <a name="exporttomenubutton"></a>  CMFCToolBarComboBoxButton::ExportToMenuButton  
 複製識別碼從應用程式的字串資料表指定功能表的下拉式方塊按鈕命令的字串。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `menuButton`  
 功能表按鈕的參考。  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
##  <a name="finditem"></a>  CMFCToolBarComboBoxButton::FindItem  
 傳回包含指定的字串清單方塊中的第一個項目的索引。  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszText`  
 要在清單方塊中搜尋文字。  
  
### <a name="return-value"></a>傳回值  
 項目; 索引或`CB_ERR`如果找不到項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getbycmd"></a>  CMFCToolBarComboBoxButton::GetByCmd  
 取得具有指定的命令 id。 下拉式方塊按鈕的指標  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 下拉式方塊按鈕的命令識別碼。  
  
 [輸入] `bIsFocus`  
 `TRUE` 若要只搜尋已取得焦點的按鈕;`FALSE`搜尋所有的按鈕。  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊按鈕; 指標或`NULL`如果找不到按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox  
 讓指標回到下拉式方塊中下拉式方塊按鈕。  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CComboBox 類別](../../mfc/reference/ccombobox-class.md)物件方法是否成功，否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcontextmenuid"></a>  CMFCToolBarComboBoxButton::GetContextMenuID  
 取得下拉式方塊按鈕的捷徑功能表上的資源識別碼。  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>傳回值  
 捷徑功能表上的資源 id。  
  
##  <a name="getcount"></a>  CMFCToolBarComboBoxButton::GetCount  
 清單方塊中，傳回的項目數。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單方塊中的項目數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcountall"></a>  CMFCToolBarComboBoxButton::GetCountAll  
 取得具有指定的命令 id。 下拉式方塊按鈕的清單方塊中的項目數  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 下拉式方塊按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 清單方塊; 中的項目數否則，`CB_ERR`如果找不到下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcursel"></a>  CMFCToolBarComboBoxButton::GetCurSel  
 清單方塊中，取得目前選取之項目的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中，目前選取項目的索引或`CB_ERR`如果不選取任何項目。  
  
### <a name="remarks"></a>備註  
 清單方塊索引以零為起始。  
  
##  <a name="getcurselall"></a>  CMFCToolBarComboBoxButton::GetCurSelAll  
 傳回目前選取之項目的索引中的下拉式清單方塊 按鈕具有指定的命令識別碼。  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 下拉式方塊按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中，目前選取項目的索引否則，`CB_ERR`如果選取任何項目或找不到下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
 清單方塊索引以零為起始。  
  
##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl  
 讓指標回到編輯方塊中下拉式方塊按鈕。  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>傳回值  
 指向的編輯方塊，如果該方法成功。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gethwnd"></a>  CMFCToolBarComboBoxButton::GetHwnd  
 傳回視窗控制代碼之下拉式方塊。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>傳回值  
 視窗控制代碼或`NULL`如果下拉式方塊不是視窗物件相關聯。  
  
##  <a name="getitem"></a>  CMFCToolBarComboBoxButton::GetItem  
 傳回與清單方塊中的指定索引處的項目相關聯的字串。  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 項目; 相關聯的字串指標否則，`NULL`如果索引參數無效，或者索引參數是-1，下拉式方塊中沒有選取項目。  
  
### <a name="remarks"></a>備註  
 索引參數為-1 會傳回目前選取之項目的字串。  
  
##  <a name="getitemall"></a>  CMFCToolBarComboBoxButton::GetItemAll  
 傳回具有指定的命令 id。 下拉式方塊按鈕的清單方塊中的指定索引處的項目相關聯的字串  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 下拉式方塊按鈕的命令識別碼。  
  
 [輸入] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功; 項目的字串的指標否則，`NULL`下拉式方塊按鈕索引不正確，如果不是找不到，或者索引是-1，下拉式方塊中沒有選取項目。  
  
### <a name="remarks"></a>備註  
 索引值-1 會傳回目前選取之項目的字串。  
  
##  <a name="getitemdata"></a>  CMFCToolBarComboBoxButton::GetItemData  
 傳回與清單方塊中指定索引處的項目相關聯的資料。  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 與項目; 相關聯的資料或 0，如果項目不存在。  
  
### <a name="remarks"></a>備註  
 索引參數為-1 會傳回目前選取的項目相關聯的資料。  
  
##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll  
 傳回具有特定的命令 id。 下拉式方塊按鈕的清單方塊中的特定索引處的項目相關聯的資料  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 下拉式方塊按鈕的命令識別碼。  
  
 [輸入] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功; 與項目相關聯的資料否則，0，表示指定的索引不正確，或找不到 CB_ERR 如果下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
 索引參數為-1 會傳回目前選取的項目相關聯的資料。  
  
##  <a name="getitemdataptrall"></a>  CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 傳回具有特定的命令 id。 下拉式方塊按鈕的清單方塊中的特定索引處的項目相關聯的資料 這項資料會傳回的指標。  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 下拉式方塊按鈕的命令識別碼。  
  
 [輸入] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功。 相關聯之項目的指標如果發生錯誤，否則為-1 或`NULL`如果找不到下拉式方塊按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getprompt"></a>  CMFCToolBarComboBoxButton::GetPrompt  
 傳回提示字串的下拉式方塊按鈕。  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>傳回值  
 提示的字串。  
  
### <a name="remarks"></a>備註  
 這個方法目前未實作。  
  
##  <a name="gettext"></a>  CMFCToolBarComboBoxButton::GetText  
 取得文字編輯方塊中。  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 編輯方塊中的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettextall"></a>  CMFCToolBarComboBoxButton::GetTextAll  
 取得具有指定的命令 id。 下拉式方塊按鈕的編輯方塊中的文字  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 特定的下拉式方塊按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功; 在編輯方塊中的文字否則， `NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus  
 表示下拉式方塊目前是否有焦點。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果下拉式方塊目前具有焦點。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法也會傳回`TRUE`如果下拉式方塊的任何子視窗目前具有焦點。  
  
##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert  
 傳回應用程式中的下拉式方塊按鈕的垂直位置。  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果按鈕會置中。，`FALSE`頂端對齊按鈕則。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isflatmode"></a>  CMFCToolBarComboBoxButton::IsFlatMode  
 傳回應用程式中的下拉式方塊按鈕的平面樣式外觀。  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果按鈕具有平面的樣式。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 下拉式方塊按鈕的預設一般樣式是 `FALSE.`  
  
##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf  
 指出指定的控制代碼是否與下拉式方塊按鈕，或其中一個子系相關聯。  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `hwnd`  
 視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果控制代碼相關聯，與下拉式方塊按鈕，或其中一個子系。否則， `FALSE`。  
  
##  <a name="isribbonbutton"></a>  CMFCToolBarComboBoxButton::IsRibbonButton  
 表示下拉式方塊按鈕是否位於功能區面板。  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一定是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法一律會傳回`FALSE`，這表示下拉式方塊按鈕永遠不會顯示在功能區面板上。  
  
##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible  
 傳回在下拉式方塊的可見性狀態 按鈕。  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊按鈕的可見性狀態。  
  
##  <a name="notifycommand"></a>  CMFCToolBarComboBoxButton::NotifyCommand  
 表示下拉式方塊按鈕是否處理訊息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iNotifyCode`  
 與命令相關聯的通知訊息。  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊按鈕是否會處理訊息。  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 加入按鈕時由架構呼叫**自訂** 對話方塊。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize  
 由架構呼叫以計算按鈕的大小。  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容顯示下拉式方塊按鈕。  
  
 [輸入] `sizeDefault`  
 下拉式方塊按鈕的預設大小。  
  
 [輸入] `bHorz`  
 為父工具列停駐狀態。 `TRUE` 當工具列是否停駐水平及`FALSE`當工具列是否停駐垂直。  
  
### <a name="return-value"></a>傳回值  
 A`SIZE`結構，其中包含下拉式方塊按鈕，像素為單位的維度。  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarComboBoxButton::OnChangeParentWnd  
 下拉式方塊按鈕插入新的工具列時由架構呼叫。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParent`  
 新的父工具列的指標。  
  
##  <a name="onclick"></a>  CMFCToolBarComboBoxButton::OnClick  
 當使用者按下下拉式方塊按鈕時由架構呼叫。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 下拉式方塊按鈕的父視窗的指標。  
  
 [輸入] `bDelay`  
 保留供衍生類別中使用。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果方法可以處理事件。，否則， `FALSE`。  
  
##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor  
 當使用者將父工具列色彩變更為設定下拉式方塊按鈕的色彩時由架構呼叫。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容顯示下拉式方塊按鈕。  
  
 [輸入] `nCtlColor`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 架構會使用來繪製下拉式方塊按鈕的背景的筆刷的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法也會設定下拉式方塊按鈕的文字色彩。  
  
##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw  
 由架構呼叫以繪製下拉式方塊按鈕，使用指定的樣式和選項。  
  
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
 [輸入] `Pdc`  
 裝置內容顯示的按鈕。  
  
 [輸入] `rect`  
 按鈕的週框。  
  
 [輸入] `pImages`  
 與按鈕相關聯的影像集合。  
  
 [輸入] `bHorz`  
 為父工具列停駐狀態。 `TRUE` 當工具列是否停駐水平及`FALSE`當工具列是否停駐垂直。  
  
 [輸入] `bCustomizeMode`  
 應用程式是否在自訂模式。  
  
 [輸入] `bHighlight`  
 是否要繪製反白顯示下拉式方塊按鈕。  
  
 [輸入] `bDrawBorder`  
 是否要繪製框線的下拉式方塊按鈕。  
  
 [輸入] `bGrayDisabledButtons`  
 `TRUE` 若要繪製陰影的已停用的按鈕。`FALSE`使用停用映像的集合。  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 由架構呼叫以繪製下拉式方塊按鈕**命令**窗格**自訂** 對話方塊。  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容顯示下拉式方塊按鈕。  
  
 [輸入] `rect`  
 下拉式方塊按鈕的週框。  
  
 [輸入] `bSelected`  
 `TRUE` 如果下拉式方塊按鈕已選取;否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 寬度 （以像素的下拉式方塊按鈕）。  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 由架構呼叫以設定下拉式方塊按鈕字型，應用程式字型變更時。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>  CMFCToolBarComboBoxButton::OnMove  
 由架構呼叫以為父工具列移動時，變更下拉式方塊按鈕的位置。  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>  CMFCToolBarComboBoxButton::OnShow  
 當您隱藏或顯示下拉式方塊按鈕時由架構呼叫。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bShow`  
 是否要隱藏或顯示下拉式方塊按鈕。  
  
##  <a name="onsize"></a>  CMFCToolBarComboBoxButton::OnSize  
 由架構呼叫以變更下拉式方塊按鈕的大小，為父工具列的大小變更時。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iSize`  
 下拉式方塊按鈕新的寬度。  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarComboBoxButton::OnUpdateToolTip  
 使用者變更下拉式方塊按鈕的工具提示時，由架構呼叫。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParent`  
 下拉式方塊按鈕的父視窗的指標。  
  
 [輸入] `iButtonIndex`  
 下拉式方塊按鈕的識別碼。  
  
 [輸入] `wndToolTip`  
 要與下拉式方塊按鈕的工具提示。  
  
 [輸入] `str`  
 工具提示文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果方法可以處理事件。，否則， `FALSE`。  
  
##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems  
 刪除清單] 和 [編輯方塊中的所有項目。  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>備註  
 移除所有項目從清單方塊，並編輯下拉式方塊控制項。  
  
##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem  
 清單方塊中選取項目。  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
 [輸入] `bNotify`  
 `TRUE` 通知下拉式方塊按鈕的選取項目。否則`FALSE`。  
  
 [輸入] `dwData`  
 清單方塊中的項目與相關的資料。  
  
 [輸入] `lpszText`  
 清單方塊中項目的文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果該方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll  
 選取的項目在清單方塊的下拉式方塊按鈕具有指定的命令識別碼。  
  
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
 [輸入] `uiCmd`  
 包含在清單方塊的下拉式方塊按鈕的命令識別碼。  
  
 [輸入] `iIndex`  
 清單方塊中的項目以零為起始的索引。 值為-1 移除任何目前的選擇清單方塊中，並清除 [編輯] 方塊。  
  
 [輸入] `dwData`  
 清單方塊中的項目資料。  
  
 [輸入] `lpszText`  
 清單方塊中項目的文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果該方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="serialize"></a>  CMFCToolBarComboBoxButton::Serialize  
 從封存讀取此物件，或將它寫入至封存。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `ar`  
 `CArchive`来序列化的物件。  
  
### <a name="remarks"></a>備註  
 中的設定`CArchive`物件決定這個方法會讀取或寫入封存。  
  
##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData  
 填入指定`CAccessibilityData`使用下拉式方塊按鈕的協助工具資料的物件。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pParent`  
 下拉式方塊按鈕的父視窗。  
  
 [輸出] `data`  
 A`CAccessibilityData`物件，可從下拉式方塊按鈕接收協助工具資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果該方法成功。否則`FALSE`。  
  
##  <a name="setcentervert"></a>  CMFCToolBarComboBoxButton::SetCenterVert  
 設定應用程式中的下拉式方塊按鈕的垂直位置。  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bCenterVert`  
 `TRUE` 若要置中下拉式方塊按鈕，在工具列中;`FALSE`對齊下拉式方塊按鈕上方的工具列。  
  
### <a name="remarks"></a>備註  
 根據預設，下拉式方塊按鈕對齊上方。  
  
##  <a name="setcontextmenuid"></a>  CMFCToolBarComboBoxButton::SetContextMenuID  
 設定下拉式方塊按鈕的捷徑功能表上的資源識別碼。  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiResID`  
 捷徑功能表上的資源 id。  
  
##  <a name="setdropdownheight"></a>  CMFCToolBarComboBoxButton::SetDropDownHeight  
 向下拖曳時，請設定清單方塊的高度。  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nHeight`  
 高度 （像素為單位的清單方塊）。  
  
### <a name="remarks"></a>備註  
 預設高度為 150 像素。  
  
##  <a name="setflatmode"></a>  CMFCToolBarComboBoxButton::SetFlatMode  
 應用程式中設定下拉式方塊按鈕的平面樣式的外觀。  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bFlat`  
 `TRUE` 平面樣式外觀。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 下拉式方塊按鈕的預設一般樣式是`FALSE`。  
  
##  <a name="setstyle"></a>  CMFCToolBarComboBoxButton::SetStyle  
 設定指定的樣式的下拉式方塊按鈕，並重新繪製控制項，如果未停用。  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nStyle`  
 的位元組合 (OR) 工具列的樣式。  
  
### <a name="remarks"></a>備註  
 如需工具列按鈕樣式的清單，請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>  CMFCToolBarComboBoxButton::SetText  
 設定編輯方塊的下拉式方塊按鈕的文字。  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszText`  
 字串，其中包含編輯方塊的文字指標。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



