---
title: CMFCToolBarFontComboBox 類別 |Microsoft 文件
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
ms.openlocfilehash: 3826a1a649cf4a2c3f292b660e90384edac2575e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040086"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 類別
包含可讓使用者從系統字型的清單選取字型下拉式方塊控制項的工具列按鈕。  
  
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
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|將指標傳回至`CMFCFontInfo`下拉式方塊中的指定索引的物件。|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|字型的名稱或前置字元和字元組的字型，請根據 字型下拉式方塊中選取的字型。|  
  
### <a name="data-members"></a>資料成員  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 字型下拉式方塊中之字元的高度。  
  
## <a name="remarks"></a>備註  
 若要將字型下拉式方塊按鈕加入至工具列，請遵循下列步驟：  
  
1.  為父工具列資源的按鈕保留假的資源 ID。  
  
2.  建構`CMFCToolBarFontComboBox`物件。  
  
3.  處理 AFX_WM_RESETTOOLBAR 訊息的訊息處理常式，在 [原始] 按鈕，以取代新的下拉式方塊按鈕使用[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
4.  同步處理已選取下拉式方塊中的文件中的字型使用的字型[CMFCToolBarFontComboBox::SetFont](#setfont)方法。  
  
 若要同步處理文件的字型，與下拉式方塊中選取的字型，請使用[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)方法來擷取選取的字型屬性，並使用這些屬性來建立[CFont 類別](../../mfc/reference/cfont-class.md)物件。  
  
 字型下拉式方塊按鈕呼叫 Win32 函式[EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620)來決定供系統使用的螢幕及印表機字型。  
  
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
 工具列影像的以零為起始的索引。 映像位於[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別會維護。  
  
 [in]*nFontType*  
 下拉式方塊包含的字型類型。 這個參數可以是下列值的組合 (布林值 OR):  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [in]*nCharSet*  
 如果設定為 DEFAULT_CHARSET，下拉式方塊包含所有字元集中的所有唯一名稱的字型。 （如果有具有相同名稱的兩種字型，下拉式方塊包含其中一個）。如果設定為有效的字元設定值，而下拉式方塊包含只在指定的字元集的字型。 請參閱[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)的可能字元清單設定。  
  
 [in]*dwStyle*  
 下拉式方塊樣式。 (請參閱[下拉式方塊樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))  
  
 [in]*iWidth*  
 在編輯控制項的像素寬度。  
  
 [in]*nPitchAndFamily*  
 如果設定為 DEFAULT_PITCH，下拉式方塊包含不論字幅的字型。 如果設定為 FIXED_PITCH 或 VARIABLE_PITCH，下拉式方塊包含只與該音高類型的字型。 目前不支援字型系列為基礎的篩選。  
  
 [out]*pLstFontsExternal*  
 指標[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中儲存可用的字型。  
  
### <a name="remarks"></a>備註  
 通常，`CMFCToolBarFontComboBox`物件使用的字型清單儲存於單一共用`CObList`物件。 如果您使用建構函式的第二個多載，提供的有效指標*pLstFontsExternal*、 該`CMFCToolBarFontComboBox`物件將會改為填滿`CObList`， *pLstFontsExternal*指向以可用的字型。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構`CMFCToolBarFontComboBox`物件。 此程式碼片段是 [WordPad 範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc  
 將指標傳回至`CMFCFontInfo`下拉式方塊中的指定索引的物件。  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*iIndex*  
 指定下拉式方塊項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCFontInfo`物件。 如果*iIndex*未指定有效的項目索引，則傳回值是`NULL`。  
  
##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight  
 指定高度，單位為像素字型下拉式方塊的下拉式方塊是否擁有者繪製樣式中的字元。  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>備註  
 如果`m_nFontHeight`變數是 0，則根據預設字型下拉式方塊的高度會自動計算。 高度包含兩者的基準上方的字元 （堆疊） 和字元下方基準的深度。  
  
##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont  
 選取的字型名稱與字元字型下拉式方塊中的字型設定的參數中指定。  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszName*  
 指定字型名稱的前置詞。  
  
 [in]*nCharSet*  
 指定的字元集。  
  
 [in]*bExact*  
 指定是否*lpszName*包含字型名稱或字型前置詞。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 選取的字型為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果*bExact*是`TRUE`，這個方法會選取與您指定為名稱完全相符的字型*lpszName*。 如果*bExact*是`FALSE`，這個方法會選取開頭為指定之文字的字型*lpszName* ，並使用您指定為字元集*nCharSet*. 如果*nCharSet*設定的字元集到 DEFAULT_CHARSET，將會忽略和只有*lpszName*將用來選取字型的字型。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



