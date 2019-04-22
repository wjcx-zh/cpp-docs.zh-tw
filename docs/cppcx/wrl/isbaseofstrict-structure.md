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
ms.openlocfilehash: 85aeb71ceaa162cc6366836dd286f2f9983d34e2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784505"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>參數

*基底*<br/>
基底類型。

*衍生*<br/>
在衍生的型別。

## <a name="remarks"></a>備註

測試某個類型是否為另一個類型的基底。

第一個範本會測試是否為型別衍生自基底型別，可能會產生**真**或是**false**。 第二個範本會測試是否為型別衍生自本身，這一律會產生**false**。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

名稱                            | 描述
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | 指出是否會有一個類型的另一個基底。

## <a name="inheritance-hierarchy"></a>繼承階層

`IsBaseOfStrict`

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="value"></a>IsBaseOfStrict::value

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>備註

指出是否會有一個類型的另一個基底。

`value` 是 **，則為 true**如果型別`Base`的基底類別型別的`Derived`，否則就是**false**。
