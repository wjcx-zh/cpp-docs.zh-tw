---
title: 裝置內容全域函式
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d225bd0cd996fd908479b5a93aad81ea0428900b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496093"
---
# <a name="device-context-global-functions"></a>裝置內容全域函式

此函式會為指定的裝置建立裝置內容。

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|建立裝置內容。|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

建立[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)結構中所指定裝置的裝置內容。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>參數

*hdc*<br/>
在裝置內容的現有控制碼, 或 Null。

*ptd*<br/>
在`DVTARGETDEVICE`結構的指標, 其中包含目標裝置的相關資訊。

### <a name="return-value"></a>傳回值

傳回中`DVTARGETDEVICE`所指定裝置的裝置內容控制碼。 如果未指定任何裝置, 則會傳回預設顯示裝置的控制碼。

### <a name="remarks"></a>備註

如果結構是 Null, 而*hdc*是 null, 則會建立預設顯示裝置的裝置內容。

如果*hdc*不是 null, 而且*ptd*是 null, 則函數會傳回現有的*hdc*。

## <a name="requirements"></a>需求

**標頭:** atlwin.h。h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
