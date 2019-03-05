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
ms.openlocfilehash: 2a9ade332c87f293719872e426fb459b011d2d35
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270252"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 類別

允許加入桌面警示對話方塊的按鈕。

## <a name="syntax"></a>語法

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|預設建構函式。|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|決定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|決定是否 按鈕會關閉警示 對話方塊。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|布林值，指定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|布林值，指定是否 按鈕會關閉警示 對話方塊。|

### <a name="remarks"></a>備註

根據預設，設定建構函式`m_bIsCaptionButton`和`m_bIsCloseButton`資料成員設為 FALSE。 父代`CMFCDesktopAlertDialog`物件集`m_bIsCaptionButton`為 TRUE，如果按鈕位於 [警示] 對話方塊的標題區域中。 `CMFCDesktopAlertDialog`類別會建立`CMFCDesktopAlertWndButton`物件，可做為關閉警示 對話方塊的按鈕方塊，並設定`m_bIsCloseButton`設為 TRUE。

新增`CMFCDesktopAlertWndButton`物件至`CMFCDesktopAlertDialog`物件與加入的任何按鈕。 如需詳細資訊`CMFCDesktopAlertDialog`，請參閱 < [CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。

## <a name="example"></a>範例

下列範例示範如何使用`SetImage`方法中的`CMFCDesktopAlertWndButton`類別。 此程式碼片段是一部分[桌面警示示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdesktopalertwnd.h

##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton

決定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕顯示在 [警示] 對話方塊中，[標題] 區域中，非零值。否則就是 0。

##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton

決定是否 按鈕會關閉警示 對話方塊。

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕會關閉警示 對話方塊中，為非零否則就是 0。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)
