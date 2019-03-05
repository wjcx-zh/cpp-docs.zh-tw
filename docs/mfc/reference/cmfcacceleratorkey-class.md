---
title: CMFCAcceleratorKey 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: 6a99ad00a43ac7912320ee469d542b6bf9cca3de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292259"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey 類別

實作虛擬按鍵對應和格式化的協助程式類別。

## <a name="syntax"></a>語法

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|建構 `CMFCAcceleratorKey` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|將轉譯成它的視覺表示的加速度結構。|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|設定快速鍵`CMFCAcceleratorKey`物件。|

## <a name="remarks"></a>備註

快速鍵是也稱為快速鍵。 如果您想要顯示使用者輸入的鍵盤快速鍵[CMFCAcceleratorKeyAssignCtrl 類別](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)對應鍵盤快速鍵，例如 Alt + Shift + S，自訂文字格式，例如"Alt + Shift + S"。 每個`CMFCAcceleratorKey`物件對應至以文字格式的單一的快速鍵。

如需如何使用快速鍵和快速鍵對應表的詳細資訊，請參閱[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)。

## <a name="example"></a>範例

下列範例示範如何建構`CMFCAcceleratorKey`物件，以及如何使用其`Format`方法。

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>需求

**標頭：** afxacceleratorkey.h

##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey

建構[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)物件。

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>參數

*lpAccel*<br/>
[in]攠摝坫指標。

### <a name="remarks"></a>備註

當您建立時如果您未提供攠摝坫`CMFCAccleratorKey`，使用[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)方法，以建立關聯的快速鍵，與您`CMFCAcceleratorKey`物件。

##  <a name="format"></a>  CMFCAcceleratorKey::Format

將轉譯的加速度結構，其相關聯的字串值。

```
void Format(CString& str) const;
```

### <a name="parameters"></a>參數

*str*<br/>
[out]參考`CString`物件，方法會將寫入的已翻譯的快速鍵。

### <a name="remarks"></a>備註

這個方法會擷取字串的格式相關聯的快速鍵。 您可以設定的字串格式[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)物件使用建構函式或方法[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)。

##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator

設定快速鍵[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)物件。

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>參數

*lpAccel*<br/>
[in]攠摝坫指標。

### <a name="remarks"></a>備註

使用此方法來設定的快速鍵`CMFCAcceleratorKey`如果您未提供攠摝坫您在建立時`CMFCAcceleratorKey`。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)
