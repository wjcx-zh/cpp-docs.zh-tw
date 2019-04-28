---
title: 'Platform:: recreateexception 方法'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 9e167efc54352d125e849956a2da8d8e8cad4ed6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330319"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException 方法

這個方法僅供內部使用，使用者程式碼並不需要。 請改用 exception:: createexception 方法。

## <a name="syntax"></a>語法

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>參數

*hr*

### <a name="property-valuereturn-value"></a>屬性值/傳回值

根據指定的 HRESULT 傳回新的 Platform::Exception^。
