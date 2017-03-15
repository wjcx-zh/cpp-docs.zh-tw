---
title: "CMFCPropertyGridFontProperty 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFontProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFontProperty::OnClickButton method
- CMFCPropertyGridFontProperty class
- CMFCPropertyGridFontProperty::FormatProperty method
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
caps.latest.revision: 23
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
ms.openlocfilehash: 05d1db7e7de2ee72244e885d8a083ac3cda20142
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 類別
`CMFCPropertyGridFileProperty`類別支援開啟字型選取對話方塊的屬性清單控制項項目。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|建構 `CMFCPropertyGridFontProperty` 物件。|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|格式化屬性值的文字表示法。 (覆寫[CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|  
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|擷取使用者從字型 對話方塊中選取的字型色彩。|  
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|擷取使用者從字型 對話方塊中選取的字型。|  
|`CMFCPropertyGridFontProperty::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|`CMFCPropertyGridFontProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。 (覆寫[CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|  
  
## <a name="remarks"></a>備註  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxpropertygridctrl.h  
  
##  <a name="a-namecmfcpropertygridfontpropertya--cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty  
 建構 `CMFCPropertyGridFontProperty` 物件。  
  
```  
CMFCPropertyGridFontProperty(
    const CString& strName,  
    LOGFONT& lf,  
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `strName`  
 屬性的名稱。  
  
 [in] `lf`  
 指定的屬性之字型的邏輯字型結構。  
  
 [in] `dwFontDialogFlags`  
 適用於當您按一下屬性值的下拉式按鈕會顯示 [字型] 對話方塊的樣式。 預設值是 CF_EFFECTS 和 CF_SCREENFONTS 合 (OR)。 如需詳細資訊，請參閱`Flags`參數[CHOOSEFONT 結構](http://msdn.microsoft.com/library/windows/desktop/ms646832)。  
  
 [in] `lpszDescr`  
 字型屬性的描述。 預設值是 `NULL`。  
  
 [in] `dwData`  
 應用程式特定資料，例如整數或其他與屬性相關聯的資料指標。 預設值為 0。  
  
 [in] `color`  
 字型的色彩。 預設值為預設色彩。  
  
### <a name="remarks"></a>備註  
 A`CMFCPropertyGridFontProperty`物件都代表在屬性方格字型控制項的字型屬性。  
  
### <a name="example"></a>範例  
 下列範例將示範如何建構的物件`CMFCPropertyGridFontProperty`類別。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&26;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]  
  
##  <a name="a-namegetcolora--cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridFontProperty::GetColor  
 擷取使用者從字型 對話方塊中選取的字型色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值，表示選取的字型色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetlogfonta--cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont  
 擷取使用者從字型 對話方塊中選取的字型。  
  
```  
LPLOGFONT GetLogFont();
```  
  
### <a name="return-value"></a>傳回值  
 指標[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)該結構描述選取的字型。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)

