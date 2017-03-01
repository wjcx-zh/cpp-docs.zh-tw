---
title: "CMFCToolBarFontComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox class
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
caps.latest.revision: 29
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
ms.openlocfilehash: 50b22e19cab4f434ec53383c8a170344e89cbab0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 類別
包含可讓使用者從系統字型的清單選取字型的下拉式方塊控制項的工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|建構 `CMFCToolBarFontComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|傳回的指標`CMFCFontInfo`下拉式方塊中指定之索引的物件。|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|字型的名稱或字型的前置詞和字元集合會依據 字型下拉式方塊中選取字型。|  
  
### <a name="data-members"></a>資料成員  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 字型下拉式方塊中之字元的高度。  
  
## <a name="remarks"></a>備註  
 若要將字型下拉式方塊按鈕加入至工具列，請遵循下列步驟︰  
  
1.  為父工具列資源的按鈕保留假的資源 ID。  
  
2.  建構`CMFCToolBarFontComboBox`物件。  
  
3.  在訊息處理常式中處理`AFX_WM_RESETTOOLBAR`訊息，請以新的下拉式方塊按鈕取代原始的按鈕，使用[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
4.  同步處理的下拉式方塊中的文件中的字型選取使用的字型[CMFCToolBarFontComboBox::SetFont](#setfont)方法。  
  
 若要使用下拉式方塊中選取的字型，同步處理文件的字型，請使用[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)方法來擷取選取的字型屬性，並使用這些屬性來建立[CFont 類別](../../mfc/reference/cfont-class.md)物件。  
  
 字型下拉式方塊按鈕會呼叫 Win32 函式[EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620)來判斷系統可用的螢幕及印表機字型。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbarfontcombobox.h  
  
##  <a name="a-namecmfctoolbarfontcomboboxa--cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
 建構[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)物件。  
  
```  
public:  
CMFCToolBarFontComboBox(
    UINT uiID,  
    int iImage,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    DWORD dwStyle = CBS_DROPDOWN,  
    int iWidth = 0,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);

 
protected:  
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,  
    int nFontType,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily);  
  
CMFCToolBarFontComboBox();
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 下拉式方塊的命令 ID。  
  
 [in] `iImage`  
 工具列按鈕影像的以零為起始的索引。 映像位於[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別會維護。  
  
 [in] `nFontType`  
 字型下拉式方塊包含型別。 這個參數可以是下列值的組合 (布林值 OR):  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [in] `nCharSet`  
 如果設定為 DEFAULT_CHARSET，下拉式方塊包含所有字元集中的所有唯一名稱的字型。 （如果有兩個具有相同名稱的字型，下拉式方塊包含其中一個）。如果設定為有效的字元設定的值，下拉式方塊包含指定的字元集中的字型。 請參閱[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)的可能字元清單設定。  
  
 [in] `dwStyle`  
 下拉式方塊樣式。 (請參閱[下拉式方塊樣式](../../mfc/reference/combo-box-styles.md))  
  
 [in] `iWidth`  
 單位為像素編輯控制項的寬度。  
  
 [in] `nPitchAndFamily`  
 如果設定為 DEFAULT_PITCH，下拉式方塊包含不論字幅的字型。 如果設定為 FIXED_PITCH 或 VARIABLE_PITCH，下拉式方塊包含只與該音調類型的字型。 目前不支援基礎字型家族的篩選。  
  
 [輸出] `pLstFontsExternal`  
 指標[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中儲存可用的字型。  
  
### <a name="remarks"></a>備註  
 通常，`CMFCToolBarFontComboBox`物件使用的字型清單儲存於單一共用`CObList`物件。 如果您使用建構函式的第二個多載，並提供有效指標`pLstFontsExternal`，`CMFCToolBarFontComboBox`物件將會改為填滿`CObList`，`pLstFontsExternal`指向可用的字型。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構`CMFCToolBarFontComboBox`物件。 此程式碼片段是一部分[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&7;](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="a-namegetfontdesca--cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc  
 傳回的指標`CMFCFontInfo`下拉式方塊中指定之索引的物件。  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 指定的下拉式方塊項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCFontInfo`物件。 如果`iIndex`未指定有效的項目索引，則傳回值是`NULL`。  
  
##  <a name="a-namemnfontheighta--cmfctoolbarfontcomboboxmnfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight  
 指定高度，單位為像素下拉式方塊的擁有者繪製樣式的字型下拉式方塊中的字元。  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>備註  
 如果`m_nFontHeight`變數是 0，則根據下拉式方塊的預設字型自動計算高度。 高度同時包含的基準上方字元高度和深度的基準線下方的字元。  
  
##  <a name="a-namesetfonta--cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontComboBox::SetFont  
 選取的字型名稱與字元字型下拉式方塊中的字型設定的參數中指定。  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszName`  
 指定字型名稱的前置詞。  
  
 [in] `nCharSet`  
 指定的字元集。  
  
 [in] `bExact`  
 指定是否`lpszName`包含字型的名稱或字型前置詞。  
  
### <a name="return-value"></a>傳回值  
 非零，如果選取的字型已順利啟動。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`bExact`是`TRUE`，這個方法也會選取與您指定為名稱完全相符的字型`lpszName`。 如果`bExact`是`FALSE`，這個方法會選取開頭為指定的文字字型`lpszName`，並使用您指定為字元集`nCharSet`。 如果`nCharSet`設為 DEFAULT_CHARSET，字元集會忽略，而且只`lpszName`將用來選取字型。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說︰ 將放在工具列上的控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)




