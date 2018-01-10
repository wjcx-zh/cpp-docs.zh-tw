---
title: "CMFCPropertyGridColorProperty 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
dev_langs: C++
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33c807343c29fca74168167ef5d784e056b350fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty 類別
`CMFCPropertyGridColorProperty` 類別支援開啟色彩選取對話方塊的屬性清單控制項項目。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|建構 `CMFCPropertyGridColorProperty` 物件。|  
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|可讓*自動*色彩選取對話方塊上的按鈕。 (標準自動按鈕的標籤為**自動**。)|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|可讓*其他*色彩選取對話方塊上的按鈕。 (標準其他按鈕的標籤為**更多色彩**。)|  
|`CMFCPropertyGridColorProperty::FormatProperty`|格式化屬性值的文字表示法。 (覆寫[cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|  
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|取得屬性的目前色彩。|  
|`CMFCPropertyGridColorProperty::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|`CMFCPropertyGridColorProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。 (覆寫[cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|由架構呼叫以顯示屬性值。 (覆寫[cmfcpropertygridproperty:: Ondrawvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue)。)|  
|`CMFCPropertyGridColorProperty::OnEdit`|使用者即將修改屬性值時由架構呼叫。 (覆寫[cmfcpropertygridproperty:: Onedit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit)。)|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|當可編輯屬性的值變更時由架構呼叫。 (覆寫[cmfcpropertygridproperty:: Onupdatevalue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue)。)|  
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|設定屬性的新色彩。|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|指定目前色彩屬性格線中的資料行數目。|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|設定可編輯屬性的原始值。|  
  
## <a name="remarks"></a>備註  
 `CMFCPropertyGridColorProperty` 類別支援的色彩屬性可以加入至屬性清單控制項。 如需詳細資訊，請參閱[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構 `CMFCPropertyGridColorProperty` 類別的物件，以及使用 `CMFCPropertyGridColorProperty` 類別的各種方法來設定此物件。 程式碼說明如何啟用自動和其他按鈕，以及如何設定色彩和資料行數目。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridcolorproperty"></a>CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty  
 建構 `CMFCPropertyGridColorProperty` 物件。  
  
```  
CMFCPropertyGridColorProperty(
    const CString& strName,  
    const COLORREF& color,  
    CPalette* pPalette = NULL,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `strName`  
 屬性的名稱。  
  
 [輸入] `color`  
 色彩屬性的值。  
  
 [輸入] `pPalette`  
 指標的色彩調色盤。 預設值是 `NULL`。  
  
 [輸入] `lpszDescr`  
 屬性描述。 預設值是 `NULL`。  
  
 [輸入] `dwData`  
 應用程式特定資料，例如整數或其他與屬性相關聯的資料指標。 預設值為 0。  
  
##  <a name="enableautomaticbutton"></a>CMFCPropertyGridColorProperty::EnableAutomaticButton  
 可讓*自動*色彩選取對話方塊上的按鈕。 (標準自動按鈕的標籤為**自動**。)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszLabel`  
 自動按鈕的標籤文字。  
  
 [輸入] `colorAutomatic`  
 自動 （預設） 色彩的 RGB 色彩值。  
  
 [輸入] `bEnable`  
 `TRUE`若要啟用 [自動] 按鈕。否則， `FALSE`。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enableotherbutton"></a>CMFCPropertyGridColorProperty::EnableOtherButton  
 可讓*其他*色彩選取對話方塊上的按鈕。 (標準其他按鈕的標籤為**更多色彩**。)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg = TRUE,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszLabel`  
 其他按鈕的標籤文字。  
  
 [輸入] `bAltColorDlg`  
 `TRUE`若要顯示`CMFCColorDialog` 對話方塊。`FALSE`顯示標準色彩選取對話方塊。 預設值是 `TRUE`。  
  
 [輸入] `bEnable`  
 `TRUE`若要顯示 [其他] 按鈕。否則， `FALSE`。  預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcolor"></a>CMFCPropertyGridColorProperty::GetColor  
 取得屬性的目前色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setcolor"></a>CMFCPropertyGridColorProperty::SetColor  
 設定屬性的新色彩。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `color`  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setcolumnsnumber"></a>CMFCPropertyGridColorProperty::SetColumnsNumber  
 指定目前色彩屬性格線中的資料行數目。  
  
```  
void SetColumnsNumber(int nColumnsNumber);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nColumnsNumber`  
 色彩屬性格線中的資料行的慣用的數目。  
  
### <a name="remarks"></a>備註  
 這個方法會設定的值`m_nColumnsNumber`受保護的資料成員。  
  
##  <a name="setoriginalvalue"></a>CMFCPropertyGridColorProperty::SetOriginalValue  
 設定可編輯屬性的原始值。  
  
```  
virtual void SetOriginalValue(const COleVariant& varValue);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `varValue`  
 一個值。  
  
### <a name="remarks"></a>備註  
 使用[cmfcpropertygridproperty:: Resetoriginalvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue)方法來重設已編輯的屬性的原始值。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)
