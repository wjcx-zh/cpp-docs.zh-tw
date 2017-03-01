---
title: "CMFCColorButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorButton::m_Color data member
- CMFCColorButton::m_bAutoSetFocus data member
- CMFCColorButton::m_pPopup data member
- CMFCColorButton::m_nColumns data member
- CMFCColorButton class
- CMFCColorButton::m_strAutoColorText data member
- CMFCColorButton::m_bAltColorDlg data member
- CMFCColorButton::m_strDocColorsText data member
- CMFCColorButton::m_strOtherText data member
- CMFCColorButton::m_pPalette data member
- CMFCColorButton::m_lstDocColors data member
- CMFCColorButton::m_ColorAutomatic data member
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
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
ms.openlocfilehash: 6a9290d396c8ce5ccafa2ae556b21ff89806d830
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 類別
`CMFCColorButton`和[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)類別會一起用來實作色彩選擇器控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|建構新`CMFCColorButton`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|啟用和停用規則的色彩按鈕上方位於 「 自動 」 按鈕。 (標準系統自動按鈕標記**自動**。)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|啟用和停用規則的色彩按鈕位於 [其他] 按鈕。 (標準的系統標示為 「 其他 」 按鈕**更多色彩...**.)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|擷取目前的自動色彩。|  
|[CMFCColorButton::GetColor](#getcolor)|擷取按鈕的色彩。|  
|[CMFCColorButton::SetColor](#setcolor)|設定按鈕的色彩。|  
|[CMFCColorButton::SetColorName](#setcolorname)|設定色彩名稱。|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|設定色彩選擇器對話方塊的資料行數目。|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|指定色彩選擇器 對話方塊顯示的文件特定色彩的清單。|  
|[CMFCColorButton::SetPalette](#setpalette)|指定標準的顯示色彩的調色盤。|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|變更大小的按鈕控制項，視其文字和影像的大小而定。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|指出是否要將目前的色彩按鈕顯示在 Windows XP 視覺化樣式。|  
|[CMFCColorButton::OnDraw](#ondraw)|若要顯示的按鈕影像架構呼叫。|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|若要顯示按鈕的框線架構呼叫。|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|若要顯示焦點矩形按鈕具有焦點時架構呼叫。|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|顯示色彩選擇器對話方塊時，由架構呼叫。|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|初始化`m_pPalette`受保護的資料成員指定的調色盤或預設的系統調色盤。|  
|[CMFCColorButton::UpdateColor](#updatecolor)|當使用者從色彩選擇器對話方塊的調色盤選取色彩，由架構呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|`m_bAltColorDlg`|布林值。 如果`TRUE`，架構會顯示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)色彩對話方塊時*其他*按一下按鈕時，或如果`FALSE`，系統的 [色彩] 對話方塊。 預設值是 `TRUE`。 如需詳細資訊，請參閱[CMFCColorButton::EnableOtherButton](#enableotherbutton)。|  
|`m_bAutoSetFocus`|布林值。 如果`TRUE`，架構將焦點設在 [色彩] 功能表或功能表顯示時，如果`FALSE`，不會變更焦點。 預設值是 `TRUE`。|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指出是否啟用 [色彩] 按鈕的自訂模式。|  
|`m_Color`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含目前選取的色彩。|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含目前選取的預設色彩。|  
|`m_Colors`|A [CArray](../../mfc/reference/carray-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含目前可用的色彩。|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含目前的文件色彩。|  
|`m_nColumns`|整數。 包含要顯示的格線色彩選取功能表中的色彩中的資料行數目。|  
|`m_pPalette`|指標[CPalette](../../mfc/reference/cpalette-class.md)。 包含目前的色彩選取功能表中可用的色彩。|  
|`m_pPopup`|指標[CMFCColorPopupMenu 類別](../../mfc/reference/cmfccolorpopupmenu-class.md)物件。 當您按一下色彩按鈕會顯示色彩選取功能表。|  
|`m_strAutoColorText`|字串。 色彩選取功能表中的 「 自動 」 按鈕的標籤。|  
|`m_strDocColorsText`|字串。 顯示文件色彩的色彩選取功能表中的按鈕標籤。|  
|`m_strOtherText`|字串。 色彩選取功能表中的 「 其他 」 按鈕的標籤。|  
  
## <a name="remarks"></a>備註  
 根據預設，`CMFCColorButton`類別行為，以開啟色彩選擇器對話方塊的按鈕。 色彩選擇器對話方塊包含陣列的小型彩色按鈕及顯示自訂色彩選擇器 的 其他 按鈕。 (標準的系統標示為 「 其他 」 按鈕**更多色彩...**.)當使用者選取新的色彩，`CMFCColorButton`物件會反映出變更，並顯示選取的色彩。  
  
 建立色彩的按鈕控制項，直接在程式碼，或使用**ClassWizard**工具和對話方塊範本。 如果您直接建立色彩的按鈕控制項，將`CMFCColorButton`變數與您的應用程式，然後呼叫建構函式和`Create`方法`CMFCColorButton`物件。 如果您使用**ClassWizard**，加入`CButton`變數設為您的應用程式，然後變更變數的型別`CButton`到`CMFCColorButton`。  
  
 色彩選擇器對話方塊 ( [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)) 會顯示[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)方法時，架構會呼叫`OnLButtonDown`事件處理常式。 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)可以覆寫方法，以支援自訂色彩選取項目。  
  
 `CMFCColorButton`物件通知色彩變更傳送其父代`WM_COMMAND | BN_CLICKED`通知。 父系會使用[CMFCColorButton::GetColor](#getcolor)方法來擷取目前的色彩。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法中的設定的色彩按鈕`CMFCColorButton`類別。 方法會設定色彩的色彩按鈕和其資料行的數目，並讓自動和其他按鈕。 這個範例是屬於[狀態列示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo #&10;](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo #&11;](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcolorbutton.h  
  
##  <a name="a-namecmfccolorbuttona--cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton  
 建構新`CMFCColorButton`物件。  
  
```  
CMFCColorButton();
```  
  
##  <a name="a-nameenableautomaticbuttona--cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton  
 啟用或停用色彩選擇器控制項的 「 自動 」 按鈕，並設定自動 （預設） 的色彩。  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 指定自動按鈕的文字。  
  
 [in] `colorAutomatic`  
 指定自動按鈕的預設色彩的 RGB 值。  
  
 [in] `bEnable`  
 指定是否啟用或停用 [自動] 按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenableotherbuttona--cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton  
 啟用或停用的 「 其他 」 按鈕，會出現一般的色彩按鈕下方。  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 指定按鈕的文字。  
  
 [in] `bAltColorDlg`  
 指定是否[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)當使用者按一下按鈕開啟對話方塊或系統的 [色彩] 對話方塊。  
  
 [in] `bEnable`  
 指定是否啟用或停用 「 其他 」 按鈕。  
  
### <a name="remarks"></a>備註  
 按一下 [其他] 按鈕以顯示一個對話方塊。 如果*bAltColorDlg*參數是`TRUE`、 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)會顯示; 否則就會顯示系統的 [色彩] 對話方塊。  
  
##  <a name="a-namegetautomaticcolora--cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor  
 擷取目前的自動 （預設） 色彩。  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 代表目前的自動色彩的 RGB 值。  
  
### <a name="remarks"></a>備註  
 目前的自動色彩會設定[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)方法。  
  
##  <a name="a-namegetcolora--cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFCColorButton::GetColor  
 擷取目前選取的色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdrawxpthemea--cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme  
 指出是否要將目前的色彩按鈕顯示在 Windows XP 視覺化樣式。  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果有支援視覺化樣式和目前的色彩按鈕會顯示在 Windows XP; 的視覺化樣式否則， `FALSE`。  
  
##  <a name="a-namembenabledincustomizemodea--cmfccolorbuttonmbenabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode  
 將色彩按鈕設定為自訂模式。  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>備註  
 如果您要加入自訂對話方塊頁面的色彩按鈕 （或允許使用者選擇其他色彩選項，在自訂期間），啟用 按鈕設定`m_bEnabledInCustomizeMode`成員`TRUE`。 根據預設，這個成員設定為`FALSE`。  
  
##  <a name="a-nameondrawa--cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFCColorButton::OnDraw  
 呼叫架構來呈現按鈕的影像。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 用來呈現按鈕的影像的裝置內容的指標。  
  
 [in] `rect`  
 限定的矩形的按鈕。  
  
 [in] `uiState`  
 指定按鈕的可見狀態。  
  
### <a name="remarks"></a>備註  
 覆寫此方法來自訂轉譯程序。  
  
##  <a name="a-nameondrawbordera--cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder  
 若要顯示按鈕的框線架構呼叫。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 用來繪製框線的裝置內容的指標。  
  
 [in] `rectClient`  
 在裝置內容所指定的矩形`pDC`參數，定義要繪製按鈕的界限。  
  
 [in] `uiState`  
 指定按鈕的可見狀態。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來自訂 [色彩] 按鈕的框線外觀。  
  
##  <a name="a-nameondrawfocusrecta--cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect  
 若要顯示焦點矩形按鈕具有焦點時架構呼叫。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 用來繪製焦點矩形的裝置內容的指標。  
  
 [in] `rectClient`  
 在所指定的裝置內容的矩形`pDC`參數，定義按鈕的界限。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以自訂的焦點矩形的外觀。  
  
##  <a name="a-nameonshowcolorpopupa--cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup  
 快顯色軸會顯示之前呼叫。  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerebuildpalettea--cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette  
 初始化`m_pPalette`受保護的資料成員指定的調色盤或預設的系統調色盤。  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pPal`|邏輯調色盤的指標或`NULL`。 如果`NULL`，會使用預設的系統調色盤。|  
  
##  <a name="a-namesetcolora--cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCColorButton::SetColor  
 指定按鈕的色彩。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 RGB 值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetcolornamea--cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorButton::SetColorName  
 指定的色彩名稱。  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 此色彩的 RGB 值。  
  
 [in] `strName`  
 此色彩的名稱。  
  
### <a name="remarks"></a>備註  
 色彩名稱清單是每個應用程式的全域範圍。 因此，這個方法會將傳輸至其參數[CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。  
  
##  <a name="a-namesetcolumnsnumbera--cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber  
 定義使用者的色彩選擇程序期間呈現給使用者的色彩表中所顯示的資料行數目。  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>參數  
 [in] `nColumns`  
 指定資料行數目。  
  
### <a name="remarks"></a>備註  
 使用者可以從快顯色軸顯示預先定義之色彩的色彩。 使用此方法在資料表中定義的資料行數目。  
  
##  <a name="a-namesetdocumentcolorsa--cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors  
 指定一組色彩和集的名稱。 使用顯示的色彩設定[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 指定要使用的文件色彩來顯示標籤。  
  
 [in] `lstColors`  
 RGB 值的清單參考。  
  
### <a name="remarks"></a>備註  
 A`CMFCColorButton`物件會維護一份 RGB 值傳送至[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件。 這些色彩色軸顯示時，會顯示其標籤所指定的特殊區段`lpszLabel`參數。  
  
##  <a name="a-namesetpalettea--cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCColorButton::SetPalette  
 指定要在快顯色軸上顯示標準的色彩。  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPalette`  
 色彩調色盤指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesizetocontenta--cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCColorButton::SizeToContent  
 調整大小以配合其文字和影像的按鈕控制項。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bCalcOnly`  
 如果是非零值，新的按鈕控制項的大小進行計算，但不是會變更的實際大小。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，指定新的按鈕控制項大小。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameupdatecolora--cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCColorButton::UpdateColor  
 當使用者選取一個色彩從色軸會顯示當使用者按一下 [色彩] 按鈕，由架構呼叫。  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 使用者選取的色彩。  
  
### <a name="remarks"></a>備註  
 `UpdateColor`函式會變更目前選取之的按鈕的色彩，並會傳送通知其父代`WM_COMMAND`訊息`BN_CLICKED`的標準通知。 使用[CMFCColorButton::GetColor](#getcolor)方法來擷取所選取的色彩。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)   
 [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette 類別](../../mfc/reference/cpalette-class.md)   
 [CArray 類別](../../mfc/reference/carray-class.md)   
 [CList 類別](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)

