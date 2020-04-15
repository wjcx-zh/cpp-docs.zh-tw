---
title: CMFC 功能標籤類
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: cd30e374441661368d3ea7abf5177424f8dffb3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375129"
---
# <a name="cmfcribbonlabel-class"></a>CMFC 功能標籤類

實作功能區的不可點選式文字標籤。

## <a name="syntax"></a>語法

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC帶標籤::CMFC帶標籤](#cmfcribbonlabel)|使用指定的文字字串建構和初始`CMFCRibbonLabel`化物件。|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonLabel::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC 功能標籤::設定ACC數據](#setaccdata)|確定當前功能區標籤元素的輔助功能數據。 ( 覆寫[CMFC 功能按鈕:設定ACC資料](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>備註

建立功能區標籤後,請調用[CMFC 功能面板:::添加](../../mfc/reference/cmfcribbonpanel-class.md#add),將其添加到面板中。

不能向「快速存取」工具列添加功能區標籤。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonLabel.h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFC帶標籤::CMFC帶標籤

建構並初始化顯示指定文本字串的[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)物件。

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[在]要顯示在標籤中的文本。

*bIs 多行*<br/>
[在]TRUE 指定標籤是多行標籤;否則,FALSE。

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFC 功能標籤::設定ACC數據

確定當前功能區標籤元素的輔助功能數據。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
[在]表示當前功能區標籤的父視窗。

*資料*<br/>
[出]使用當前功能區`CAccessibilityData`標籤的輔助功能數據的填充的類型物件。

### <a name="return-value"></a>傳回值

如果*資料*參數已成功填充當前功能區標籤的輔助功能數據,則為 TRUE;否則,FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
