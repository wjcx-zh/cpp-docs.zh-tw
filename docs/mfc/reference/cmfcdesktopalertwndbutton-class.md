---
title: CMFCDesktopAlertWndButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 6d296966001dcbc2279a298bdd1d9c21195d61fd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840775"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 類別

允許將按鈕新增至桌面警示對話方塊。

## <a name="syntax"></a>語法

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|預設建構函式。|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CMFCDesktopAlertWndButton：： IsCaptionButton](#iscaptionbutton)|決定按鈕是否顯示在警示對話方塊的標題區域中。|
|[CMFCDesktopAlertWndButton：： IsCloseButton](#isclosebutton)|判斷按鈕是否會關閉警示對話方塊。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|-|-|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|布林值，指定按鈕是否顯示在警示對話方塊的標題區域中。|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|指定按鈕是否會關閉警示對話方塊的布林值。|

### <a name="remarks"></a>備註

根據預設，此函式會將 `m_bIsCaptionButton` 和 `m_bIsCloseButton` 資料成員設為 FALSE。 `CMFCDesktopAlertDialog` `m_bIsCaptionButton` 如果按鈕位於警示對話方塊的標題區域中，父物件就會設定為 TRUE。 `CMFCDesktopAlertDialog`類別會建立一個 `CMFCDesktopAlertWndButton` 物件，做為關閉警示對話方塊並設 `m_bIsCloseButton` 為 TRUE 的按鈕。

將 `CMFCDesktopAlertWndButton` 物件新增至 `CMFCDesktopAlertDialog` 物件，就像新增任何按鈕一樣。 如需的詳細資訊 `CMFCDesktopAlertDialog` ，請參閱 [CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。

## <a name="example"></a>範例

下列範例示範如何使用 `SetImage` 類別中的方法 `CMFCDesktopAlertWndButton` 。 此程式碼片段是 [桌面警示示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxdesktopalertwnd。h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a> CMFCDesktopAlertWndButton：： IsCaptionButton

決定按鈕是否顯示在警示對話方塊的標題區域中。

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕顯示在警示對話方塊的標題區域中，則為非零。否則為0。

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a> CMFCDesktopAlertWndButton：： IsCloseButton

判斷按鈕是否會關閉警示對話方塊。

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕關閉警示對話方塊，則為非零。否則為0。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)
