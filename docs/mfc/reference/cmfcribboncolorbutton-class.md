---
title: "CMFCRibbonColorButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonColorButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonColorButton class
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
caps.latest.revision: 36
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
ms.openlocfilehash: 8cef76fd3518e1123cb9afd0c8cc2a39b2bff65c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton 類別
`CMFCRibbonColorButton` 類別實作可以加入功能區列中的色彩按鈕。 功能區色彩按鈕會顯示包含一個或多個色板的下拉式功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|將色彩群組加入標準色彩區域中。|  
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|指定是否啟用 [自動]  按鈕。|  
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|啟用 [其他]  按鈕。|  
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||  
|[CMFCRibbonColorButton::GetColor](#getcolor)|傳回目前選取的色彩。|  
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|傳回色軸顯示的色彩項目大小。|  
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||  
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|傳回目前所選項目在快顯調色盤上的色彩。|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|從標準色彩區域移除所有色彩群組。|  
|[CMFCRibbonColorButton::SetColor](#setcolor)|從標準色彩區域選取色彩。|  
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|設定色軸顯示之所有色彩項目的大小。|  
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||  
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||  
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|指定文件色彩區域顯示的 RGB 值清單。|  
|[CMFCRibbonColorButton::SetPalette](#setpalette)||  
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||  
  
## <a name="remarks"></a>備註  
 當使用者按下它時，功能區色彩按鈕就會顯示色軸。 這個色軸預設包含色彩選取範圍的調色盤，稱為標準色彩區域。 色軸也可以選擇顯示 [自動]  按鈕，讓使用者選取預設的色彩，而 [其他]  按鈕則顯示包含其他色彩的快顯調色盤。  
  
## <a name="example"></a>範例  
 下例示範如何在 `CMFCRibbonColorButton` 類別中使用各種方法。 此範例示範如何建構 `CMFCRibbonColorButton` 物件、設定大型影像、啟用 [自動]  按鈕、啟用 [其他]  按鈕、設定資料行數目、設定色軸顯示的所有色彩項目大小、將色彩群組加入標準色彩區域中，以及指定文件色彩區域顯示的 RGB 值清單。 此程式碼片段是一部分[繪製的用戶端範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&3;](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標題:** afxribboncolorbutton.h  
  
##  <a name="a-nameaddcolorsgroupa--cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup  
 將色彩群組加入標準色彩區域中。  
  
```  
void AddColorsGroup(
    LPCTSTR lpszName,  
    const CList<COLORREF,COLORREF>& lstColors,  
    BOOL bContiguousColumns=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszName`  
 群組名稱。  
  
 [in] `lstColors`  
 色彩的清單。  
  
 [in] `bContiguousColumns`  
 控制色彩項目群組中的顯示方式。 如果`TRUE`，色彩項目會繪製沒有垂直間距。 如果`FALSE`，色彩項目會繪製具有垂直間距。  
  
### <a name="remarks"></a>備註  
 使用這個函式，使色彩快顯會顯示數個群組的色彩。 您可以控制色彩群組中的顯示方式。  
  
##  <a name="a-namecmfcribboncolorbuttona--cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton  
 建構 `CMFCRibbonColorButton` 物件。  
  
```  
CMFCRibbonColorButton();

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    COLORREF color = RGB(0, 0, 0));

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    BOOL bSimpleButtonLook,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    COLORREF color = RGB(0, 0, 0));
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 指定當使用者按一下按鈕時執行命令的命令 ID。  
  
 [in] `lpszText`  
 指定要顯示於按鈕的文字。  
  
 [in] `nSmallImageIndex`  
 要顯示在按鈕上的小型影像以零為起始的索引。  
  
 [in] `color`  
 （預設為黑色） 按鈕的色彩。  
  
 [in] `bSimpleButtonLook`  
 如果`TRUE`，按鈕會繪製成的簡單矩形。  
  
 [in] `nLargeImageIndex`  
 大型影像出現在按鈕上的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenableautomaticbuttona--cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton  
 指定是否啟用 [自動]  按鈕。  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE,  
    LPCTSTR lpszToolTip=NULL,  
    BOOL bOnTop=TRUE,  
    BOOL bDrawBorder=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 標籤**自動** 按鈕。  
  
 [in] `colorAutomatic`  
 RGB 值，指定**自動**按鈕的預設色彩。  
  
 [in] `bEnable`  
 `TRUE`如果**自動**已啟用 按鈕。`FALSE`如果已停用。  
  
 [in] `lpszToolTip`  
 工具提示的**自動** 按鈕。  
  
 [in] `bOnTop`  
 指定是否**自動**按鈕位於最上層之前的調色盤。  
  
 [in] `bDrawBorder`  
 `TRUE`如果應用程式在功能區色彩按鈕上繪製框線色彩。 色軸會顯示目前選取的色彩。 `FALSE`如果應用程式不繪製框線  
  
##  <a name="a-nameenableotherbuttona--cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton  
 啟用 [其他]  按鈕。  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    LPCTSTR lpszToolTip=NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszLabel`  
 按鈕的標籤。  
  
 `lpszToolTip`  
 工具提示文字**其他** 按鈕。  
  
### <a name="remarks"></a>備註  
 **其他**按鈕是會顯示色彩的群組下方的按鈕。 當使用者按一下**其他** 按鈕，它會顯示色彩 對話方塊。  
  
##  <a name="a-namegetautomaticcolora--cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor  
 擷取目前自動按鈕的色彩。  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值，表示目前自動按鈕的色彩。  
  
### <a name="remarks"></a>備註  
 設定自動按鈕的色彩`colorAutomatic`參數傳遞至`CMFCRibbonColorButton::EnableAutomaticButton`方法。  
  
##  <a name="a-namegetcolora--cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a>CMFCRibbonColorButton::GetColor  
 傳回目前選取的色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按一下 [] 按鈕選取的色彩。  
  
##  <a name="a-namegetcolorboxsizea--cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize  
 傳回色軸顯示的色彩項目大小。  
  
```  
CSize GetColorBoxSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式色彩調色盤的色彩按鈕大小。  
  
##  <a name="a-namegetcolumnsa--cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns  
 功能區色彩按鈕組件庫顯示的資料列中取得的項目數。  
  
```  
int GetColumns() const;  
```  
  
### <a name="return-value"></a>傳回值  
 每個資料列中傳回圖示的數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegethighlightedcolora--cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor  
 傳回目前所選元素的色彩在快顯的色板。  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的項目在快顯的調色盤色彩。  
  
##  <a name="a-nameremoveallcolorgroupsa--cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups  
 從標準色彩區域移除所有色彩群組。  
  
```  
void RemoveAllColorGroups();
```  
  
##  <a name="a-namesetcolora--cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCRibbonColorButton::SetColor  
 從標準色彩區域選取色彩。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 若要設定的色彩。  
  
##  <a name="a-namesetcolorboxsizea--cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize  
 設定色軸顯示之所有色彩項目的大小。  
  
```  
void SetColorBoxSize(CSize sizeBox);
```  
  
### <a name="parameters"></a>參數  
 [in] `sizeBox`  
 中的色彩調色盤的色彩按鈕，新的大小。  
  
##  <a name="a-namesetcolornamea--cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName  
 設定指定的色彩的新名稱。  
  
```  
static void __stdcall SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 RGB 色彩的值。  
  
 [in] `strName`  
 指定的色彩新名稱。  
  
### <a name="remarks"></a>備註  
 因為它會呼叫`CMFCColorBar::SetColorName`，這個方法會變更在所有指定的色彩名稱`CMFCColorBar`應用程式中的物件。  
  
##  <a name="a-namesetcolumnsa--cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns  
 設定使用者的色彩選擇程序期間呈現給使用者的色彩表中顯示的資料行數目。  
  
```  
void SetColumns(int nColumns);
```  
  
### <a name="parameters"></a>參數  
 [in] `nColumns`  
 色彩圖示以顯示每個資料列數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetdocumentcolorsa--cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors  
 指定文件色彩區域顯示的 RGB 值清單。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 若要使用文件色彩來顯示文字。  
  
 [in] `lstColors`  
 RGB 值的清單參考。  
  
##  <a name="a-namesetpalettea--cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCRibbonColorButton::SetPalette  
 指定要顯示在 [色彩] 按鈕會顯示色彩表中的標準色彩。  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPalette`  
 色彩調色盤指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameupdatecolora--cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor  
 當使用者選取色彩的色彩表顯示當使用者按一下色彩按鈕，從由架構呼叫。  
  
```  
void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 使用者選取的色彩。  
  
### <a name="remarks"></a>備註  
 `CMFCRibbonColorButton::UpdateColor`方法變更目前選取之的按鈕的色彩，並會傳送通知其父代`WM_COMMAND`訊息`BN_CLICKED`的標準通知。 使用[CMFCRibbonColorButton::GetColor](#getcolor)方法來擷取所選取的色彩。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)

