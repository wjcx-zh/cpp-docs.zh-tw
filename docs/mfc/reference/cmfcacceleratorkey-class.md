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
ms.openlocfilehash: 7d66e7043325bbbd324f3ac443368787a653ebe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369932"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey 類別

實現虛擬金鑰映射和格式化的幫助程式類。

## <a name="syntax"></a>語法

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC加速器鍵:CMFC加速器鍵](#cmfcacceleratorkey)|建構 `CMFCAcceleratorKey` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 加速器鍵:格式](#format)|將 ACCEL 結構轉換為其可視表示形式。|
|[CMFC加速器鍵::設定加速器](#setaccelerator)|設置`CMFCAcceleratorKey`物件的快速鍵。|

## <a name="remarks"></a>備註

快速鍵也稱為快捷鍵。 如果要顯示使用者輸入的鍵盤快速鍵[,CMFC加速器KeyAssignCtrl 類](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)會將鍵盤快捷鍵(如 Alt_Shift_S)映射到自定義文本格式,如"Alt + Shift + S"。 每個`CMFCAcceleratorKey`物件將單個快速鍵映射到文字格式。

有關如何使用快捷鍵和快捷鍵表的詳細資訊,請參閱[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCAcceleratorKey`物件以及如何使用`Format`其方法。

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>需求

**標題:** afx加速器鍵.h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFC加速器鍵:CMFC加速器鍵

建構[CMFC 加速器鍵](../../mfc/reference/cmfcacceleratorkey-class.md)物件。

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>參數

*lpAccel*<br/>
[在]指向快速鍵的指標。

### <a name="remarks"></a>備註

如果在創建 時未提供快速`CMFCAccleratorKey`鍵 ,請使用[CMFCAcceleratorKey::setAccelerator](#setaccelerator)方法`CMFCAcceleratorKey`將快速鍵與 對象相關聯。

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a>CMFC 加速器鍵:格式

將 ACCEL 結構轉換為其關聯的字串值。

```
void Format(CString& str) const;
```

### <a name="parameters"></a>參數

*Str*<br/>
[出]對物件引用`CString`,該方法在其中寫入已翻譯的快捷鍵。

### <a name="remarks"></a>備註

此方法檢索關聯的快捷鍵的字串格式。 您可以使用建構函數或方法[CMFC 加速器鍵:::setaccelerator](#setaccelerator)設置,設定[CMFC加速器Key](../../mfc/reference/cmfcacceleratorkey-class.md)物件的字串格式。

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFC加速器鍵::設定加速器

設置[CMFC 加速器鍵](../../mfc/reference/cmfcacceleratorkey-class.md)物件的快速鍵。

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>參數

*lpAccel*<br/>
[在]指向快速鍵的指標。

### <a name="remarks"></a>備註

`CMFCAcceleratorKey`如果在創建 時未提供快捷鍵,請使用 此方法為`CMFCAcceleratorKey`設置的快速鍵。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)
