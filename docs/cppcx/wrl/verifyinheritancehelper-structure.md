---
title: VerifyInheritanceHelper 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: 3650cfb70ffc12572b3965534eff4e1f2ecb2cf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374224"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>參數

*I.*<br/>
類型。

*基地*<br/>
另一種類型。

## <a name="remarks"></a>備註

測試一個介面是否派生自另一個介面。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                                       | 描述
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[驗證繼承說明程式::驗證](#verify) | 測試當前範本參數指定的兩個介面,並確定一個介面是否派生自另一個介面。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VerifyInheritanceHelper`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="verifyinheritancehelperverify"></a><a name="verify"></a>驗證繼承說明程式::驗證

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>備註

測試當前範本參數指定的兩個介面,並確定一個介面是否派生自另一個介面。

如果一個介面不是從另一個介面派生的,則發出錯誤。
