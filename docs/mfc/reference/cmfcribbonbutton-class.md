---
title: "CMFCRibbonButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButton class
ms.assetid: 732e941c-9504-4b83-a691-d18075965d53
caps.latest.revision: 42
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
ms.openlocfilehash: 08672f10cf67a773f2af8d12130c4e3f5b497e11
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonbutton-class"></a>CMFCRibbonButton 類別
`CMFCRibbonButton` 類別實作可以放置在功能區列項目 (例如面板、快速存取工具列和快顯功能表) 上的按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonButton : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonButton::CMFCRibbonButton](#cmfcribbonbutton)|建構功能區按鈕物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonButton::AddSubItem](#addsubitem)|將功能表項目加入至與按鈕相關聯的快顯功能表。|  
|[CMFCRibbonButton::CanBeStretched](#canbestretched)|(覆寫[CMFCRibbonBaseElement::CanBeStretched](../../mfc/reference/cmfcribbonbaseelement-class.md#canbestretched)。)|  
|[CMFCRibbonButton::CleanUpSizes](#cleanupsizes)|(覆寫[CMFCRibbonBaseElement::CleanUpSizes](../../mfc/reference/cmfcribbonbaseelement-class.md#cleanupsizes)。)|  
|[CMFCRibbonButton::ClosePopupMenu](#closepopupmenu)|(覆寫[CMFCRibbonBaseElement::ClosePopupMenu](../../mfc/reference/cmfcribbonbaseelement-class.md#closepopupmenu)。)|  
|[CMFCRibbonButton::DrawBottomText](#drawbottomtext)||  
|[CMFCRibbonButton::DrawImage](#drawimage)|(覆寫[CMFCRibbonBaseElement::DrawImage](../../mfc/reference/cmfcribbonbaseelement-class.md#drawimage)。)|  
|[CMFCRibbonButton::DrawRibbonText](#drawribbontext)||  
|[CMFCRibbonButton::FindSubItemIndexByID](#findsubitemindexbyid)|傳回與指定之命令識別碼相關聯的快顯功能表項目索引。|  
|[CMFCRibbonButton::GetCommandRect](#getcommandrect)||  
|[CMFCRibbonButton::GetCompactSize](#getcompactsize)|傳回功能區項目的壓縮大小。 (覆寫[CMFCRibbonBaseElement::GetCompactSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getcompactsize)。)|  
|[CMFCRibbonButton::GetIcon](#geticon)||  
|[CMFCRibbonButton::GetImageIndex](#getimageindex)|傳回與按鈕相關聯的映像索引。|  
|[CMFCRibbonButton::GetImageSize](#getimagesize)|傳回功能區項目的影像大小。 (覆寫[CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)。)|  
|[CMFCRibbonButton::GetIntermediateSize](#getintermediatesize)|傳回中繼狀態之功能區項目的大小。 (覆寫[CMFCRibbonBaseElement::GetIntermediateSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getintermediatesize)。)|  
|[CMFCRibbonButton::GetMenu](#getmenu)|傳回已指派給功能區按鈕之 Windows 功能表的控制代碼。|  
|[CMFCRibbonButton::GetMenuRect](#getmenurect)||  
|[CMFCRibbonButton::GetRegularSize](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonButton::GetSubItems](#getsubitems)||  
|[CMFCRibbonButton::GetTextRowHeight](#gettextrowheight)||  
|[CMFCRibbonButton::GetToolTipText](#gettooltiptext)|傳回功能區項目的工具提示文字。 (覆寫[CMFCRibbonBaseElement::GetToolTipText](../../mfc/reference/cmfcribbonbaseelement-class.md#gettooltiptext)。)|  
|[CMFCRibbonButton::HasCompactMode](#hascompactmode)|指定功能區項目是否有精簡模式。 (覆寫[CMFCRibbonBaseElement::HasCompactMode](../../mfc/reference/cmfcribbonbaseelement-class.md#hascompactmode)。)|  
|[CMFCRibbonButton::HasIntermediateMode](#hasintermediatemode)|指定功能區項目是否有中繼模式。 (覆寫[CMFCRibbonBaseElement::HasIntermediateMode](../../mfc/reference/cmfcribbonbaseelement-class.md#hasintermediatemode)。)|  
|[CMFCRibbonButton::HasLargeMode](#haslargemode)|指定功能區項目是否有大型模式。 (覆寫[CMFCRibbonBaseElement::HasLargeMode](../../mfc/reference/cmfcribbonbaseelement-class.md#haslargemode)。)|  
|[CMFCRibbonButton::HasMenu](#hasmenu)|(覆寫[CMFCRibbonBaseElement::HasMenu](../../mfc/reference/cmfcribbonbaseelement-class.md#hasmenu)。)|  
|[CMFCRibbonButton::IsAlwaysDrawBorder](#isalwaysdrawborder)||  
|[CMFCRibbonButton::IsAlwaysLargeImage](#isalwayslargeimage)|(覆寫[CMFCRibbonBaseElement::IsAlwaysLargeImage](../../mfc/reference/cmfcribbonbaseelement-class.md#isalwayslargeimage)。)|  
|[CMFCRibbonButton::IsApplicationButton](#isapplicationbutton)||  
|[CMFCRibbonButton::IsCommandAreaHighlighted](#iscommandareahighlighted)||  
|[CMFCRibbonButton::IsDefaultCommand](#isdefaultcommand)|判定您是否已啟用功能區按鈕的預設命令。|  
|[CMFCRibbonButton::IsDefaultPanelButton](#isdefaultpanelbutton)||  
|[CMFCRibbonButton::IsDrawTooltipImage](#isdrawtooltipimage)||  
|[CMFCRibbonButton::IsLargeImage](#islargeimage)||  
|[CMFCRibbonButton::IsMenuAreaHighlighted](#ismenuareahighlighted)||  
|[CMFCRibbonButton::IsMenuOnBottom](#ismenuonbottom)||  
|[CMFCRibbonButton::IsPopupDefaultMenuLook](#ispopupdefaultmenulook)||  
|[CMFCRibbonButton::IsRightAlignMenu](#isrightalignmenu)|判定功能表是否靠右對齊。|  
|[CMFCRibbonButton::IsSingleLineText](#issinglelinetext)||  
|[CMFCRibbonButton::OnCalcTextSize](#oncalctextsize)|(覆寫[CMFCRibbonBaseElement::OnCalcTextSize](../../mfc/reference/cmfcribbonbaseelement-class.md#oncalctextsize)。)|  
|[CMFCRibbonButton::OnDrawBorder](#ondrawborder)||  
|[CMFCRibbonButton::OnDraw](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonButton::OnFillBackground](#onfillbackground)||  
|[CMFCRibbonButton::RemoveAllSubItems](#removeallsubitems)|從快顯功能表中移除所有功能表項目。|  
|[CMFCRibbonButton::RemoveSubItem](#removesubitem)|從快顯功能表中移除功能表項目。|  
|[CMFCRibbonButton::SetACCData](#setaccdata)|(覆寫[CMFCRibbonBaseElement::SetACCData](../../mfc/reference/cmfcribbonbaseelement-class.md#setaccdata)。)|  
|[CMFCRibbonButton::SetAlwaysLargeImage](#setalwayslargeimage)|指定使用者摺疊按鈕時，按鈕是顯示大型影像還是小型影像。|  
|[CMFCRibbonButton::SetDefaultCommand](#setdefaultcommand)|啟用功能區按鈕的預設命令。|  
|[CMFCRibbonButton::SetDescription](#setdescription)|設定功能區項目的描述。 (覆寫[CMFCRibbonBaseElement::SetDescription](../../mfc/reference/cmfcribbonbaseelement-class.md#setdescription)。)|  
|[CMFCRibbonButton::SetImageIndex](#setimageindex)|將索引指派給按鈕的影像。|  
|[CMFCRibbonButton::SetMenu](#setmenu)|將快顯功能表上指派給功能區按鈕。|  
|[CMFCRibbonButton::SetParentCategory](#setparentcategory)|(覆寫[CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)。)|  
|[CMFCRibbonButton::SetRightAlignMenu](#setrightalignmenu)|將快顯功能表對齊按鈕右邊。|  
|[CMFCRibbonButton::SetText](#settext)|設定功能區項目的文字。 (覆寫[CMFCRibbonBaseElement::SetText](../../mfc/reference/cmfcribbonbaseelement-class.md#settext)。)|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonButton::OnClick](#onclick)|使用者按一下按鈕時由架構呼叫。|  
  
## <a name="example"></a>範例  
 下列範例示範如何在 `CMFCRibbonButton` 類別中使用各種方法。 此範例示範如何建構 `CMFCRibbonButton` 類別的物件、將快顯功能表指派給功能區按鈕、設定按鈕的描述、從快顯功能表中移除功能表項目，以及將快顯功能表靠右對齊按鈕的邊緣。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&7;](../../mfc/reference/codesnippet/cpp/cmfcribbonbutton-class_1.cpp)]  
  
## <a name="remarks"></a>備註  
 若要使用的功能區按鈕的應用程式中，建構按鈕物件並將它加入至適當的功能區[面板](../../mfc/reference/cmfcribbonpanel-class.md)。  
  
```  
CMFCRibbonPanel* pPanel = pCategory->AddPanel (
    _T("Clipboard"), // Panel name  
    m_PanelIcons.ExtractIcon (0)); // Panel icon  

// Create the first button ("Paste"):  
CMFCRibbonButton* pPasteButton = 
    new CMFCRibbonButton (ID_EDIT_PASTE, _T("Paste"), -1, 0);

// The third parameter (-1) disables small images for button.  
// This button is always displayed with a large image  
// Associate a pop-up menu with the "Paste" button:  
pPasteButton->SetMenu (IDR_CONTEXT_MENU);

// Add buttons to the panel. These buttons have only small images.  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_CUT, _T("Cut"), 1));
pPanel->Add (new CMFCRibbonButton (ID_EDIT_COPY, _T("Copy"), 2));
pPanel->Add (new CMFCRibbonButton (ID_EDIT_PAINT, _T("Paint"), 9));
```  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribbonbutton.h  
  
##  <a name="a-nameaddsubitema--cmfcribbonbuttonaddsubitem"></a><a name="addsubitem"></a>CMFCRibbonButton::AddSubItem  
 將功能表項目加入至與按鈕相關聯的快顯功能表。  
  
```  
void AddSubItem(
    CMFCRibbonBaseElement* pSubItem,  
    int nIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `pSubItem`  
 指定要加入的新元素的指標。  
  
 [in] `nIndex`  
 指定要加入的按鈕，功能表項目陣列項目索引加入功能表項目的陣列結尾處的項目-1。  
  
##  <a name="a-namecanbestretcheda--cmfcribbonbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCRibbonButton::CanBeStretched  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecleanupsizesa--cmfcribbonbuttoncleanupsizes"></a><a name="cleanupsizes"></a>CMFCRibbonButton::CleanUpSizes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CleanUpSizes();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameclosepopupmenua--cmfcribbonbuttonclosepopupmenu"></a><a name="closepopupmenu"></a>CMFCRibbonButton::ClosePopupMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ClosePopupMenu();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecmfcribbonbuttona--cmfcribbonbuttoncmfcribbonbutton"></a><a name="cmfcribbonbutton"></a>CMFCRibbonButton::CMFCRibbonButton  
 建構功能區按鈕物件。  
  
```  
CMFCRibbonButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1,  
    BOOL bAlwaysShowDescription=FALSE);

CMFCRibbonButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon,  
    BOOL bAlwaysShowDescription=FALSE,  
    HICON hIconSmall=NULL,  
    BOOL bAutoDestroyIcon=FALSE,  
    BOOL bAlphaBlendIcon=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 指定按鈕的命令 ID。  
  
 [in] `lpszText`  
 指定按鈕的文字標籤。  
  
 [in] `nSmallImageIndex`  
 影像清單的父類別中指定按鈕的小型影像的以零為起始索引。  
  
 [in] `nLargeImageIndex`  
 影像清單的父類別中指定按鈕的大型影像的以零為起始索引。  
  
 [in] `hIcon`  
 指定應用程式做為按鈕的影像之圖示的控制代碼。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構`CMFCRibbonButton`物件。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&6;](../../mfc/reference/codesnippet/cpp/cmfcribbonbutton-class_2.cpp)]  
  
##  <a name="a-namedrawbottomtexta--cmfcribbonbuttondrawbottomtext"></a><a name="drawbottomtext"></a>CMFCRibbonButton::DrawBottomText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CSize DrawBottomText(
    CDC* pDC,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `bCalcOnly`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedrawimagea--cmfcribbonbuttondrawimage"></a><a name="drawimage"></a>CMFCRibbonButton::DrawImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void DrawImage(
    CDC* pDC,  
    RibbonImageType type,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `type`  
 [in] `rectImage`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedrawribbontexta--cmfcribbonbuttondrawribbontext"></a><a name="drawribbontext"></a>CMFCRibbonButton::DrawRibbonText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int DrawRibbonText(
    CDC* pDC,  
    const CString& strText,  
    CRect rectText,  
    UINT uiDTFlags,  
    COLORREF clrText = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `strText`  
 [in] `rectText`  
 [in] `uiDTFlags`  
 [in] `clrText`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namefindsubitemindexbyida--cmfcribbonbuttonfindsubitemindexbyid"></a><a name="findsubitemindexbyid"></a>CMFCRibbonButton::FindSubItemIndexByID  
 傳回與指定之命令識別碼相關聯的快顯功能表項目索引。  
  
```  
int FindSubItemIndexByID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 指定命令識別碼的快顯功能表項目。  
  
### <a name="return-value"></a>傳回值  
 以零起始的索引子相關聯的項目的`uiID`。 如果沒有這類項目-1。  
  
##  <a name="a-namegetcommandrecta--cmfcribbonbuttongetcommandrect"></a><a name="getcommandrect"></a>CMFCRibbonButton::GetCommandRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetCommandRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcompactsizea--cmfcribbonbuttongetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonButton::GetCompactSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegeticona--cmfcribbonbuttongeticon"></a><a name="geticon"></a>CMFCRibbonButton::GetIcon  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HICON GetIcon(BOOL bLargeIcon = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bLargeIcon`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetimageindexa--cmfcribbonbuttongetimageindex"></a><a name="getimageindex"></a>CMFCRibbonButton::GetImageIndex  
 傳回與按鈕相關聯的映像索引。  
  
```  
int GetImageIndex(BOOL bLargeImage) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bLargeImage`  
 如果`TRUE`，傳回包含大型影像，否則會傳回包含小型影像的影像清單內的映像索引的影像清單中的影像索引。  
  
### <a name="return-value"></a>傳回值  
 按鈕的影像相關聯的影像清單中的索引。  
  
##  <a name="a-namegetimagesizea--cmfcribbonbuttongetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButton::GetImageSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetImageSize(RibbonImageType type) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `type`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetintermediatesizea--cmfcribbonbuttongetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonButton::GetIntermediateSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetmenua--cmfcribbonbuttongetmenu"></a><a name="getmenu"></a>CMFCRibbonButton::GetMenu  
 傳回已指派給功能區按鈕之 Windows 功能表的控制代碼。  
  
```  
HMENU GetMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Windows 功能表指派給按鈕，控制代碼`NULL`沒有指派功能表。  
  
##  <a name="a-namegetmenurecta--cmfcribbonbuttongetmenurect"></a><a name="getmenurect"></a>CMFCRibbonButton::GetMenuRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetMenuRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetregularsizea--cmfcribbonbuttongetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButton::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetsubitemsa--cmfcribbonbuttongetsubitems"></a><a name="getsubitems"></a>CMFCRibbonButton::GetSubItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& GetSubItems() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettextrowheighta--cmfcribbonbuttongettextrowheight"></a><a name="gettextrowheight"></a>CMFCRibbonButton::GetTextRowHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTextRowHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettooltiptexta--cmfcribbonbuttongettooltiptext"></a><a name="gettooltiptext"></a>CMFCRibbonButton::GetToolTipText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehascompactmodea--cmfcribbonbuttonhascompactmode"></a><a name="hascompactmode"></a>CMFCRibbonButton::HasCompactMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehasintermediatemodea--cmfcribbonbuttonhasintermediatemode"></a><a name="hasintermediatemode"></a>CMFCRibbonButton::HasIntermediateMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasIntermediateMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehaslargemodea--cmfcribbonbuttonhaslargemode"></a><a name="haslargemode"></a>CMFCRibbonButton::HasLargeMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehasmenua--cmfcribbonbuttonhasmenu"></a><a name="hasmenu"></a>CMFCRibbonButton::HasMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisalwaysdrawbordera--cmfcribbonbuttonisalwaysdrawborder"></a><a name="isalwaysdrawborder"></a>CMFCRibbonButton::IsAlwaysDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAlwaysDrawBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisalwayslargeimagea--cmfcribbonbuttonisalwayslargeimage"></a><a name="isalwayslargeimage"></a>CMFCRibbonButton::IsAlwaysLargeImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAlwaysLargeImage() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisapplicationbuttona--cmfcribbonbuttonisapplicationbutton"></a><a name="isapplicationbutton"></a>CMFCRibbonButton::IsApplicationButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsApplicationButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameiscommandareahighlighteda--cmfcribbonbuttoniscommandareahighlighted"></a><a name="iscommandareahighlighted"></a>CMFCRibbonButton::IsCommandAreaHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsCommandAreaHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdefaultcommanda--cmfcribbonbuttonisdefaultcommand"></a><a name="isdefaultcommand"></a>CMFCRibbonButton::IsDefaultCommand  
 指定是否要啟用的功能區按鈕的預設命令。  
  
```  
BOOL IsDefaultCommand() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果您已啟用的功能區按鈕; 的預設命令`FALSE`否則。  
  
##  <a name="a-nameisdefaultpanelbuttona--cmfcribbonbuttonisdefaultpanelbutton"></a><a name="isdefaultpanelbutton"></a>CMFCRibbonButton::IsDefaultPanelButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDefaultPanelButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdrawtooltipimagea--cmfcribbonbuttonisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonButton::IsDrawTooltipImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameislargeimagea--cmfcribbonbuttonislargeimage"></a><a name="islargeimage"></a>CMFCRibbonButton::IsLargeImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsLargeImage() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameismenuareahighlighteda--cmfcribbonbuttonismenuareahighlighted"></a><a name="ismenuareahighlighted"></a>CMFCRibbonButton::IsMenuAreaHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsMenuAreaHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameismenuonbottoma--cmfcribbonbuttonismenuonbottom"></a><a name="ismenuonbottom"></a>CMFCRibbonButton::IsMenuOnBottom  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuOnBottom() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameispopupdefaultmenulooka--cmfcribbonbuttonispopupdefaultmenulook"></a><a name="ispopupdefaultmenulook"></a>CMFCRibbonButton::IsPopupDefaultMenuLook  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsPopupDefaultMenuLook() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisrightalignmenua--cmfcribbonbuttonisrightalignmenu"></a><a name="isrightalignmenu"></a>CMFCRibbonButton::IsRightAlignMenu  
 指定功能表是否為靠右對齊。  
  
```  
BOOL IsRightAlignMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果是靠右對齊。否則`FALSE`。  
  
##  <a name="a-nameissinglelinetexta--cmfcribbonbuttonissinglelinetext"></a><a name="issinglelinetext"></a>CMFCRibbonButton::IsSingleLineText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsSingleLineText() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoncalctextsizea--cmfcribbonbuttononcalctextsize"></a><a name="oncalctextsize"></a>CMFCRibbonButton::OnCalcTextSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnCalcTextSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonclicka--cmfcribbonbuttononclick"></a><a name="onclick"></a>CMFCRibbonButton::OnClick  
 使用者按一下按鈕時由架構呼叫。  
  
```  
virtual void OnClick(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指定滑鼠點選位置。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，如果您想要處理這個事件。  
  
##  <a name="a-nameondrawa--cmfcribbonbuttonondraw"></a><a name="ondraw"></a>CMFCRibbonButton::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawbordera--cmfcribbonbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCRibbonButton::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonfillbackgrounda--cmfcribbonbuttononfillbackground"></a><a name="onfillbackground"></a>CMFCRibbonButton::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameremoveallsubitemsa--cmfcribbonbuttonremoveallsubitems"></a><a name="removeallsubitems"></a>CMFCRibbonButton::RemoveAllSubItems  
 從快顯功能表中移除所有功能表項目。  
  
```  
void RemoveAllSubItems();
```  
  
##  <a name="a-nameremovesubitema--cmfcribbonbuttonremovesubitem"></a><a name="removesubitem"></a>CMFCRibbonButton::RemoveSubItem  
 從快顯功能表中移除功能表項目。  
  
```  
BOOL RemoveSubItem(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定您想要移除功能表項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，已移除指定的項目否則`FALSE`如果`nIndex`為負數，或超過快顯功能表中功能表項目數目。  
  
##  <a name="a-namesetaccdataa--cmfcribbonbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonButton::SetACCData  
 設定功能區按鈕的協助工具資料。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);  
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 功能區項目的父視窗。  
  
 `data`  
 功能區項目的協助工具資料。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 `TRUE` ，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetalwayslargeimagea--cmfcribbonbuttonsetalwayslargeimage"></a><a name="setalwayslargeimage"></a>CMFCRibbonButton::SetAlwaysLargeImage  
 指定使用者摺疊按鈕時，按鈕是顯示大型影像還是小型影像。  
  
```  
void SetAlwaysLargeImage(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 如果`TRUE`，按鈕會顯示大影像。 否則，按鈕會顯示小影像。  
  
##  <a name="a-namesetdefaultcommanda--cmfcribbonbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFCRibbonButton::SetDefaultCommand  
 啟用功能區按鈕的預設命令。  
  
```  
void SetDefaultCommand(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 如果`TRUE`，按鈕可以執行其預設的命令。 如果`FALSE`，按鈕無法執行其預設的命令。  
  
### <a name="remarks"></a>備註  
 `bSet`是只有當按鈕的功能表。 如果`bSet`是`TRUE`，按鈕可以執行其預設的命令，而且指定的快顯功能表會出現只有當使用者按一下按鈕右邊的箭號。 否則，按鈕無法執行其預設的命令，而且不論 [區域] 按鈕的使用者按一下快顯功能表會出現。  
  
##  <a name="a-namesetdescriptiona--cmfcribbonbuttonsetdescription"></a><a name="setdescription"></a>CMFCRibbonButton::SetDescription  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetDescription(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszText`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetimageindexa--cmfcribbonbuttonsetimageindex"></a><a name="setimageindex"></a>CMFCRibbonButton::SetImageIndex  
 將索引指派給按鈕的影像。  
  
```  
void SetImageIndex(
    int nIndex,  
    BOOL bLargeImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定映像索引。  
  
 [in] `bLargeImage`  
 如果`TRUE`，指定的索引是指大型映像的清單。 否則，索引參考的小型影像清單。  
  
##  <a name="a-namesetmenua--cmfcribbonbuttonsetmenu"></a><a name="setmenu"></a>CMFCRibbonButton::SetMenu  
 將快顯功能表上指派給功能區按鈕。  
  
```  
void SetMenu(
    HMENU hMenu,  
    BOOL bIsDefaultCommand=FALSE,  
    BOOL bRightAlign=FALSE);

void SetMenu(
    UINT uiMenuResID,  
    BOOL bIsDefaultCommand=FALSE,  
    BOOL bRightAlign=FALSE);
```  
  
### <a name="parameters"></a>參數  
 `hMenu`  
 Windows 功能表控制代碼。  
  
 `bIsDefaultCommand`  
 如果`TRUE`，按鈕可以執行其預設的命令; 否則按鈕會顯示快顯功能表。  
  
 `bRightAlign`  
 如果`TRUE`，是靠右對齊。 否則，功能表是靠左對齊。  
  
 `uiMenuResID`  
 功能表上的資源 id。  
  
### <a name="remarks"></a>備註  
 當應用程式會將功能表指定給按鈕時，按鈕會顯示在右側箭號。 如果`bIsDefaultCommand`是`TRUE`，只有當使用者按一下箭號時，才會出現的功能表。 如果使用者按一下按鈕時，它預設會執行命令。 如果`bIsDefaultCommand`是`FALSE`，功能表會出現在按鈕上的任意處按一下。  
  
##  <a name="a-namesetparentcategorya--cmfcribbonbuttonsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButton::SetParentCategory  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParent`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetrightalignmenua--cmfcribbonbuttonsetrightalignmenu"></a><a name="setrightalignmenu"></a>CMFCRibbonButton::SetRightAlignMenu  
 對齊按鈕的邊緣的快顯功能表。  
  
```  
void SetRightAlignMenu(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 如果`TRUE`，是靠右對齊。 否則，功能表會靠左對齊  
  
##  <a name="a-namesettexta--cmfcribbonbuttonsettext"></a><a name="settext"></a>CMFCRibbonButton::SetText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszText`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

