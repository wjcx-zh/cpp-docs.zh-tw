---
title: "CMFCRibbonGallery 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::AddGroup
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::AddSubItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::Clear
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::EnableMenuResize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::EnableMenuSideBar
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetCompactSize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetDroppedDown
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetGroupName
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetGroupOffset
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetIconsInRow
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetItemToolTip
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetLastSelectedItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetPaletteID
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetRegularSize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetSelectedItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::HasMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsButtonMode
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuResizeEnabled
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuResizeVertical
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuSideBar
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnAfterChangeRect
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnDraw
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnEnable
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnRTLChanged
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::RedrawIcons
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::RemoveItemToolTips
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SelectItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetACCData
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetButtonMode
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetGroupName
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetIconsInRow
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetItemToolTip
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetPaletteID
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnDrawPaletteIcon
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGallery class
ms.assetid: 9734c9c9-981c-4b3f-8c59-264fd41811b4
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c4eadb9820f2d7318131cc4d197dbe28d65491c0
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbongallery-class"></a>CMFCRibbonGallery 類別
實作 Office 2007 樣式的功能區組件庫。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonGallery : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonGallery::CMFCRibbonGallery](#cmfcribbongallery)|建構並初始化 `CMFCRibbonGallery` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonGallery::AddGroup](#addgroup)|將新的群組加入至組件庫。|  
|[CMFCRibbonGallery::AddSubItem](#addsubitem)|將新的功能表項目加入至下拉式選單。|  
|[CMFCRibbonGallery::Clear](#clear)|清除組件庫的內容。|  
|[CMFCRibbonGallery::EnableMenuResize](#enablemenuresize)|啟用或停用功能表面板的調整大小。|  
|[CMFCRibbonGallery::EnableMenuSideBar](#enablemenusidebar)|啟用或停用提要欄位的左邊的快顯功能表。|  
|[CMFCRibbonGallery::GetCompactSize](#getcompactsize)|(覆寫[CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonGallery::GetDroppedDown](#getdroppeddown)|(覆寫[CMFCRibbonBaseElement::GetDroppedDown](../../mfc/reference/cmfcribbonbaseelement-class.md#getdroppeddown)。)|  
|[CMFCRibbonGallery::GetGroupName](#getgroupname)|傳回位於指定索引上的群組名稱。|  
|[CMFCRibbonGallery::GetGroupOffset](#getgroupoffset)||  
|[CMFCRibbonGallery::GetIconsInRow](#geticonsinrow)|功能區組件庫的資料列中傳回的項目數。|  
|[CMFCRibbonGallery::GetItemToolTip](#getitemtooltip)|傳回組件庫中的項目相關聯的工具提示文字。|  
|[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)|傳回使用者選取的資源庫中的最後一個項目的索引。|  
|[CMFCRibbonGallery::GetPaletteID](#getpaletteid)|傳回目前的組件庫的命令 ID。|  
|[CMFCRibbonGallery::GetRegularSize](#getregularsize)|(覆寫[CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonGallery::GetSelectedItem](#getselecteditem)||  
|[CMFCRibbonGallery::HasMenu](#hasmenu)|(覆寫[CMFCRibbonButton::HasMenu](../../mfc/reference/cmfcribbonbutton-class.md#hasmenu)。)|  
|[CMFCRibbonGallery::IsButtonMode](#isbuttonmode)|指定是否要將組件庫包含在組件庫 按鈕。|  
|[CMFCRibbonGallery::IsMenuResizeEnabled](#ismenuresizeenabled)|指定是否啟用或停用功能表調整大小。|  
|[CMFCRibbonGallery::IsMenuResizeVertical](#ismenuresizevertical)||  
|[CMFCRibbonGallery::IsMenuSideBar](#ismenusidebar)|指定是否啟用或停用提要欄位。|  
|[CMFCRibbonGallery::OnAfterChangeRect](#onafterchangerect)|(覆寫 `CMFCRibbonButton::OnAfterChangeRect`。)|  
|[CMFCRibbonGallery::OnDraw](#ondraw)|(覆寫[CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonGallery::OnEnable](#onenable)|(覆寫 `CMFCRibbonBaseElement::OnEnable`。)|  
|[CMFCRibbonGallery::OnRTLChanged](#onrtlchanged)|(覆寫[CMFCRibbonBaseElement::OnRTLChanged](../../mfc/reference/cmfcribbonbaseelement-class.md#onrtlchanged)。)|  
|[CMFCRibbonGallery::RedrawIcons](#redrawicons)|組件庫來重新繪製。|  
|[CMFCRibbonGallery::RemoveItemToolTips](#removeitemtooltips)|移除組件庫中所有項目的工具提示。|  
|[CMFCRibbonGallery::SelectItem](#selectitem)||  
|[CMFCRibbonGallery::SetACCData](#setaccdata)|(覆寫[CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
|[CMFCRibbonGallery::SetButtonMode](#setbuttonmode)|指定是否要顯示的功能區組件庫，為下拉式按鈕或直接在功能區上的調色盤。|  
|[CMFCRibbonGallery::SetGroupName](#setgroupname)|設定群組的名稱。|  
|[CMFCRibbonGallery::SetIconsInRow](#seticonsinrow)|組件庫中定義的每個資料列的項目數。|  
|[CMFCRibbonGallery::SetItemToolTip](#setitemtooltip)|組件庫中設定項目的工具提示文字。|  
|[CMFCRibbonGallery::SetPalette](#setpalette)|附加至功能區圖庫的調色盤。|  
|[CMFCRibbonGallery::SetPaletteID](#setpaletteid)|定義傳送中的命令識別碼`WM_COMMAND`訊息已選取主機庫項目時。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonGallery::OnDrawPaletteIcon](#ondrawpaletteicon)|組件庫圖示繪製時，由架構呼叫。|  
  
## <a name="remarks"></a>備註  
 組件庫 按鈕的行為就像一般功能表按鈕但它會顯示組件庫，當使用者開啟它。 當您在圖庫中選取項目時，架構就會傳送`WM_COMMAND`以及按鈕的命令 ID 的訊息。 當您處理訊息時，您應該呼叫[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)來判斷組件庫中所選取的項目。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonGallery`類別來設定`CMFCRibbonGallery`物件。 此範例說明如何指定組件庫中的每個資料列的項目數、 啟用功能表面板的調整大小、 啟用提要欄位的左邊的快顯功能表中，並顯示功能區組件庫做為直接在功能區列上的色板。 此程式碼片段是一部分[繪製的用戶端範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&6;](../../mfc/reference/codesnippet/cpp/cmfcribbongallery-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonPaletteGallery.h  
  
##  <a name="addgroup"></a>CMFCRibbonGallery::AddGroup  
 將新的群組加入至組件庫。  
  
```  
void AddGroup(
    LPCTSTR lpszGroupName,  
    UINT uiImagesPaletteResID,  
    int cxPaletteImage);

 
void AddGroup(
    LPCTSTR lpszGroupName,  
    CMFCToolBarImages& imagesGroup);

 
void AddGroup(
    LPCTSTR lpszGroupName,  
    int nIconsNum);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszGroupName`  
 指定群組的名稱。  
  
 [in] `uiImagesPaletteResID`  
 指定映像清單，其中包含的映像群組的資源識別碼。  
  
 [in] `cxPaletteImage`  
 指定的寬度，單位為像素的影像。  
  
 [in] `imagesGroup`  
 包含群組的映像的映像清單參考。  
  
 [in] `nIconsNum`  
 指定群組中的圖示數目。 應該指定這個參數，只會針對自訂 （擁有者繪製） 群組。  
  
### <a name="remarks"></a>備註  
 您可以分割成多個群組的功能區組件庫上的項目，藉由呼叫這個方法。 每個群組可以有標題。  
  
##  <a name="addsubitem"></a>CMFCRibbonGallery::AddSubItem  
 將新的功能表項目加入至下拉式選單。  
  
```  
void AddSubItem(
    CMFCRibbonBaseElement* pSubItem,  
    int nIndex=-1,  
    BOOL bOnTop=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pSubItem`  
 要加入至功能表項目的指標。  
  
 [in] `nIndex`  
 指定位置之以零為起始索引位置插入項目。  
  
 [in] `bOnTop`  
 `TRUE`若要指定項目，應該插入之前的功能區組件庫。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以呼叫這個方法，以快顯功能表項目結合快顯視窗中的組件庫。 之前或之後的組件庫，則可以放置功能表項目。  
  
 若要插入組件庫之前，項目，設定`bOnTop`到`TRUE`。 設定`bOnTop`至`FALSE`插入組件庫底下的項目。  
  
> [!NOTE]
>  參數`nIndex`指定插入索引在組件庫的頂端和底部的組件庫。 例如，如果您需要將組件庫之前的項目一個位置，設定`nIndex`為 1 和`bOnTop`到`TRUE`。 同樣地，如果您需要將下列組件庫的項目一個位置，設定`nIndex`為 1 和`bOnTop`到`FALSE`。  
  
##  <a name="clear"></a>CMFCRibbonGallery::Clear  
 清除組件庫的內容。  
  
```  
virtual void Clear();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來移除的功能區組件庫中的所有內容。 這必須在您附加的功能區組件庫的新功能區組件庫或一組群組之前完成。  
  
##  <a name="cmfcribbongallery"></a>CMFCRibbonGallery::CMFCRibbonGallery  
 建構並初始化[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)物件。  
  
```  
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    CMFCToolBarImages& imagesPalette);

 
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    UINT uiImagesPaletteResID=0,  
    int cxPaletteImage=0);

 
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    CSize sizeIcon,  
    int nIconsNum,  
    BOOL bDefaultButtonStyle=TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 指定當使用者按一下按鈕時執行命令的命令 ID。  
  
 `lpszText`  
 指定要顯示於按鈕的文字。  
  
 `nSmallImageIndex`  
 要顯示在按鈕上的小型影像以零為起始的索引。  
  
 `nLargeImageIndex`  
 大型影像出現在按鈕上的以零為起始的索引。  
  
 `imagesPalette`  
 參考[CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md)物件，其中包含出現在組件庫映像。  
  
 `uiImagesPaletteResID`  
 在組件庫上顯示的影像清單的資源識別碼。  
  
 `cxPaletteImage`  
 指定寬度，單位為像素上組件庫的映像。  
  
 `sizeIcon`  
 指定大小，單位為像素資源庫映像。  
  
 `nIconsNum`  
 組件庫中指定圖示的數目。  
  
 `bDefaultButtonStyle`  
 指定是否要使用預設值或為主控描繪按鈕樣式。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enablemenuresize"></a>CMFCRibbonGallery::EnableMenuResize  
 啟用或停用功能表面板的調整大小。  
  
```  
void EnableMenuResize(
    BOOL bEnable = TRUE,  
    BOOL bVertcalOnly = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用功能表; 調整大小否則， `FALSE`。  
  
 [in] `bVertcalOnly`  
 `TRUE`若要指定的組件庫可調整大小只能垂直;`FALSE`來指定組件庫可調整大小，兩者垂直和水平。  
  
### <a name="remarks"></a>備註  
 若要啟用或停用調整大小功能區組件庫中使用這個方法。 啟用時調整大小，功能區組件庫顯示移駐夾，使用者可用來調整其大小。  
  
##  <a name="enablemenusidebar"></a>CMFCRibbonGallery::EnableMenuSideBar  
 啟用或停用提要欄位的左邊的快顯功能表。  
  
```  
void EnablMenuSideBar(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要指定的提要欄位已啟用。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來啟用或停用 Office XP 樣式提要欄位，在左側的功能表。  
  
##  <a name="getcompactsize"></a>CMFCRibbonGallery::GetCompactSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getdroppeddown"></a>CMFCRibbonGallery::GetDroppedDown  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getgroupname"></a>CMFCRibbonGallery::GetGroupName  
 傳回位於指定索引上的群組名稱。  
  
```  
LPCTSTR GetGroupName(int nGroupIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nGroupIndex`  
 指定您想要擷取其名稱的群組以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 位於指定索引處的群組名稱。 傳遞無效的索引將會導致失敗的判斷提示。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getgroupoffset"></a>CMFCRibbonGallery::GetGroupOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetGroupOffset() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="geticonsinrow"></a>CMFCRibbonGallery::GetIconsInRow  
 功能區組件庫的資料列中傳回的項目數。  
  
```  
int GetIconsInRow() const;  
```  
  
### <a name="return-value"></a>傳回值  
 資料列中的項目數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getitemtooltip"></a>CMFCRibbonGallery::GetItemToolTip  
 傳回組件庫中的項目相關聯的工具提示文字。  
  
```  
LPCTSTR GetItemToolTip(int nItemIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nItemIndex`  
 指定要擷取的工具提示文字的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指派給功能區組件庫中的項目工具提示字串的指標。 它可以是`NULL`如果沒有工具提示會指派給這個項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getlastselecteditem"></a>CMFCRibbonGallery::GetLastSelectedItem  
 傳回使用者選取的功能區資源庫中的最後一個項目的索引。  
  
```  
static int GetLastSelectedItem(UINT uiCmdID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 指定開啟功能區組件庫之功能表項目的命令 ID。  
  
### <a name="return-value"></a>傳回值  
 當使用者在功能區組件庫中選取任何項目時，程式庫會傳送`WM_COMMAND`的訊息和命令 ID 的開啟功能區組件庫功能表按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getpaletteid"></a>CMFCRibbonGallery::GetPaletteID  
 傳回目前的調色盤的命令 ID。  
  
```  
int GetPaletteID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的調色盤的命令 ID。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getregularsize"></a>CMFCRibbonGallery::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getselecteditem"></a>CMFCRibbonGallery::GetSelectedItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="hasmenu"></a>CMFCRibbonGallery::HasMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isbuttonmode"></a>CMFCRibbonGallery::IsButtonMode  
 指定調色盤是否包含在組件庫 按鈕。  
  
```  
BOOL IsButtonMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果調色盤會顯示為下拉式選單 按鈕。`FALSE`如果直接在功能區上顯示調色盤。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ismenuresizeenabled"></a>CMFCRibbonGallery::IsMenuResizeEnabled  
 指定是否啟用功能表調整大小。  
  
```  
BOOL IsMenuResizeEnabled() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用功能表調整大小;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ismenuresizevertical"></a>CMFCRibbonGallery::IsMenuResizeVertical  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuResizeVertical() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ismenusidebar"></a>CMFCRibbonGallery::IsMenuSideBar  
 指定是否啟用或停用提要欄位。  
  
```  
BOOL IsMenuSideBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 Office XP 樣式提要欄位會在快顯功能表中，左側繪製否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onafterchangerect"></a>CMFCRibbonGallery::OnAfterChangeRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondraw"></a>CMFCRibbonGallery::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawpaletteicon"></a>CMFCRibbonGallery::OnDrawPaletteIcon  
 組件庫圖示繪製時，由架構呼叫。  
  
```  
virtual void OnDrawPaletteIcon(
    CDC* pDC,  
    CRect rectIcon,  
    int nIconIndex,  
    CMFCRibbonGalleryIcon* pIcon,  
    COLORREF clrText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 用於繪製的裝置內容指標。  
  
 [in] `rectIcon`  
 指定要繪製圖示的周框矩形。  
  
 [in] `nIconIndex`  
 若要繪製圖示的組件庫圖示的影像清單中指定的以零為起始的索引。  
  
 [in] `pIcon`  
 所繪製之圖示的指標。  
  
 [in] `clrText`  
 指定要繪製的項目文字的色彩。  
  
### <a name="remarks"></a>備註  
 您可以覆寫這個方法在衍生類別訂功能區組件庫中。  
  
##  <a name="onenable"></a>CMFCRibbonGallery::OnEnable  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrtlchanged"></a>CMFCRibbonGallery::OnRTLChanged  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsRTL`  
  
### <a name="remarks"></a>備註  
  
##  <a name="redrawicons"></a>CMFCRibbonGallery::RedrawIcons  
 組件庫來重新繪製。  
  
```  
void RedrawIcons();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式來重繪其組件庫。 如果您已在執行階段組件庫的內容，您必須呼叫這個方法。  
  
##  <a name="removeitemtooltips"></a>CMFCRibbonGallery::RemoveItemToolTips  
 移除組件庫中所有項目的工具提示。  
  
```  
void RemoveItemToolTips();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="selectitem"></a>CMFCRibbonGallery::SelectItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SelectItem(int nItemIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nItemIndex`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setaccdata"></a>CMFCRibbonGallery::SetACCData  
 使用功能區圖庫中的協助工具資料填入指定的 `CAccessibilityData` 物件。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,   
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParent`  
 功能區圖庫視窗的父視窗。  
  
 [輸出] `data`  
 從功能區圖庫接收協助工具資料的 `CAccessibilityData` 物件。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 如果方法成功，則為 `TRUE`，否則為 `FALSE`。  
  
##  <a name="setbuttonmode"></a>CMFCRibbonGallery::SetButtonMode  
 決定是否要顯示的功能區組件庫，為下拉式按鈕或直接在功能區上的調色盤。  
  
```  
void SetButtonMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 `TRUE`若要以下拉式選單 按鈕，顯示功能區組件庫`FALSE`在功能區上直接顯示功能區組件庫的內容。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setgroupname"></a>CMFCRibbonGallery::SetGroupName  
 設定群組的名稱。  
  
```  
void SetGroupName(
    int nGroupIndex,  
    LPCTSTR lpszGroupName);
```  
  
### <a name="parameters"></a>參數  
 [in] `nGroupIndex`  
 指定的群組名稱要變更的以零為起始的索引。  
  
 [in] `lpszGroupName`  
 指定群組的新名稱。  
  
### <a name="remarks"></a>備註  
 正在變更其名稱的群組必須已加入使用[CMFCRibbonGallery::AddGroup](#addgroup)方法。  
  
##  <a name="seticonsinrow"></a>CMFCRibbonGallery::SetIconsInRow  
 指定組件庫中的每個資料列的項目數。  
  
```  
void SetIconsInRow(int nIconsInRow);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIconsInRow`  
 指定項目出現在組件庫的每個資料列數目。  
  
### <a name="remarks"></a>備註  
 使用這個方法指定的功能區組件庫的寬度。  
  
##  <a name="setitemtooltip"></a>CMFCRibbonGallery::SetItemToolTip  
 組件庫中設定項目的工具提示文字。  
  
```  
void SetItemToolTip(
    int nItemIndex,  
    LPCTSTR lpszToolTip);
```  
  
### <a name="parameters"></a>參數  
 [in] `nItemIndex`  
 要與工具提示相關聯的調色盤項目以零為起始的索引。  
  
 [in] `lpszToolTip`  
 若要顯示在工具提示文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpalette"></a>CMFCRibbonGallery::SetPalette  
 附加至功能區圖庫的調色盤。  
  
```  
void SetPalette(CMFCToolBarImages& imagesPalette);

 
void SetPalette(
    UINT uiImagesPaletteResID,  
    int cxPaletteImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `imagesPalette`  
 指定包含要顯示在組件庫上的圖示的影像清單。  
  
 [in] `uiImagesPaletteResID`  
 指定映像清單，其中包含出現在組件庫圖示的資源識別碼。  
  
 [in] `cxPaletteImage`  
 指定寬度，單位為像素上組件庫的映像。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpaletteid"></a>CMFCRibbonGallery::SetPaletteID  
 定義傳送中的命令識別碼**WM_COMMAND**訊息，當使用者選取主機庫項目。  
  
```  
void SetPaletteID(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 指定傳送中的命令 ID **WM_COMMAND**訊息，當使用者選取主機庫項目。  
  
### <a name="remarks"></a>備註  
 若要判斷從組件庫中選取使用者的特定項目，請呼叫[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)靜態方法。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonGalleryMenuButton 類別](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

