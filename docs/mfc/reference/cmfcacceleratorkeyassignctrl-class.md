---
title: CMFCAcceleratorKeyAssignCtrl 類別
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: 5e57bf149fdbc293692c613afcabcf2d11d32221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505464"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 類別

類別會擴充[CEdit 類別](../../mfc/reference/cedit-class.md)，以支援額外的系統按鈕，例如 ALT、CONTROL 和 SHIFT。 `CMFCAcceleratorKeyAssignCtrl`

## <a name="syntax"></a>語法

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|建構 `CMFCAcceleratorKeyAssignCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|針對在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下的快速鍵，擷取 `ACCEL` 結構。|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|判斷是否已定義快速鍵。|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式之前的視窗訊息。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|重設快速鍵。|

## <a name="remarks"></a>備註

此類別可藉由支援快速鍵來擴充 `CEdit` 類別的功能。 類別會當做[CEdit 類別](../../mfc/reference/cedit-class.md)來運作，而且也可以辨識系統按鈕。 `CMFCAcceleratorKeyAssignCtrl`

這個類別會將實體快速鍵組合對應至字串值。 例如，假設按鍵組合 ALT + B 會對應至字串 "Alt + B"。 當使用者在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下此按鍵組合時，會對使用者顯示 "Alt + B"。 如需快速鍵和字串格式之間對應的詳細資訊，請參閱[CMFCAcceleratorKey 類別](../../mfc/reference/cmfcacceleratorkey-class.md)。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCAcceleratorKeyAssignCtrl` 物件，並使用其 `ResetKey` 方法來重設快速鍵。

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>需求

**標頭：** afxacceleratorkeyassignctrl。h

##  <a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl：： CMFCAcceleratorKeyAssignCtrl

結構[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl：： GetAccel

抓取 [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) `ACCEL`物件中所按下快速鍵的結構。

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>傳回值

描述快速鍵的結構。 `ACCEL`

### <a name="remarks"></a>備註

使用此函式來`ACCEL`抓取使用者在`CMFCAcceleratorKeyAssignCtrl`物件中輸入之快速鍵的結構。

##  <a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl：： IsFocused

如需詳細資訊，請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl：： IsKeyDefined

判斷快速鍵是否已定義于[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件中。

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>傳回值

如果使用者已按下定義快速鍵的有效索引鍵組合，則為非零值;否則為0。

### <a name="remarks"></a>備註

使用此函式來判斷使用者是否在您`CMFCAcceleratorKeyAssignCtrl`的物件中輸入有效的快速鍵。 如果快捷方式索引鍵存在，您可以使用[CMFCAcceleratorKeyAssignCtrl：： GetAccel](#getaccel)方法來取得`ACCEL`與這個快速鍵相關聯的結構。

##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

如需詳細資訊，請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

在*pMsg*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl：： ResetKey

重設快速鍵。

```
void ResetKey();
```

### <a name="remarks"></a>備註

函式會清除編輯控制項的文字。 這包括使用者按下的任何快速鍵。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey 類別](../../mfc/reference/cmfcacceleratorkey-class.md)
