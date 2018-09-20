---
title: CMFCToolBarFontSizeComboBox 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9942f0d9ca4f890965aaf7d05383beae6fa24af9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429444"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 類別

包含下拉式方塊控制項，可讓使用者選取字型大小的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|建構 `CMFCToolBarFontSizeComboBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|傳回所選的字型大小，以 twip 為單位。|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|填入所有支援的字型大小指定字型下拉式方塊的清單。|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|設定字型大小以 twip 為單位。|

## <a name="remarks"></a>備註

您可以使用`CMFCToolBarFontSizeComboBox`物件搭配[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)物件，讓使用者選取的字型和字型大小。

就像您加入字型下拉式方塊按鈕，您可以加入工具列的字型下拉式方塊按鈕。 如需詳細資訊，請參閱 < [CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。

當使用者選取中的新字型`CMFCToolBarFontComboBox`物件，您也可以使用該字型支援的大小與填入字型的大小下拉式方塊[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)方法。

## <a name="example"></a>範例

下列範例示範如何使用中的各種方法`CMFCToolBarFontSizeComboBox`類別，以設定`CMFCToolBarFontSizeComboBox`物件。 此範例說明如何擷取的字型大小，以 twip 為單位，從文字方塊中填入所有的有效大小的指定之字型的字型的大小下拉式方塊，以 twip 為單位指定的字型大小。 此程式碼片段是 [WordPad 範例](../../visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>需求

**標頭：** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

建構 `CMFCToolBarFontSizeComboBox` 物件。

```
CMFCToolBarFontSizeComboBox();
```

##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize

擷取的字型大小，以 twip 為單位，從字型大小下拉式方塊的文字方塊。

```
int GetTwipSize() const;
```

### <a name="return-value"></a>傳回值

如果傳回的值是正數，它是以 twip 為單位的字型大小。 如果是空的下拉式方塊的文字方塊中，它會為-1。 如果發生錯誤，它就會是-2。

##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes

填入所有的有效大小，指定字型的字型大小下拉式方塊。

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>參數

*strFontName*<br/>
[in]指定的字型名稱。

### <a name="remarks"></a>備註

呼叫此函式，當您想要一個字型下拉式方塊中的選取項目和字型的大小下拉式方塊中，同步處理這類[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。

##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize

指定的四捨五入的大小 （以 twip 為單位） 的最接近的大小，以點，然後集設為該值下拉式方塊中選取的大小。

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
[in]若要設定中指定的字型大小 （以 twip 為單位）。

### <a name="remarks"></a>備註

您可以稍後擷取的前一個有效的字型大小，藉由呼叫[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)方法。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



