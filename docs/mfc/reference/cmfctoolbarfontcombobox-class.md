---
title: CMFCToolBarFontComboBox 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2625316aa731e658d9d45e495809d2402a3cb4c5
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849746"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 類別
包含可讓使用者從一份系統字型選取字型下拉式方塊控制項的工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|建構 `CMFCToolBarFontComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|將指標傳回至`CMFCFontInfo`下拉式方塊中指定索引的物件。|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|字型的名稱或前置詞和字元組的字型，請根據其中一個字型下拉式方塊中選取的字型。|  
  
### <a name="data-members"></a>資料成員  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 字型下拉式方塊中的字元高度。  
  
## <a name="remarks"></a>備註  
 字型下拉式方塊按鈕加入工具列，請遵循下列步驟：  
  
1.  為父工具列資源的按鈕保留假的資源 ID。  
  
2.  建構`CMFCToolBarFontComboBox`物件。  
  
3.  訊息處理常式中處理 AFX_WM_RESETTOOLBAR 訊息，原始的按鈕使用以取代新的下拉式方塊按鈕[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
4.  同步處理已選取下拉式方塊中的文件中的字型所使用的字型[CMFCToolBarFontComboBox::SetFont](#setfont)方法。  
  
 若要同步處理文件的字型，使用下拉式方塊中選取的字型，請使用[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)方法來擷取選取的字型屬性，並使用這些屬性來建立[CFont 類別](../../mfc/reference/cfont-class.md)物件。  
  
 字型下拉式方塊按鈕呼叫 Win32 函式[EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620)來判斷螢幕及印表機供系統使用的字型。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
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
 [in]*uiID*  
 下拉式方塊的命令識別碼。  
  
 [in]*iImage*  
 工具列影像之以零起始的索引。 映像位於[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別會負責維護。  
  
 [in]*nFontType*  
 字型下拉式方塊包含的類型。 這個參數可以是下列值的組合 (布林值 OR):  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [in]*nCharSet*  
 如果設為 DEFAULT_CHARSET，下拉式方塊包含所有字元集中的所有唯一名稱的字型。 （如果有具有相同名稱的兩種字型，下拉式方塊包含其中一個）。如果設為有效的字元組值，而下拉式方塊包含只在指定的字元集的字型。 請參閱[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)的可能字元清單的設定。  
  
 [in]*cheaderctrl:: Create*  
 下拉式方塊的樣式。 (請參閱[下拉式方塊樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))  
  
 [in]*iWidth*  
 像素為單位，編輯控制項的寬度。  
  
 [in]*nPitchAndFamily*  
 如果設為 DEFAULT_PITCH，下拉式方塊包含不論字幅的字型。 如果設定為 FIXED_PITCH 或 VARIABLE_PITCH，下拉式方塊包含僅透過這樣的字幅的字型。 目前不支援篩選根據字型家族。  
  
 [out]*pLstFontsExternal*  
 指標[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中儲存可用的字型。  
  
### <a name="remarks"></a>備註  
 通常`CMFCToolBarFontComboBox`物件使用的字型清單儲存於單一共用`CObList`物件。 如果您使用第二個多載的建構函式，並提供的有效指標*pLstFontsExternal*，、 該`CMFCToolBarFontComboBox`物件將會改為填滿`CObList`可*pLstFontsExternal*若要使用可用字型的點。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構`CMFCToolBarFontComboBox`物件。 此程式碼片段是 [WordPad 範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc  
 將指標傳回至`CMFCFontInfo`下拉式方塊中指定索引的物件。  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*iIndex*  
 指定下拉式方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `CMFCFontInfo` 物件的指標。 如果*iIndex*未指定有效的項目索引，則傳回值是 NULL。  
  
##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight  
 指定高度，單位為像素字型下拉式方塊下拉式方塊是否擁有者繪製樣式中的字元。  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>備註  
 如果`m_nFontHeight`變數為 0 時，根據預設字型下拉式方塊的高度會自動計算。 高度包括的基準以上的字元高度以及的基準線下方的字元深度。  
  
##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont  
 選取的字型名稱和字元根據字型下拉式方塊中的字型設定的參數中指定。  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszName*  
 指定的字型名稱或前置詞。  
  
 [in]*nCharSet*  
 指定的字元集。  
  
 [in]*bExact*  
 指定是否*lpszName*包含字型名稱或字型前置詞。  
  
### <a name="return-value"></a>傳回值  
 如果已順利啟動。 選取的字型為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果*bExact*為 TRUE 時，這個方法會選取與您指定為名稱完全相符的字型*lpszName*。 如果*bExact*為 FALSE 時，此方法會選取字型的文字開頭指定為*lpszName* ，並使用您指定為字元集*nCharSet*。 如果*nCharSet*設定為 DEFAULT_CHARSET 的字元集會忽略，而且只*lpszName*將用來選取字型的字型。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



