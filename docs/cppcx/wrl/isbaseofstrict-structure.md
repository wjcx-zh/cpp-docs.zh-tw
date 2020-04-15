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
ms.openlocfilehash: 71db5a1b52a7d7d5471c15591fb34d954b465d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371358"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>參數

*基地*<br/>
基底類型。

*派生*<br/>
派生類型。

## <a name="remarks"></a>備註

測試某個類型是否為另一個類型的基底。

第一個樣本測試類型是否派生自基類型,該基類型可能產生**真**或**假**。 第二個樣本測試類型是否派生自自身,後者始終生成**false**。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

名稱                            | 描述
------------------------------- | --------------------------------------------------
[是嚴格的基礎::值](#value) | 指示一種類型是否是另一種類型的基礎。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IsBaseOfStrict`

## <a name="requirements"></a>需求

**標題:** 內部.h

**命名空間:** 微軟::WRL::D

## <a name="isbaseofstrictvalue"></a><a name="value"></a>是嚴格的基礎::值

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>備註

指示一種類型是否是另一種類型的基礎。

`value`如果類型`Base`是型`Derived`態的基項,則為**true,** 否則為**false**。
