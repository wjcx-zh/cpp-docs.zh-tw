---
title: "CMFCFontComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 53958d1a9f2a2647a42405a2b535441dee162b70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox 類別
`CMFCFontComboBox`類別會建立包含字型清單的下拉式方塊控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|建構 `CMFCFontComboBox` 物件。|  
|`CMFCFontComboBox::~CMFCFontComboBox`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|由架構呼叫以判斷目前的字型下拉式方塊控制項的已排序的清單方塊中的新項目相對位置。 (覆寫[CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)。)|  
|`CMFCFontComboBox::DrawItem`|由架構呼叫以在目前的字型下拉式方塊控制項中繪製指定的項目。 (覆寫[CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem)。)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|擷取目前選取的字型相關資訊。|  
|`CMFCFontComboBox::MeasureItem`|由架構呼叫以通知 Windows 的清單方塊中目前的字型下拉式方塊控制項的維度。 (覆寫[CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)。)|  
|`CMFCFontComboBox::PreTranslateMessage`|將視窗訊息轉譯分派至之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCFontComboBox::SelectFont](#selectfont)|選取符合指定的準則從字型下拉式方塊的字型。|  
|[CMFCFontComboBox::Setup](#setup)|初始化字型下拉式方塊中的項目清單。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|向架構指出哪一種用來繪製目前的字型下拉式方塊中的項目標籤的字型。|  
  
## <a name="remarks"></a>備註  
 若要使用`CMFCFontComboBox`物件對話方塊中，並將`CMFCFontComboBox`變數加入對話方塊類別。 接著在`OnInitDialog`方法的對話方塊類別，呼叫[CMFCFontComboBox::Setup](#setup)方法來初始化下拉式方塊控制項中的項目清單。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxfontcombobox.h  
  
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
 向架構指出哪一種用來繪製目前的字型下拉式方塊中的項目標籤的字型。  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>備註  
 這個成員設定為`TRUE`導向架構，以使用的相同字型來繪製每個項目標籤。 這個成員設定為`FALSE`導向架構，以繪製其名稱等同於標籤的字型與每個項目標籤。 這個成員的預設值是`FALSE`。  
  
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
 指向字型描述物件。  
  
 [in] `lpszName`  
 指定的字型名稱。  
  
 [in] `nCharSet`  
 指定的字元集。 預設值是 DEFAULT_CHARSET。 如需詳細資訊，請參閱`lfCharSet`隸屬[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果字型下拉式方塊中的項目符合指定的字型描述物件或字型名稱和字元集。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用這個方法來選取及捲動到對應至指定的字型的字型下拉式方塊中的項目。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SelectFont`方法中的`CMFCFontComboBox`類別。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
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
 指定的字型類型。 預設值為 DEVICE_FONTTYPE、 RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 合 (OR)。  
  
 [in] `nCharSet`  
 指定字型的字元集。 預設值是 DEFAULT_CHARSET。  
  
 [in] `nPitchAndFamily`  
 指定字型的字距和系列。 預設值是 DEFAULT_PITCH。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果初始化成功; 字型下拉式方塊否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會列舉符合指定的參數的目前已安裝的字型，並插入字型下拉式方塊中的這些字型名稱，初始化字型下拉式方塊。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Setup`方法中的`CMFCFontComboBox`類別。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)
