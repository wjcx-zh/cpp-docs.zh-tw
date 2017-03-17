---
title: "CMFCRibbonPanel 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonPanel
- AFXRIBBONPANEL/CMFCRibbonPanel
- AFXRIBBONPANEL/CMFCRibbonPanel::CMFCRibbonPanel
- AFXRIBBONPANEL/CMFCRibbonPanel::Add
- AFXRIBBONPANEL/CMFCRibbonPanel::AddSeparator
- AFXRIBBONPANEL/CMFCRibbonPanel::AddToolBar
- AFXRIBBONPANEL/CMFCRibbonPanel::FindByData
- AFXRIBBONPANEL/CMFCRibbonPanel::FindByID
- AFXRIBBONPANEL/CMFCRibbonPanel::GetCaptionHeight
- AFXRIBBONPANEL/CMFCRibbonPanel::GetCount
- AFXRIBBONPANEL/CMFCRibbonPanel::GetData
- AFXRIBBONPANEL/CMFCRibbonPanel::GetDefaultButton
- AFXRIBBONPANEL/CMFCRibbonPanel::GetDroppedDown
- AFXRIBBONPANEL/CMFCRibbonPanel::GetElement
- AFXRIBBONPANEL/CMFCRibbonPanel::GetElements
- AFXRIBBONPANEL/CMFCRibbonPanel::GetElementsByID
- AFXRIBBONPANEL/CMFCRibbonPanel::GetFocused
- AFXRIBBONPANEL/CMFCRibbonPanel::GetGalleryRect
- AFXRIBBONPANEL/CMFCRibbonPanel::GetHighlighted
- AFXRIBBONPANEL/CMFCRibbonPanel::GetIndex
- AFXRIBBONPANEL/CMFCRibbonPanel::GetItemIDsList
- AFXRIBBONPANEL/CMFCRibbonPanel::GetName
- AFXRIBBONPANEL/CMFCRibbonPanel::GetParentButton
- AFXRIBBONPANEL/CMFCRibbonPanel::GetParentCategory
- AFXRIBBONPANEL/CMFCRibbonPanel::GetParentMenuBar
- AFXRIBBONPANEL/CMFCRibbonPanel::GetPreferedMenuLocation
- AFXRIBBONPANEL/CMFCRibbonPanel::GetPressed
- AFXRIBBONPANEL/CMFCRibbonPanel::GetRect
- AFXRIBBONPANEL/CMFCRibbonPanel::GetVisibleElements
- AFXRIBBONPANEL/CMFCRibbonPanel::HasElement
- AFXRIBBONPANEL/CMFCRibbonPanel::HitTest
- AFXRIBBONPANEL/CMFCRibbonPanel::HitTestEx
- AFXRIBBONPANEL/CMFCRibbonPanel::Insert
- AFXRIBBONPANEL/CMFCRibbonPanel::InsertSeparator
- AFXRIBBONPANEL/CMFCRibbonPanel::IsCenterColumnVert
- AFXRIBBONPANEL/CMFCRibbonPanel::IsCollapsed
- AFXRIBBONPANEL/CMFCRibbonPanel::IsHighlighted
- AFXRIBBONPANEL/CMFCRibbonPanel::IsJustifyColumns
- AFXRIBBONPANEL/CMFCRibbonPanel::IsMainPanel
- AFXRIBBONPANEL/CMFCRibbonPanel::IsMenuMode
- AFXRIBBONPANEL/CMFCRibbonPanel::MakeGalleryItemVisible
- AFXRIBBONPANEL/CMFCRibbonPanel::OnKey
- AFXRIBBONPANEL/CMFCRibbonPanel::RecalcWidths
- AFXRIBBONPANEL/CMFCRibbonPanel::Remove
- AFXRIBBONPANEL/CMFCRibbonPanel::RemoveAll
- AFXRIBBONPANEL/CMFCRibbonPanel::Replace
- AFXRIBBONPANEL/CMFCRibbonPanel::ReplaceByID
- AFXRIBBONPANEL/CMFCRibbonPanel::SetCenterColumnVert
- AFXRIBBONPANEL/CMFCRibbonPanel::SetData
- AFXRIBBONPANEL/CMFCRibbonPanel::SetElementMenu
- AFXRIBBONPANEL/CMFCRibbonPanel::SetElementRTC
- AFXRIBBONPANEL/CMFCRibbonPanel::SetElementRTCByID
- AFXRIBBONPANEL/CMFCRibbonPanel::SetFocused
- AFXRIBBONPANEL/CMFCRibbonPanel::SetJustifyColumns
- AFXRIBBONPANEL/CMFCRibbonPanel::SetKeys
- AFXRIBBONPANEL/CMFCRibbonPanel::ShowPopup
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonPanel class
ms.assetid: 51d70749-1140-4386-b103-f14082049ba6
caps.latest.revision: 34
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
ms.openlocfilehash: 1f833e1fa59f733734da321718d5db73377fa4bd
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonpanel-class"></a>CMFCRibbonPanel 類別
實作包含一組功能區項目的面板。 繪製面板時，會在指定的面板大小下，顯示盡可能多的項目。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonPanel : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonPanel::CMFCRibbonPanel](#cmfcribbonpanel)|建構並初始化 `CMFCRibbonPanel` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonPanel::Add](#add)|將功能區項目加入面板。|  
|[CMFCRibbonPanel::AddSeparator](#addseparator)|將功能區面板中的分隔符號。|  
|[CMFCRibbonPanel::AddToolBar](#addtoolbar)|將工具列新增至功能區面板。|  
|[CMFCRibbonPanel::FindByData](#findbydata)||  
|[CMFCRibbonPanel::FindByID](#findbyid)|傳回指定的命令識別碼識別項目。|  
|[CMFCRibbonPanel::GetCaptionHeight](#getcaptionheight)||  
|[CMFCRibbonPanel::GetCount](#getcount)|在功能區面板中傳回的項目數。|  
|[CMFCRibbonPanel::GetData](#getdata)|傳回與面板相關聯的使用者定義資料。|  
|[CMFCRibbonPanel::GetDefaultButton](#getdefaultbutton)||  
|[CMFCRibbonPanel::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonPanel::GetElement](#getelement)|傳回位於指定索引處的功能區項目。|  
|[CMFCRibbonPanel::GetElements](#getelements)|擷取包含在功能區面板中的所有項目。|  
|[CMFCRibbonPanel::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonPanel::GetFocused](#getfocused)|傳回具有焦點的項目。|  
|[CMFCRibbonPanel::GetGalleryRect](#getgalleryrect)|傳回組件庫項目的周框矩形。|  
|[CMFCRibbonPanel::GetHighlighted](#gethighlighted)||  
|[CMFCRibbonPanel::GetIndex](#getindex)||  
|[CMFCRibbonPanel::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonPanel::GetName](#getname)||  
|[CMFCRibbonPanel::GetParentButton](#getparentbutton)||  
|[CMFCRibbonPanel::GetParentCategory](#getparentcategory)|傳回父類別的功能區面板。|  
|[CMFCRibbonPanel::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonPanel::GetPreferedMenuLocation](#getpreferedmenulocation)||  
|[CMFCRibbonPanel::GetPressed](#getpressed)||  
|[CMFCRibbonPanel::GetRect](#getrect)||  
|[CMFCRibbonPanel::GetVisibleElements](#getvisibleelements)|取得可見項目的陣列。|  
|[CMFCRibbonPanel::HasElement](#haselement)||  
|[CMFCRibbonPanel::HitTest](#hittest)||  
|[CMFCRibbonPanel::HitTestEx](#hittestex)||  
|[CMFCRibbonPanel::Insert](#insert)|將功能區項目插入位於指定位置。|  
|[CMFCRibbonPanel::InsertSeparator](#insertseparator)|在指定位置插入分隔符號。|  
|[CMFCRibbonPanel::IsCenterColumnVert](#iscentercolumnvert)|是否所有面板項目應該垂直置都中 （對齊），以指定資料行。|  
|[CMFCRibbonPanel::IsCollapsed](#iscollapsed)||  
|[CMFCRibbonPanel::IsHighlighted](#ishighlighted)||  
|[CMFCRibbonPanel::IsJustifyColumns](#isjustifycolumns)|指定面板的所有資料行是否具有相同的寬度。|  
|[CMFCRibbonPanel::IsMainPanel](#ismainpanel)||  
|[CMFCRibbonPanel::IsMenuMode](#ismenumode)||  
|[CMFCRibbonPanel::MakeGalleryItemVisible](#makegalleryitemvisible)|捲動的組件庫中看見指定的功能區項目。|  
|[CMFCRibbonPanel::OnKey](#onkey)||  
|[CMFCRibbonPanel::RecalcWidths](#recalcwidths)||  
|[CMFCRibbonPanel::Remove](#remove)|移除，並選擇性地刪除位於指定索引處的項目。|  
|[CMFCRibbonPanel::RemoveAll](#removeall)|從功能區面板中移除所有項目。|  
|[CMFCRibbonPanel::Replace](#replace)|一個項目取代另一個根據其各自的索引值。|  
|[CMFCRibbonPanel::ReplaceByID](#replacebyid)|一個項目取代另一個根據指定的命令識別碼。|  
|[CMFCRibbonPanel::SetCenterColumnVert](#setcentercolumnvert)|排序資料行垂直對齊項目 [面板]。|  
|[CMFCRibbonPanel::SetData](#setdata)|將使用者定義的資料與功能區面板。|  
|[CMFCRibbonPanel::SetElementMenu](#setelementmenu)|將快顯功能表指派項目具有指定的命令識別碼。|  
|[CMFCRibbonPanel::SetElementRTC](#setelementrtc)|將指定的功能區面板提供執行階段類別資訊的功能區項目。|  
|[CMFCRibbonPanel::SetElementRTCByID](#setelementrtcbyid)|將指定的功能區面板提供執行階段類別資訊的功能區項目。|  
|[CMFCRibbonPanel::SetFocused](#setfocused)|將焦點移到指定的功能區項目。|  
|[CMFCRibbonPanel::SetJustifyColumns](#setjustifycolumns)|啟用或停用資料行對齊方式。|  
|[CMFCRibbonPanel::SetKeys](#setkeys)|設定顯示功能區面板的鍵盤快速鍵。|  
|[CMFCRibbonPanel::ShowPopup](#showpopup)||  
  
## <a name="remarks"></a>備註  
 功能區面板是您在功能區類別內建立的相關工作的邏輯群組。 為功能區變更的大小，面板版面配置會自動調整顯示盡可能多的項目。  
  
 您可以取得功能區面板中所包含功能區類別藉由呼叫[CMFCRibbonCategory::GetPanel](../../mfc/reference/cmfcribboncategory-class.md#getpanel)方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定`CMFCRibbonPanel`使用各種方法的物件`CMFCRibbonPanel`類別。 此範例示範如何設定顯示功能區面板的鍵盤快速鍵、 垂直對齊面板中的元素，依資料行，並啟用資料行對齊方式。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&10;](../../mfc/reference/codesnippet/cpp/cmfcribbonpanel-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonPanel.h  
  
##  <a name="add"></a>CMFCRibbonPanel::Add  
 將指定的功能區項目附加至功能區面板中所包含的功能區項目的陣列。  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `pElem`  
 功能區元素的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="addseparator"></a>CMFCRibbonPanel::AddSeparator  
 將功能區面板中的分隔符號。  
  
```  
virtual void AddSeparator();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法可以加入至功能區面板的分隔符號。 將加入分隔符號，由先前呼叫所加入的功能區項目旁邊[CMFCRibbonPanel::Add](#add)。 若要插入的指定位置的分隔符號，呼叫[CMFCRibbonPanel::InsertSeparator](#insertseparator)。  
  
##  <a name="addtoolbar"></a>CMFCRibbonPanel::AddToolBar  
 將工具列新增至功能區面板。  
  
```  
CMFCRibbonButtonsGroup* AddToolBar(
UINT uiToolbarResID,  
UINT uiColdResID = 0,  
UINT uiHotResID = 0,  
UINT uiDisabledResID = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiToolbarResID`  
 指定要新增工具列資源識別碼。  
  
 [in] `uiColdResID`  
 指定冷的工具列影像的資源識別碼。  
  
 [in] `uiHotResID`  
 指定工具列的作用中影像的資源識別碼。  
  
 [in] `uiDisabledResID`  
 指定已停用的工具列影像的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 呼叫這個方法，將工具列新增至功能區面板。 工具列會加入先前呼叫所加入的功能區項目旁邊[CMFCRibbonPanel::Add](#add)。  
  
### <a name="remarks"></a>備註  
 如需有關工具列、 作用中影像、 冷的映像和停用映像的詳細資訊，請參閱[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)。  
  
##  <a name="cmfcribbonpanel"></a>CMFCRibbonPanel::CMFCRibbonPanel  
 建構並初始化[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)物件。  
  
```  
CMFCRibbonPanel(
LPCTSTR lpszName = NULL,  
HICON hIcon = NULL);  
  
CMFCRibbonPanel(CMFCRibbonGallery* pPaletteButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszName`  
 功能區面板名稱。  
  
 [in] `hIcon`  
 功能區面板的預設按鈕的圖示的控制代碼。  
  
 [in] `pPaletteButton`  
 功能區組件庫功能區面板的指標。  
  
##  <a name="findbydata"></a>CMFCRibbonPanel::FindByData  
 擷取與指定的資料相關聯的功能區項目。  
  
```  
CMFCRibbonBaseElement* FindByData(DWORD_PTR dwData) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `dwData`  
 使用功能區項目相關聯的資料。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，功能區項目的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="findbyid"></a>CMFCRibbonPanel::FindByID  
 擷取指定的命令識別碼所識別的功能區項目  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 功能區項目的命令 ID。  
  
### <a name="return-value"></a>傳回值  
 功能區項目所指定的命令 ID。否則`NULL`如果沒有任何功能區項目會識別出具有指定的命令 id。  
  
##  <a name="getcaptionheight"></a>CMFCRibbonPanel::GetCaptionHeight  
 擷取功能區面板的標題的高度。  
  
```  
int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素功能區面板的標題。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcount"></a>CMFCRibbonPanel::GetCount  
 擷取包含在功能區面板中的功能區項目數目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區面板中所包含的功能區項目數目。  
  
##  <a name="getdata"></a>CMFCRibbonPanel::GetData  
 傳回與面板相關聯的使用者定義資料。  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>傳回值  
 與面板相關聯的使用者定義的資料。  
  
##  <a name="getdefaultbutton"></a>CMFCRibbonPanel::GetDefaultButton  
 擷取功能區面板的預設按鈕。  
  
```  
CMFCRibbonButton& GetDefaultButton();
```  
  
### <a name="return-value"></a>傳回值  
 功能區面板的 [預設] 按鈕。  
  
### <a name="remarks"></a>備註  
 在功能區面板有足夠的空間可顯示其功能區項目時，會顯示 [預設] 按鈕。  
  
##  <a name="getdroppeddown"></a>CMFCRibbonPanel::GetDroppedDown  
 如果其快顯功能表下拉，擷取功能區項目的指標。  
  
```  
CMFCRibbonBaseElement* GetDroppedDown() const;  
```  
  
### <a name="return-value"></a>傳回值  
 具有下拉式; 其快顯功能表上的功能區元素的指標否則`NULL`沒有功能區項目是否有其落下的快顯功能表。  
  
### <a name="remarks"></a>備註  
 測試功能區面板中所包含的功能區項目。  
  
##  <a name="getelement"></a>CMFCRibbonPanel::GetElement  
 傳回位於指定索引處的功能區項目。  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定要擷取之項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 基底功能區元素的有效指標位於位置`nIndex`在功能區面板或`NULL`如果沒有指定索引處的項目。  
  
##  <a name="getelements"></a>CMFCRibbonPanel::GetElements  
 擷取包含在功能區面板中的所有功能區項目。  
  
```  
void GetElements(CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `arElements`  
 要填滿功能區面板中所包含的所有功能區項目的陣列。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getelementsbyid"></a>CMFCRibbonPanel::GetElementsByID  
 加入功能區項目具有指定的命令 ID，到指定的陣列。  
  
```  
void GetElementsByID(
UINT uiCmdID,  
CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 功能區項目的命令 ID。  
  
 [in] `arElements`  
 功能區項目的陣列。  
  
### <a name="remarks"></a>備註  
 測試功能區面板中所包含的功能區項目。  
  
##  <a name="gethighlighted"></a>CMFCRibbonPanel::GetHighlighted  
 擷取會反白顯示功能區面板的功能區項目。  
  
```  
CMFCRibbonBaseElement* GetHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標會反白顯示功能區面板的功能區項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getindex"></a>CMFCRibbonPanel::GetIndex  
 擷取指定的功能區項目之以零起始的索引，從功能區面板中所包含的功能區項目的陣列。  
  
```  
virtual int GetIndex(CMFCRibbonBaseElement* pElem) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pElem`  
 功能區元素的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功; 指定的功能區項目的以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getitemidslist"></a>CMFCRibbonPanel::GetItemIDsList  
 擷取在功能區面板中的所有功能區項目的命令 Id。  
  
```  
void GetItemIDsList(CList<UINT, UINT>& lstItems) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `lstItems`  
 功能區項目包含在功能區面板中的命令 Id 的清單。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getname"></a>CMFCRibbonPanel::GetName  
 擷取功能區面板名稱。  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區面板名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getparentbutton"></a>CMFCRibbonPanel::GetParentButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getparentcategory"></a>CMFCRibbonPanel::GetParentCategory  
 傳回父類別的功能區面板。  
  
```  
CMFCRibbonCategory* GetParentCategory() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含此功能區面板的功能區類別指標。  
  
##  <a name="getparentmenubar"></a>CMFCRibbonPanel::GetParentMenuBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getpreferedmenulocation"></a>CMFCRibbonPanel::GetPreferedMenuLocation  
 擷取快顯功能表功能區面板的慣用的顯示的矩形。  
  
```  
virtual BOOL GetPreferedMenuLocation(CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rect`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法一律會傳回 `FALSE`。 覆寫這個方法來擷取快顯功能表的功能區面板的慣用的顯示矩形。  
  
##  <a name="getpressed"></a>CMFCRibbonPanel::GetPressed  
 如果使用者目前按下它會擷取功能區面板上的功能區元素的指標。  
  
```  
CMFCRibbonBaseElement* GetPressed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果使用者目前按下，功能區元素的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrect"></a>CMFCRibbonPanel::GetRect  
 擷取功能區面板的顯示矩形。  
  
```  
const CRect& GetRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區面板顯示矩形。  
  
### <a name="remarks"></a>備註  
  
##  <a name="haselement"></a>CMFCRibbonPanel::HasElement  
 表示功能區面板是否包含指定的功能區項目。  
  
```  
BOOL HasElement(const CMFCRibbonBaseElement* pElem) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pElem`  
 功能區元素的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能區面板包含指定的功能區的項目。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="highlight"></a>CMFCRibbonPanel::Highlight  
 設定為醒目提示色彩選取功能區面板，以及指定點的功能區項目。  
  
```  
virtual void Highlight(
BOOL bHighlight,  
CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHighlight`  
 `TRUE`若要反白顯示功能區面板。`FALSE`到 unhighlight 功能區面板。  
  
 [in] `point`  
 指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hittest"></a>CMFCRibbonPanel::HitTest  
 如果指定的點位於，擷取功能區項目。  
  
```  
virtual CMFCRibbonBaseElement* HitTest(
CPoint point,  
BOOL bCheckPanelCaption = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指標，相對於視窗左上角的 x 和 y 座標。  
  
 [in] `bCheckPanelCaption`  
 `TRUE`若要測試的功能區面板標題中。否則`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 功能區項目指定的點位於; 如果指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
 測試功能區面板中所包含的功能區項目。  
  
##  <a name="hittestex"></a>CMFCRibbonPanel::HitTestEx  
 擷取具有指定的點中的功能區項目以零為起始索引。  
  
```  
virtual int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="return-value"></a>傳回值  
 包含指定的點中，功能區項目的以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 測試功能區面板中所包含的功能區項目。  
  
##  <a name="insert"></a>CMFCRibbonPanel::Insert  
 指定的功能區項目指定位置插入陣列中的功能區項目包含在功能區面板中。  
  
```  
virtual BOOL Insert(
CMFCRibbonBaseElement* pElem,  
int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `pElem`  
 功能區元素的指標。  
  
 [in] `nIndex`  
 以零為起始的值，範圍從-1 到陣列中所包含的功能區項目數目。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能區項目已插入可順利啟動。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果值`nIndex`為-1，或者如果`nIndex`等於陣列中的功能區元素的數目，則指定的功能區項目加入至陣列的結尾。 如果值`nIndex`是超出範圍，該方法會失敗。  
  
##  <a name="insertseparator"></a>CMFCRibbonPanel::InsertSeparator  
 在指定位置插入分隔符號。  
  
```  
virtual BOOL InsertSeparator(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定分隔符號插入的位置以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果分隔符號插入可順利啟動。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法所指定的位置插入分隔符號`nIndex`。 若要插入最近新增的功能區項目旁邊的分隔符號，請呼叫[CMFCRibbonPanel::AddSeparator](#addseparator)。  
  
##  <a name="iscentercolumnvert"></a>CMFCRibbonPanel::IsCenterColumnVert  
 表示功能區元素的垂直位置會置中對齊其顯示矩形內。  
  
```  
BOOL IsCenterColumnVert() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果垂直放置的功能區項目是內部置中對齊其顯示矩形。否則`FALSE`。  
  
##  <a name="iscollapsed"></a>CMFCRibbonPanel::IsCollapsed  
 指出是否顯示功能區面板的大小最小化，以水平方向。  
  
```  
BOOL IsCollapsed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果顯示的功能區面板大小降到最低的水平方向。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 當功能區面板摺疊時，它只會顯示其預設按鈕、 其名稱和下拉箭號。  
  
##  <a name="ishighlighted"></a>CMFCRibbonPanel::IsHighlighted  
 表示功能區面板的顯示會反白顯示。  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能區面板的顯示會反白顯示。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 當指標位於其上方時，會反白顯示功能區面板的顯示。  
  
##  <a name="isjustifycolumns"></a>CMFCRibbonPanel::IsJustifyColumns  
 指出是否顯示維度的功能區面板中的相同資料行中的功能區項目，設定成相同寬度。  
  
```  
BOOL IsJustifyColumns() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果顯示的維度相同的資料行，在功能區面板中的功能區項目會設為相同的寬度;否則`FALSE`。  
  
##  <a name="ismainpanel"></a>CMFCRibbonPanel::IsMainPanel  
 指出功能區面板是否為主要的功能區面板。  
  
```  
virtual BOOL IsMainPanel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法一律會傳回 `FALSE`。 覆寫此方法表示功能區面板是否為主要的功能區面板。  
  
 主要的功能區面板會顯示在使用者選取的應用程式按鈕時。  
  
##  <a name="ismenumode"></a>CMFCRibbonPanel::IsMenuMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onkey"></a>CMFCRibbonPanel::OnKey  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>參數  
 [in] `nChar`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="recalcwidths"></a>CMFCRibbonPanel::RecalcWidths  
 重新計算功能區面板的每個顯示配置組態的寬度。  
  
```  
virtual void RecalcWidths(
CDC* pDC,  
int nHeight);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 功能區面板的裝置內容的指標。  
  
 [in] `nHeight`  
 功能區面板的高度。  
  
### <a name="remarks"></a>備註  
 在功能區面板可用的寬度變更時變更其版面配置設定。  
  
##  <a name="remove"></a>CMFCRibbonPanel::Remove  
 移除，並選擇性地刪除位於指定索引處的項目。  
  
```  
BOOL Remove(
int nIndex,  
BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定從功能區面板中移除項目的以零為起始的索引。  
  
 [in] `bDelete`  
 `TRUE`若要刪除的項目被移除。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果移除及刪除的項目 (如果`bDelete`是`TRUE`);`FALSE`如果無法移除項目，或如果沒有任何功能區項目位在`nIndex`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法從功能區面板中移除的項目。  
  
##  <a name="removeall"></a>CMFCRibbonPanel::RemoveAll  
 從功能區面板中刪除所有的功能區項目。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 所有的功能區項目從功能區面板中刪除或終結。  
  
##  <a name="replace"></a>CMFCRibbonPanel::Replace  
 一個項目取代另一個根據其索引值。  
  
```  
BOOL Replace(
int nIndex,  
CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定要取代之項目的以零為起始的索引。  
  
 [in][out]`pElem`  
 有效的指標取代原始的項目中的項目。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果原始的功能區項目已成功取代新的功能區項目。`FALSE`未被取代的功能區項目，或如果沒有指定索引處的項目。  
  
### <a name="remarks"></a>備註  
 若要命令 ID 所取代的功能區項目，呼叫[CMFCRibbonPanel::ReplaceByID](#replacebyid)。  
  
##  <a name="replacebyid"></a>CMFCRibbonPanel::ReplaceByID  
 一個項目取代另一個根據指定的命令識別碼。  
  
```  
BOOL ReplaceByID(
UINT uiCmdID,  
CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 指定要取代之項目的命令 ID。  
  
 [in][out]`pElem`  
 有效的項目將會取代原始項目的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果原始的功能區項目已成功取代新的功能區項目。`FALSE`未被取代的功能區項目，或具有指定的命令 ID 的項目確實存在。  
  
### <a name="remarks"></a>備註  
 若要取代的功能區項目，根據位置，請呼叫[CMFCRibbonPanel::Replace](#replace)。  
  
##  <a name="setcentercolumnvert"></a>CMFCRibbonPanel::SetCenterColumnVert  
 啟用或停用的功能區項目，其顯示矩形內的垂直位置置中。  
  
```  
void SetCenterColumnVert(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 `TRUE`若要垂直位置的功能區項目內的顯示矩形。`FALSE`停用此功能。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setdata"></a>CMFCRibbonPanel::SetData  
 將使用者定義的資料與功能區面板。  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwData`  
 指定要設定的使用者定義資料。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法將使用者自訂資料與功能區面板。  
  
##  <a name="setelementmenu"></a>CMFCRibbonPanel::SetElementMenu  
 將快顯功能表指派項目具有指定的命令識別碼。  
  
```  
BOOL SetElementMenu(
UINT uiCmdID,  
HMENU hMenu,  
BOOL bIsDefautCommand = FALSE,  
BOOL bRightAlign = FALSE);

 
BOOL SetElementMenu(
UINT uiCmdID,  
UINT uiMenuResID,  
BOOL bIsDefautCommand = FALSE,  
BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 指定命令識別碼的功能表會加入其中的功能區項目。  
  
 [in] `hMenu`  
 指定將新增至功能區面板的 [視窗] 功能表的控制代碼。  
  
 [in] `bIsDefautCommand`  
 `TRUE`若要指定如果按一下功能區項目，則應該執行的功能區項目相關聯的命令。 在此情況下，當使用者按一下功能區項目旁的箭號，是只有開啟功能表。 `FALSE`若要指定是否按下功能區項目，不應執行的功能區項目相關聯的命令。 在此情況下，不論在使用者按一下此項目會出現快顯功能表。  
  
 [in] `bRightAlign`  
 `TRUE`若要指定快顯功能表為靠右對齊。否則， `FALSE`。  
  
 [in] `uiMenuResID`  
 指定要加入至功能區面板功能表的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能表已指派給功能區項目。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來將快顯功能表指派給功能區項目具有指定的命令識別碼。  
  
##  <a name="setelementrtc"></a>CMFCRibbonPanel::SetElementRTC  
 加入功能區項目所指定的功能區面板提供執行階段類別資訊。  
  
```  
CMFCRibbonBaseElement* SetElementRTC(
int nIndex,  
CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定要加入功能區項目的以零為起始的索引。  
  
 [in][out]`pRTC`  
 執行階段類別資訊加入至功能區面板功能區項目的指標。  
  
### <a name="return-value"></a>傳回值  
 使用指定的執行階段類別資訊建立功能區項目。  
  
### <a name="remarks"></a>備註  
 如果您想要將自訂項目 （例如，色彩按鈕） 加入至功能區面板，您必須指定自訂的項目執行階段類別資訊。 功能區儲存這項資訊、 建立自訂的項目，並取代現有項目位於 （識別） 指定的命令 id。 功能區接著會傳回新建立的項目指標。  
  
##  <a name="setelementrtcbyid"></a>CMFCRibbonPanel::SetElementRTCByID  
 將功能區項目所指定的功能區面板提供執行階段類別資訊。  
  
```  
CMFCRibbonBaseElement* SetElementRTCByID(
UINT uiCmdID,  
CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 指定要新增的命令識別碼的功能區項目。  
  
 [in][out]`pRTC`  
 加入至功能區面板的功能區項目相關聯的執行階段類別資訊的指標。  
  
### <a name="return-value"></a>傳回值  
 使用指定的執行階段類別資訊建立功能區項目。  
  
### <a name="remarks"></a>備註  
 如果您想要將自訂項目 （例如，色彩按鈕） 加入至功能區面板，您必須指定自訂的項目執行階段類別資訊。 功能區儲存這項資訊、 建立自訂項目，並取代現有的項目，位於所指定的命令 id。 然後，它會傳回指標至新建立的項目。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetElementRTCByID`方法︰  
  
```  
 
// Load and add toolbar with standard buttons. This toolbar  
// should display a custom color button with id ID_CHAR_COLOR:  
 
pPanel->AddToolBar(IDR_MAINFRAME,
    IDB_MAINFRAME256);

CMFCRibbonColorButton* pColorButton = 
(CMFCRibbonColorButton*)pPanel->SetElementRTCByID(
ID_CHAR_COLOR,
    RUNTIME_CLASS (CMFCRibbonColorButton));

 
// SetElementRTCByID sets runtime class and returns a pointer  
// to the newly created custom button,
    which can be set up immediately:  
pColorButton->EnableAutomaticButton(_T("Automatic"),
    RGB (0,
    0,
    0));  
```  
  
##  <a name="setjustifycolumns"></a>CMFCRibbonPanel::SetJustifyColumns  
 啟用或停用的相同資料行中的功能區項目的寬度調整。  
  
```  
void SetJustifyColumns(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 `TRUE`若要調整為寬度的最大的功能區項目資料行，在相同的資料行中的功能區項目的寬度`FALSE`停用此寬度調整。  
  
### <a name="remarks"></a>備註  
 在功能區面板中啟用這項功能時，相同的資料行中的功能區項目的寬度會調整為最大的功能區項目，在相同的資料行的寬度。  
  
##  <a name="setkeys"></a>CMFCRibbonPanel::SetKeys  
 設定預設按鈕的功能區面板 keytip。  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszKeys`  
 預設按鈕的功能區面板 keytip。  
  
### <a name="remarks"></a>備註  
 在功能區面板有足夠的空間可顯示其功能區項目時，會顯示 [預設] 按鈕。  
  
##  <a name="showpopup"></a>CMFCRibbonPanel::ShowPopup  
 建立並顯示快顯功能表功能區面板。  
  
```  
CMFCRibbonPanelMenu* ShowPopup(CMFCRibbonDefaultPanelButton* pButton = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 功能區面板的預設按鈕的指標。  
  
### <a name="return-value"></a>傳回值  
 指標的快顯功能表功能區面板，如果方法成功。否則`NULL`。  
  
### <a name="remarks"></a>備註  
 功能區面板的快顯功能表功能區面板顯示摺疊時才可用。  
  
##  <a name="setfocused"></a>CMFCRibbonPanel::SetFocused  
 將焦點移到指定的功能區項目。  
  
```  
void SetFocused(CMFCRibbonBaseElement* pNewFocus);
```  
  
### <a name="parameters"></a>參數  
 `pNewFocus`  
 焦點功能區項目的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="makegalleryitemvisible"></a>CMFCRibbonPanel::MakeGalleryItemVisible  
 捲動的組件庫中看見指定的功能區項目。  
  
```  
void MakeGalleryItemVisible(CMFCRibbonBaseElement* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 顯示功能區項目的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="iswindows7look"></a>CMFCRibbonPanel::IsWindows7Look  
 表示父功能區是否有 Windows 7 尋找 （矩形的小型應用程式按鈕）。  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果父功能區看起來; Windows 7否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getvisibleelements"></a>CMFCRibbonPanel::GetVisibleElements  
 擷取可見項目的陣列。  
  
```  
void GetVisibleElements(
CArray<CMFCRibbonBaseElement*,  
CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>參數  
 `arElements`  
 函式傳回時，此參數會包含可見的項目陣列。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getgalleryrect"></a>CMFCRibbonPanel::GetGalleryRect  
 傳回組件庫項目的周框矩形。  
  
```  
CRect GetGalleryRect();
```  
  
### <a name="return-value"></a>傳回值  
 大小，此面板中的圖庫項目的位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getfocused"></a>CMFCRibbonPanel::GetFocused  
 傳回具有焦點的項目。  
  
```  
CMFCRibbonBaseElement* GetFocused() const;  
```  
  
### <a name="return-value"></a>傳回值  
 具有焦點的項目之指標或`NULL`。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [CMFCRibbonCategory 類別](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)

