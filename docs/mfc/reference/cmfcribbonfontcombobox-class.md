---
title: CMFCRibbonFontComboBox 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86a46614cdb61e39af1016e496b12518b87f59ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370503"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox 類別
實作包含字型清單的下拉式方塊。 您可以在功能區面板上放置下拉式方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|解構函式。|  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|建構並初始化 `CMFCRibbonFontComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|在功能區字型下拉式方塊中填入指定字型類型的字型、字元集，及字距和系列。|  
|`CMFCRibbonFontComboBox::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|傳回指定的字元集。|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|傳回在下拉式方塊中顯示之字型的字距和系列。|  
|`CMFCRibbonFontComboBox::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|在功能區字型下拉式方塊中填入先前指定之字型類型的字型、字元集，及字距和系列。|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|在下拉式方塊中選取指定的字型。|  
  
## <a name="remarks"></a>備註  
 在建立之後`CMFCRibbonFontComboBox`物件，請將它加入至功能區面板中，藉由呼叫[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxRibbonComboBox.h  
  
##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts  
 在功能區字型下拉式方塊中填入。  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nFontType`  
 指定要加入字型的字型類型。  
  
 [輸入] `nCharSet`  
 指定要加入字型的字元集。  
  
 [輸入] `nPitchAndFamily`  
 指定字距和系列新增的字型。  
  
##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
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
 [輸入] `nID`  
 當使用者從下拉式方塊選取項目時執行命令的命令識別碼。  
  
 [輸入] `nFontType`  
 指定要顯示在下拉式方塊中的哪一種字型類型。 有效的選項為**DEVICE_FONTTYPE**， **RASTER_FONTTYPE**，和**TRUETYPE_FONTTYPE**，或任何位元組合。  
  
 [輸入] `nCharSet`  
 篩選出隸屬於指定的字元集的下拉式方塊中的字型...  
  
 [輸入] `nPitchAndFamily`  
 指定的字距和下拉式方塊中顯示的字型系列。  
  
 [輸入] `nWidth`  
 像素為單位的下拉式方塊中指定的寬度。  
  
### <a name="remarks"></a>備註  
 如需有關可能`nFontType`參數值，請參閱[EnumFontFamProc](http://msdn.microsoft.com/library/windows/desktop/dd162621) Windows SDK 文件中。  
  
 如需有關有效的字元集，可以指派給`nCharSet`，以及有效的值指派給`nPitchAndFamily`，請參閱[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) Windows SDK 文件中。  
  
##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts  
 先前指定的字型類型、 字元集，及字距和系列的功能區字型下拉式方塊中填入。  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>備註  
 您可以指定字型類型、 字元集，及字距和系列的字型包含在功能區字型下拉式方塊中，方塊中[建構函式](#cmfcribbonfontcombobox)這個類別，或藉由呼叫[CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont  
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
 指定選取之字型的字元集。  
  
 `bExact`  
 `TRUE` 若要指定選取的字型; 時，必須符合的字元集`FALSE`指定選取字型時，可以忽略的字集。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果找到指定的字型，而且選取;否則為零。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet  
 傳回指定的字元集。  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>傳回值  
 字元集 （請參閱 Windows SDK 文件中的 LOGFONT）。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType  
 傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 （請參閱 Windows SDK 文件中的 EnumFontFamProc） 的字型類型。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily  
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
