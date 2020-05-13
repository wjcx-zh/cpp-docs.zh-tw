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
ms.openlocfilehash: 5b18a15f8bfd98396acae0558d121b32bc4127c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367631"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 類別

允許將按鈕添加到桌面警報對話方塊中。

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
|[CMFC 桌面警示按鈕::是標題按鈕](#iscaptionbutton)|確定該按鈕是否顯示在警報對話框的標題區域中。|
|[CMFC 桌面警示按鈕::正在關閉按鈕](#isclosebutton)|確定按鈕是否關閉警報對話方塊。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|指定按鈕是否顯示在警報對話框的標題區域中的布林值。|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|指定按鈕是否關閉警報對話框的布爾值。|

### <a name="remarks"></a>備註

默認情況下,建構函數將`m_bIsCaptionButton`和`m_bIsCloseButton`數據成員設置為 FALSE。 如果按鈕`CMFCDesktopAlertDialog`位於警`m_bIsCaptionButton`報 對話框的標題區域中,則父物件將設置為 TRUE。 類`CMFCDesktopAlertDialog`創建一`CMFCDesktopAlertWndButton`個 物件,該物件用作關閉警報對話方`m_bIsCloseButton`塊並設置 為 TRUE 的按鈕。

將`CMFCDesktopAlertWndButton`物件添加到`CMFCDesktopAlertDialog`物件 ,就像添加任何按鈕一樣。 有關 的詳細`CMFCDesktopAlertDialog`資訊 ,請參閱[CMFC 桌面警示對話類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。

## <a name="example"></a>範例

下面的示例演示如何在`SetImage``CMFCDesktopAlertWndButton`類中使用 方法。 此代碼段是[桌面警報演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFC 桌面警示按鈕](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxdesktopalertwnd.h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a>CMFC 桌面警示按鈕::是標題按鈕

確定該按鈕是否顯示在警報對話框的標題區域中。

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕顯示在警報對話框的標題區域中,則非零;否則,0。

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a>CMFC 桌面警示按鈕::正在關閉按鈕

確定按鈕是否關閉警報對話方塊。

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕關閉警報對話框,則非零;否則,0。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)
