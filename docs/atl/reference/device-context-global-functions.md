---
title: 裝置內容全域函式
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: aeebec65def9364e56156f6bb323815da012e11f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276558"
---
# <a name="device-context-global-functions"></a>裝置內容全域函式

此函式會建立指定的裝置的裝置內容。

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|建立裝置內容。|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

建立裝置內容中指定的裝置[DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice)結構。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>參數

*hdc*<br/>
[in]現有的控制代碼的裝置內容，則為 NULL。

*ptd*<br/>
[in]指標`DVTARGETDEVICE`結構，其中包含目標裝置的相關資訊。

### <a name="return-value"></a>傳回值

中指定的裝置的裝置內容中傳回的控制代碼`DVTARGETDEVICE`。 如果未不指定任何裝置，則傳回預設顯示裝置的控制代碼。

### <a name="remarks"></a>備註

如果結構為 NULL 並*hdc*為 NULL，會建立預設顯示裝置的裝置內容。

如果*hdc*不是 NULL 並*ptd*是 NULL，則函數會傳回現有*hdc*。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
