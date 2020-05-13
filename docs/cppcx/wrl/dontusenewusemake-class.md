---
title: DontUseNewUseMake 類別
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: ae67373b4f2f2d4a199b939b06e6f526f1365446
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371546"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>備註

防止在`new`中`RuntimeClass`使用 運算符。 因此,您必須改用[Make 函數](make-function.md)。

## <a name="members"></a>成員

### <a name="public-operators"></a>公用運算子

名稱                                             | 描述
------------------------------------------------ | ---------------------------------------------------------------------------
[不要使用新使用製作::運算元新](#operator-new) | 重載運算子`new`並防止它使用 。`RuntimeClass`

## <a name="inheritance-hierarchy"></a>繼承階層架構

`DontUseNewUseMake`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a>不要使用新使用製作::運算元新

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>參數

*__unnamed0*<br/>
指定要分配的記憶體位元組數的未命名參數。

*位置*<br/>
要分配的類型。

### <a name="return-value"></a>傳回值

提供一個在重載運算符時傳遞其他參數的方法`new`。

### <a name="remarks"></a>備註

重載運算子`new`並防止它使用 。`RuntimeClass`
