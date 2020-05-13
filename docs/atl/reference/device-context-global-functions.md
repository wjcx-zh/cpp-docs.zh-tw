---
title: 裝置內容文全域函數
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: e640f310a1976c29a39f0ab7c2575dfd1073c889
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330146"
---
# <a name="device-context-global-functions"></a>裝置內容文全域函數

此功能為給定設備創建設備上下文。

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|創建設備上下文。|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a>AtlCreate目標DC

為[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)結構中指定的設備創建設備上下文。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>參數

*hdc*<br/>
[在]設備上下文的現有句柄,或 NULL。

*ptd*<br/>
[在]指向包含有關目標設備`DVTARGETDEVICE`的資訊的指標。

### <a name="return-value"></a>傳回值

將句柄傳回到 中指定的裝置的裝置`DVTARGETDEVICE`上下文 。 如果未指定設備,則將句柄返回到默認顯示設備。

### <a name="remarks"></a>備註

如果結構為*NULL,hdc*為 NULL,則為預設顯示設備創建設備上下文。

如果*hdc*不是 NULL,並且*ptd*為 NULL,則函數將傳回現有的*hdc*。

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
