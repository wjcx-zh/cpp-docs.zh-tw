---
title: "CMFCRibbonFontComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonFontComboBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonFontComboBox class
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
caps.latest.revision: 24
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
ms.openlocfilehash: 851ef15013ca62012931fd92baf277d5db96033d
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox 類別
實作包含字型清單的下拉式方塊。 您可以在功能區面板上放置下拉式方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|解構函式。|  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|建構並初始化 `CMFCRibbonFontComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|在功能區字型下拉式方塊中填入指定字型類型的字型、字元集，及字距和系列。|  
|`CMFCRibbonFontComboBox::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|傳回指定的字元集。|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|傳回在下拉式方塊中顯示之字型的字距和系列。|  
|`CMFCRibbonFontComboBox::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|在功能區字型下拉式方塊中填入先前指定之字型類型的字型、字元集，及字距和系列。|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|在下拉式方塊中選取指定的字型。|  
  
## <a name="remarks"></a>備註  
 在建立之後`CMFCRibbonFontComboBox`物件，將它加入至功能區面板中，藉由呼叫[CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonComboBox.h  
  
##  <a name="a-namebuildfontsa--cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts  
 填入下拉式方塊，在功能區中的字型。  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFontType`  
 指定將字型的字型類型。  
  
 [in] `nCharSet`  
 指定要加入字型的字元集。  
  
 [in] `nPitchAndFamily`  
 指定的頻率和新增的字型系列。  
  
##  <a name="a-namecmfcribbonfontcomboboxa--cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
 建構並初始化[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)物件。  
  
```  
CMFCRibbonFontComboBox(
    UINT nID,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH,  
    int nWidth = -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 當使用者從下拉式方塊選取項目時執行命令的命令識別碼。  
  
 [in] `nFontType`  
 指定哪一種字型下拉式方塊中顯示型別。 有效的選項為**DEVICE_FONTTYPE**， **RASTER_FONTTYPE**，和**TRUETYPE_FONTTYPE**，或任何位元組合。  
  
 [in] `nCharSet`  
 篩選出屬於指定的字元集的下拉式方塊中的字型...  
  
 [in] `nPitchAndFamily`  
 指定繞和下拉式方塊中顯示的字型系列。  
  
 [in] `nWidth`  
 像素為單位的下拉式方塊中指定的寬度。  
  
### <a name="remarks"></a>備註  
 如需有關可能`nFontType`參數值，請參閱[EnumFontFamProc](http://msdn.microsoft.com/library/windows/desktop/dd162621) Windows SDK 文件中。  
  
 如需有關有效的字元集，您可以指派給`nCharSet,`和有效的值指派給`nPitchAndFamily`，請參閱[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) Windows SDK 文件中。  
  
##  <a name="a-namegetfontdesca--cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerebuildfontsa--cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts  
 填入下拉式方塊的字型功能區上的先前指定的字型類型、 字元集和音調和系列。  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>備註  
 您可以指定字型類型、 字元集，以及要包含在功能區字型下拉式方塊中的字型系列和方塊中[建構函式](#cmfcribbonfontcombobox)對於此類別，或藉由呼叫[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)。  
  
##  <a name="a-namesetfonta--cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFCRibbonFontComboBox::SetFont  
 在下拉式方塊中選取指定的字型。  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 指定要選取的字型名稱。  
  
 `nCharSet`  
 指定選取的字型的字元集。  
  
 `bExact`  
 `TRUE`若要指定選取的字型; 時，必須符合的字集`FALSE`指定選取字型時，可以忽略的字集。  
  
### <a name="return-value"></a>傳回值  
 如果找到並選取; 指定的字型，非零值。反之則為零。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcharseta--cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet  
 傳回指定的字元集。  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>傳回值  
 字集 （請參閱 Windows SDK 文件中的 LOGFONT）。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetfonttypea--cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType  
 傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 （請參閱 Windows SDK 文件中的 EnumFontFamProc） 的字型。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetpitchandfamilya--cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily  
 傳回在下拉式方塊中顯示之字型的字距和系列。  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>傳回值  
 字距和系列 （請參閱 Windows SDK 文件中的 LOGFONT）。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox 類別](../../mfc/reference/cmfcribboncombobox-class.md)

