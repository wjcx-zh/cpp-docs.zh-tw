---
title: InterfaceListHelper 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 1a7b4c19bbcdd4161e9078274f18f96a48f9e7d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213846"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>參數

*T0*<br/>
範本參數0，這是必要的。

*T1*<br/>
範本參數1，預設為未指定。

*T2*<br/>
範本參數2，預設為未指定。第三個樣板參數。

*T3*<br/>
範本參數3（預設為未指定）。

*T4*<br/>
範本參數4，預設為未指定。

*T5*<br/>
範本參數5（預設為未指定）。

*T6*<br/>
範本參數6（預設為未指定）。

*T7*<br/>
範本參數7預設為未指定。

*T8*<br/>
範本參數8（預設為未指定）。

*T9*<br/>
範本參數9，預設為未指定。

## <a name="remarks"></a>備註

藉由以遞迴方式套用指定的範本參數引數，建立 `InterfaceList` 型別。

**InterfaceListHelper**範本會使用樣板參數*T0*來定義 `InterfaceList` 結構中的第一個資料成員，然後以遞迴方式將**InterfaceListHelper**範本套用至任何剩餘的範本參數。 當沒有剩餘的範本參數時， **InterfaceListHelper**就會停止。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`TypeT`|InterfaceList 類型的同義字。|

## <a name="inheritance-hierarchy"></a>繼承階層

`InterfaceListHelper`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
