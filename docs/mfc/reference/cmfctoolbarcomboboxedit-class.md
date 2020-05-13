---
title: CMFCToolBarComboBoxEdit 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
ms.openlocfilehash: dfbf24f5833d143adc6d21b6cb54dd9ac81c2f0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372195"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit 類別

框架使用`CMFCToolBarComboBoxEdit`類 創建一個工具列按鈕,該按鈕的功能類似於可編輯組合框控制項。

## <a name="syntax"></a>語法

```
class CMFCToolBarComboBoxEdit : public CEdit
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarCombox編輯:CMFCToolBarCombox編輯](#cmfctoolbarcomboboxedit)|建構 `CMFCToolBarComboBoxEdit` 物件。|
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|

### <a name="remarks"></a>備註

從`CMFCToolBarComboBoxEdit`類派生類以自定義其編輯操作。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="requirements"></a>需求

**標題:** afxtoolbarcombox 按鈕.h

## <a name="cmfctoolbarcomboboxeditcmfctoolbarcomboboxedit"></a><a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarCombox編輯:CMFCToolBarCombox編輯

建構 `CMFCToolBarComboBoxEdit` 物件。

```
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```

### <a name="parameters"></a>參數

*組合圖*<br/>
[在]對[CMFCToolBarComBoBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件的引用,該物件是包含組合框控制項的工具列按鈕。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCToolBarComboBoxEdit`類的物件。 此代碼段是[IE 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
