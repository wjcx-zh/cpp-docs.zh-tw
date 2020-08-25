---
title: 裝置內容全域函式
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d2d25660083f074683a3f42f878497ce14a008b8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833461"
---
# <a name="device-context-global-functions"></a>裝置內容全域函式

此函式會建立指定裝置的裝置內容。

|名稱|描述|
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|建立裝置內容。|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a> AtlCreateTargetDC

針對 [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) 結構中指定的裝置建立裝置內容。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>參數

*hdc*<br/>
在裝置內容的現有控制碼，或 Null。

*ptd*<br/>
在結構的指標 `DVTARGETDEVICE` ，其中包含目標裝置的相關資訊。

### <a name="return-value"></a>傳回值

傳回中所指定裝置的裝置內容控制碼 `DVTARGETDEVICE` 。 如果未指定任何裝置，則會將控制碼傳回到預設顯示裝置。

### <a name="remarks"></a>備註

如果結構是 Null，而 *hdc* 為 null，則會建立預設顯示裝置的裝置內容。

如果 *hdc* 不是 null，且 *ptd* 為 Null，則函數會傳回現有的 *hdc*。

## <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)
