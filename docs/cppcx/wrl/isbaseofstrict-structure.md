---
title: IsBaseOfStrict 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 11acb4c7162a17ff763a574c27c186061ae476a7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211524"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>參數

*群體*<br/>
基底類型。

*衍生*<br/>
衍生的型別。

## <a name="remarks"></a>備註

測試某個類型是否為另一個類型的基底。

第一個範本會測試類型是否衍生自基底類型，這可能會產生 **`true`** 或 **`false`** 。 第二個範本會測試類型是否衍生自本身，這一律會產生 **`false`** 。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

名稱                            | 說明
------------------------------- | --------------------------------------------------
[IsBaseOfStrict：： value](#value) | 指出某個類型是否為另一個類型的基底。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IsBaseOfStrict`

## <a name="requirements"></a>需求

**標頭：** 內部。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="isbaseofstrictvalue"></a><a name="value"></a>IsBaseOfStrict：： value

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>備註

指出某個類型是否為另一個類型的基底。

`value`**`true`** 如果 type `Base` 是類型的基類，則為 `Derived` ，否則為 **`false`** 。
