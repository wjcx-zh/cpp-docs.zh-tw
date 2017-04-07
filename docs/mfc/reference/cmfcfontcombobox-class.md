---
title: "CMFCFontComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontComboBox::DrawItem method
- CMFCFontComboBox::PreTranslateMessage method
- CMFCFontComboBox::MeasureItem method
- CMFCFontComboBox class
- CMFCFontComboBox::CompareItem method
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
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
ms.openlocfilehash: 1252f5ca102637e70cc384afd723464aec4144b4
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox 類別
`CMFCFontComboBox`類別會建立包含字型清單的下拉式方塊控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|建構 `CMFCFontComboBox` 物件。|  
|`CMFCFontComboBox::~CMFCFontComboBox`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|若要判斷目前的字型下拉式方塊控制項的已排序的清單方塊中的相對位置的新項目架構呼叫。 (覆寫[CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)。)|  
|`CMFCFontComboBox::DrawItem`|若要在目前的字型下拉式方塊控制項中繪製指定的項目架構呼叫。 (覆寫[CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem)。)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|擷取目前選取的字型相關資訊。|  
|`CMFCFontComboBox::MeasureItem`|呼叫以通知 Windows 清單方塊，目前的字型下拉式方塊控制項中的維度的架構。 (覆寫[CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)。)|  
|`CMFCFontComboBox::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCFontComboBox::SelectFont](#selectfont)|選取符合指定的準則從字型下拉式方塊的字型。|  
|[CMFCFontComboBox::Setup](#setup)|初始化字型下拉式方塊中的項目清單。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|架構會指出哪一種用來繪製目前的字型下拉式方塊中的項目標籤的字型。|  
  
## <a name="remarks"></a>備註  
 若要使用`CMFCFontComboBox`物件在對話方塊中，並將`CMFCFontComboBox`變數加入對話方塊類別。 接著在`OnInitDialog`方法的對話方塊類別，呼叫[CMFCFontComboBox::Setup](#setup)方法來初始化下拉式方塊控制項中的項目清單。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxfontcombobox.h  
  
##  <a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox  
 建構 `CMFCFontComboBox` 物件。  
  
```  
CMFCFontComboBox();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getselfont"></a>CMFCFontComboBox::GetSelFont  
 擷取目前選取的字型相關資訊。  
  
```  
CMFCFontInfo* GetSelFont() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)描述字型的物件。 它可以是`NULL`如果下拉式方塊中選取的字型。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont  
 架構會指出哪一種用來繪製目前的字型下拉式方塊中的項目標籤的字型。  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>備註  
 這個成員設定為`TRUE`導向的架構，用來繪製每個項目標籤的相同字型。 這個成員設定為`FALSE`導向的架構，來繪製每個項目有標籤名稱等同於標籤的字型。 預設值，這個成員是`FALSE`。  
  
##  <a name="selectfont"></a>CMFCFontComboBox::SelectFont  
 選取符合指定的準則從字型下拉式方塊的字型。  
  
```  
BOOL SelectFont(CMFCFontInfo* pDesc);

 
BOOL SelectFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDesc`  
 字型描述物件的指標。  
  
 [in] `lpszName`  
 指定的字型名稱。  
  
 [in] `nCharSet`  
 指定的字元集。 預設值是 DEFAULT_CHARSET。 如需詳細資訊，請參閱`lfCharSet`成員[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果字型下拉式方塊中的項目符合描述物件，指定的字型或字型名稱，其字元集。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用這個方法來選取及捲動到對應至指定的字型的字型下拉式方塊中的項目。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SelectFont`方法中的`CMFCFontComboBox`類別。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&34;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&35;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
##  <a name="setup"></a>CMFCFontComboBox::Setup  
 初始化字型下拉式方塊中的項目清單。  
  
```  
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFontType`  
 指定字型類型。 預設值是 DEVICE_FONTTYPE、 RASTER_FONTTYPE，和 TRUETYPE_FONTTYPE 合 (OR)。  
  
 [in] `nCharSet`  
 指定字型字元集。 預設值是 DEFAULT_CHARSET。  
  
 [in] `nPitchAndFamily`  
 指定字型的行距和系列。 預設值是 DEFAULT_PITCH。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果字型下拉式方塊初始化成功。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會列舉符合指定的參數的目前已安裝的字型，並將字型下拉式方塊中插入這些字型名稱初始化字型下拉式方塊。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Setup`方法中的`CMFCFontComboBox`類別。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&34;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&36;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)

