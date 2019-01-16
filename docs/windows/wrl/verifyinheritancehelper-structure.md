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
ms.openlocfilehash: c37a0eb74fd65b3d349d5b8b7c792fbaf7d1ac9a
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336405"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>參數

*I*<br/>
類型。

*基底*<br/>
另一個型別。

## <a name="remarks"></a>備註

測試是否有一個介面衍生自另一個介面。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                                       | 描述
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper::Verify](#verify) | 測試目前的範本參數所指定的兩個介面，並決定是否要將一個介面衍生自其他。

## <a name="inheritance-hierarchy"></a>繼承階層

`VerifyInheritanceHelper`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInheritanceHelper::Verify

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>備註

測試目前的範本參數所指定的兩個介面，並決定是否要將一個介面衍生自其他。

如果有一個介面不衍生自其他，就會發出錯誤。
