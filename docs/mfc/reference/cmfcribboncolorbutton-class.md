---
title: "CMFCRibbonColorButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8da5a7a05f1765fea840c579c91ddd9b3ef672b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton 類別
`CMFCRibbonColorButton` 類別實作可以加入功能區列中的色彩按鈕。 功能區色彩按鈕會顯示包含一個或多個色板的下拉式功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
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
 下例示範如何在 `CMFCRibbonColorButton` 類別中使用各種方法。 此範例示範如何建構 `CMFCRibbonColorButton` 物件、設定大型影像、啟用 [自動]  按鈕、啟用 [其他]  按鈕、設定資料行數目、設定色軸顯示的所有色彩項目大小、將色彩群組加入標準色彩區域中，以及指定文件色彩區域顯示的 RGB 值清單。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標題:** afxribboncolorbutton.h  
  
##  <a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup  
 將色彩群組加入標準色彩區域中。  
  
```  
void AddColorsGroup(
    LPCTSTR lpszName,  
    const CList<COLORREF,COLORREF>& lstColors,  
    BOOL bContiguousColumns=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszName`  
 群組名稱。  
  
 [輸入] `lstColors`  
 色彩的清單。  
  
 [輸入] `bContiguousColumns`  
 控制色彩項目群組中的顯示方式。 如果`TRUE`，色彩項目會繪製沒有垂直間距。 如果`FALSE`，以垂直間距繪製的色彩項目。  
  
### <a name="remarks"></a>備註  
 使用這個函式，使色彩的快顯會顯示數個群組的色彩。 您可以控制色彩群組中的顯示方式。  
  
##  <a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton  
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
 [輸入] `nID`  
 指定當使用者按一下按鈕時若要執行命令的命令識別碼。  
  
 [輸入] `lpszText`  
 指定要顯示在按鈕上的文字。  
  
 [輸入] `nSmallImageIndex`  
 會出現在按鈕上的小型影像以零為起始的索引。  
  
 [輸入] `color`  
 （預設為黑色） 按鈕的色彩。  
  
 [輸入] `bSimpleButtonLook`  
 如果`TRUE`，按鈕會繪製成的簡單矩形。  
  
 [輸入] `nLargeImageIndex`  
 在按鈕上顯示大型影像的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton  
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
 [輸入] `lpszLabel`  
 標籤**自動** 按鈕。  
  
 [輸入] `colorAutomatic`  
 RGB 值，指定**自動**按鈕的預設色彩。  
  
 [輸入] `bEnable`  
 `TRUE`如果**自動**按鈕已啟用。`FALSE`如果已停用。  
  
 [輸入] `lpszToolTip`  
 工具提示**自動** 按鈕。  
  
 [輸入] `bOnTop`  
 指定是否**自動**按鈕位於最上層之前色彩調色盤。  
  
 [輸入] `bDrawBorder`  
 `TRUE`如果應用程式功能區色彩按鈕上繪製框線色彩。 色軸會顯示目前選取的色彩。 `FALSE`如果應用程式不繪製框線  
  
##  <a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton  
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
 **其他**按鈕是顯示的色彩群組下方的按鈕。 當使用者按一下**其他**按鈕時，它會顯示 [色彩] 對話方塊。  
  
##  <a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor  
 擷取目前自動按鈕的色彩。  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值，表示目前自動按鈕的色彩。  
  
### <a name="remarks"></a>備註  
 設定自動按鈕的色彩`colorAutomatic`參數傳遞至`CMFCRibbonColorButton::EnableAutomaticButton`方法。  
  
##  <a name="getcolor"></a>CMFCRibbonColorButton::GetColor  
 傳回目前選取的色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 依序按一下 [] 按鈕選取的色彩。  
  
##  <a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize  
 傳回色軸顯示的色彩項目大小。  
  
```  
CSize GetColorBoxSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 中的下拉式色彩調色盤的色彩按鈕的大小。  
  
##  <a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns  
 取得功能區色彩按鈕圖庫顯示的資料列中的項目數目。  
  
```  
int GetColumns() const;  
```  
  
### <a name="return-value"></a>傳回值  
 每個資料列中傳回的圖示數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor  
 傳回快顯調色盤上的目前選取項目的色彩。  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 快顯調色盤上的目前選取項目的色彩。  
  
##  <a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups  
 從標準色彩區域移除所有色彩群組。  
  
```  
void RemoveAllColorGroups();
```  
  
##  <a name="setcolor"></a>CMFCRibbonColorButton::SetColor  
 從標準色彩區域選取色彩。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `color`  
 若要設定色彩。  
  
##  <a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize  
 設定色軸顯示之所有色彩項目的大小。  
  
```  
void SetColorBoxSize(CSize sizeBox);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `sizeBox`  
 中的色彩調色盤的色彩按鈕，新的大小。  
  
##  <a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName  
 設定指定的色彩的新名稱。  
  
```  
static void __stdcall SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `color`  
 色彩的 RGB 值。  
  
 [輸入] `strName`  
 指定的色彩的的新名稱。  
  
### <a name="remarks"></a>備註  
 因為它會呼叫`CMFCColorBar::SetColorName`，這個方法會變更在所有指定的色彩名稱`CMFCColorBar`應用程式中的物件。  
  
##  <a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns  
 設定使用者的色彩選取程序期間呈現給使用者的色彩表中顯示的資料行數目。  
  
```  
void SetColumns(int nColumns);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nColumns`  
 色彩圖示以顯示每個資料列數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors  
 指定文件色彩區域顯示的 RGB 值清單。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszLabel`  
 若要使用文件色彩來顯示文字。  
  
 [輸入] `lstColors`  
 參考的 RGB 值清單。  
  
##  <a name="setpalette"></a>CMFCRibbonColorButton::SetPalette  
 指定色彩按鈕會顯示色彩表中顯示標準的色彩。  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pPalette`  
 色彩調色盤指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor  
 當使用者從色彩資料表顯示當使用者按一下色彩按鈕，選取色彩，由架構呼叫。  
  
```  
void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `color`  
 使用者所選取之色彩。  
  
### <a name="remarks"></a>備註  
 `CMFCRibbonColorButton::UpdateColor`方法就會變更目前選取之按鈕的色彩，並會傳送通知其父代`WM_COMMAND`訊息`BN_CLICKED`標準的通知。 使用[CMFCRibbonColorButton::GetColor](#getcolor)方法來擷取所選的色彩。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)
