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
ms.openlocfilehash: 2021a2069885c6314859a65d528cf03712c524b6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751743"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 類別

該`CMFCAcceleratorKeyAssignCtrl`類擴展[了 CEdit 類](../../mfc/reference/cedit-class.md),以支援額外的系統按鈕,如 ALT、CONTROL 和 SHIFT。

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

此類別可藉由支援快速鍵來擴充 `CEdit` 類別的功能。 該`CMFCAcceleratorKeyAssignCtrl`類作為[CEdit 類](../../mfc/reference/cedit-class.md)運行,還可以識別系統按鈕。

這個類別會將實體快速鍵組合對應至字串值。 例如，假設按鍵組合 ALT + B 會對應至字串 "Alt + B"。 當使用者在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下此按鍵組合時，會對使用者顯示 "Alt + B"。 有關快速鍵和字串格式之間的映射的詳細資訊,請參閱[CMFC 加速器金鑰類別](../../mfc/reference/cmfcacceleratorkey-class.md)。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCAcceleratorKeyAssignCtrl` 物件，並使用其 `ResetKey` 方法來重設快速鍵。

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>需求

**標題:** afx加速器鍵分配.h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFC加速器金鑰分配Ctrl::CMFC加速器鍵分配Ctrl

建構[CMFC 加速器KeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFC加速器鍵分配Ctrl::GetAccel

檢索在`ACCEL`[CMFC 加速器KeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件中按下的快速鍵的結構。

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>傳回值

描述`ACCEL`快捷鍵的結構。

### <a name="remarks"></a>備註

使用此函數可以檢索使用者輸入`ACCEL``CMFCAcceleratorKeyAssignCtrl`到 物件的快捷鍵的結構。

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFC加速器金鑰分配Ctrl::聚焦

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFC加速器金鑰配置Ctrl::IsKey定義

確定是否已在[CMFC 加速器KeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件中定義快速鍵。

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>傳回值

如果使用者已按下定義快速鍵的有效鍵組合,則非零;否則 0。

### <a name="remarks"></a>備註

使用此函數可確定使用者是否在對`CMFCAcceleratorKeyAssignCtrl`象 中輸入了有效的快速鍵。 如果存在快速鍵,則可以使用[CMFCFc 加速器KeyAssignCtrl:getAccel](#getaccel)方法獲取與`ACCEL`此快捷鍵 關聯的結構。

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFC加速器鍵分配Ctrl::P重新翻譯消息

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

[在]*pMsg*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFC加速器金鑰分配Ctrl::重置鍵

重設快速鍵。

```cpp
void ResetKey();
```

### <a name="remarks"></a>備註

該函數清除編輯控制文本。 這包括使用者按下的任何快速鍵。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey 類別](../../mfc/reference/cmfcacceleratorkey-class.md)
