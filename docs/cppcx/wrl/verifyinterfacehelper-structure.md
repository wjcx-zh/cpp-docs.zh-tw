---
title: VerifyInterfaceHelper 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: 09c2cc7e08e2dc0e8df42c64d285c37627c5925a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374239"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper 結構

支援 Windows 運行時 C++範本庫基礎結構,並且不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>參數

*I.*<br/>
要驗證的介面。

*是 WinRT 介面*

## <a name="remarks"></a>備註

驗證範本參數指定的介面是否滿足某些要求。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                                            | 描述
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify 方法](#verify) | 驗證當前範本參數指定的介面是否滿足某些要求。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VerifyInterfaceHelper`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a>驗證介面說明程式::驗證

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>備註

驗證當前範本參數指定的介面是否滿足某些要求。
