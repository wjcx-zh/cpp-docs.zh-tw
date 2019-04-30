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
ms.openlocfilehash: c6ce8c75b1b764d1d2b66b86147035f069805d25
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403903"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 類別

`CMFCAcceleratorKeyAssignCtrl`類別會擴充[CEdit 類別](../../mfc/reference/cedit-class.md)以支援額外的系統按鈕，例如 ALT、 CONTROL 和 SHIFT。

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
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式之前的視窗訊息。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|重設快速鍵。|

## <a name="remarks"></a>備註

此類別可藉由支援快速鍵來擴充 `CEdit` 類別的功能。 `CMFCAcceleratorKeyAssignCtrl`類別可當作[CEdit 類別](../../mfc/reference/cedit-class.md)和也可以辨認系統按鈕。

這個類別會將實體快速鍵組合對應至字串值。 例如，假設按鍵組合 ALT + B 會對應至字串 "Alt + B"。 當使用者在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下此按鍵組合時，會對使用者顯示 "Alt + B"。 如需快捷鍵和字串格式之間的對應的詳細資訊，請參閱[CMFCAcceleratorKey 類別](../../mfc/reference/cmfcacceleratorkey-class.md)。

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

**標頭：** afxacceleratorkeyassignctrl.h

##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

建構[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel

擷取`ACCEL`結構中按下的快速鍵[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>傳回值

`ACCEL`該結構描述的快速鍵。

### <a name="remarks"></a>備註

使用此函式來擷取`ACCEL`結構，使用者輸入攠摝坫您`CMFCAcceleratorKeyAssignCtrl`物件。

##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

判斷是否已在定義攠摝坫[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>傳回值

如果使用者已按下定義的快速鍵; 的索引鍵的有效組合，非零值。否則為 0。

### <a name="remarks"></a>備註

使用此函式來判斷使用者是否輸入有效快速鍵，在您`CMFCAcceleratorKeyAssignCtrl`物件。 如果攠摝坫存在，您可以使用[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)方法，以取得`ACCEL`這個快顯索引鍵相關聯的結構。

##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

[in] *pMsg*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey

重設快速鍵。

```
void ResetKey();
```

### <a name="remarks"></a>備註

此函式會清除編輯控制項文字。 這包括任何使用者按下的快速鍵。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey 類別](../../mfc/reference/cmfcacceleratorkey-class.md)
