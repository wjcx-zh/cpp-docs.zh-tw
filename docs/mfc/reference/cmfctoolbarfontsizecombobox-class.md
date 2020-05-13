---
title: CMFCToolBarFontSizeComboBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: 6c90bb1ce464a90295e7edb933d87594444c3648
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745315"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 類別

包含組合框控制項的工具列按鈕,使用戶能夠選擇字體大小。

## <a name="syntax"></a>語法

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontSsCombox:CMFCToolBarFontSscombox](#cmfctoolbarfontsizecombobox)|建構 `CMFCToolBarFontSizeComboBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontSsSsBox::取得Twipsize](#gettwipsize)|以 twips 返回所選字體大小。|
|[CMFCToolBarFontSsBox::重建字型](#rebuildfontsizes)|使用指定字型的所有支援字型大小填充組合框清單。|
|[CMFCToolBarFontSsSsBox::SetTwipSize](#settwipsize)|以 twips 設置字體大小。|

## <a name="remarks"></a>備註

您可以將`CMFCToolBarFontSizeComboBox`物件與[CMFCToolBarFontComboBox 類](../../mfc/reference/cmfctoolbarfontcombobox-class.md)物件一起使用,以使用戶能夠選擇字體和字型大小。

您可以添加字型大小組合框按鈕到工具列,就像添加字體組合框按鈕一樣。 有關詳細資訊,請參閱[CMFCToolBarFontCombox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。

當使用者在`CMFCToolBarFontComboBox`物件中選擇新字體時,可以使用[CMFCToolBoxSizeComboBox::「重建字體」](#rebuildfontsizes)方法,使用該字體支援的大小填充字體大小組合框。

## <a name="example"></a>範例

下面的範例展示如何在`CMFCToolBarFontSizeComboBox`類中使用各種方法來配置`CMFCToolBarFontSizeComboBox`物件。 該示例演示如何從文字框中檢索字體大小(以 twips 形式),使用給定字體的所有有效大小填充字體大小組合框,並在 twips 中指定字型大小。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComBox按鈕](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSsComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>需求

**標題:** afxtoolbarfontcombox.h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSsCombox:CMFCToolBarFontSscombox

建構 `CMFCToolBarFontSizeComboBox` 物件。

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSsSsBox::取得Twipsize

從字體大小組合框的文字框中檢索字體大小(以 twips 形式顯示)。

```
int GetTwipSize() const;
```

### <a name="return-value"></a>傳回值

如果返回值為正,則為 twips 中的字體大小。 如果組合框的文字框為空,則為 -1。 如果發生錯誤,為 -2。

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSsBox::重建字型

使用給定字體的所有有效大小填充字體大小組合框。

```cpp
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>參數

*放大縮小字型功能 放大縮小字型功能*<br/>
[在]指定字型名稱。

### <a name="remarks"></a>備註

如果要在字體組合框中的選擇與字體大小組合框(如[CMFCToolBarFontCombox 類](../../mfc/reference/cmfctoolbarfontcombobox-class.md))之間進行同步,請調用此功能。

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSsSsBox::SetTwipSize

將指定大小(以 twips 為單位)捨入到最近的大小(以磅為單位),然後將組合框中的選定大小設置為該值。

```cpp
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
[在]指定要設置的字體大小(以 twips 表示)。

### <a name="remarks"></a>備註

稍後,您可以通過調用[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)方法來檢索以前的有效字體大小。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFC工具列:更換按鈕](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
