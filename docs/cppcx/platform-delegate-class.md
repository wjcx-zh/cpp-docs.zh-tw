---
title: Platform::Delegate 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 4116de3240c3ef334db51095997f946731372708
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769234"
---
# <a name="platformdelegate-class"></a>Platform::Delegate 類別

表示函式物件。

## <a name="syntax"></a>語法

```cpp
public delegate void delegate_name();
```

### <a name="members"></a>成員

委派類別具有衍生自 [Platform::Object Class](../cppcx/platform-object-class.md)的 Equals()、GetHashCode() 和 ToString() 方法。

### <a name="remarks"></a>備註

使用 [委派](../extensions/delegate-cpp-component-extensions.md) 關鍵字建立委派，請勿明確使用 Platform::Delegate。 如需詳細資訊，請參閱[委派](../cppcx/delegates-c-cx.md)。 如需如何建立和使用委派的範例，請參閱 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="see-also"></a>另請參閱

[Platform 命名空間](../cppcx/platform-namespace-c-cx.md)
