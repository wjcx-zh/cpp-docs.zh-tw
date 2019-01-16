---
title: InterfaceListHelper 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: c29a44249b432a7e0c15164307e95c51ae8b0536
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335687"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
樣板參數 0，這是必要。

*T1*<br/>
樣板參數 1，其預設值是 未指定。

*T2*<br/>
樣板參數 2，其預設值是 未指定。第三個樣板參數中。

*T3*<br/>
樣板參數 3，其預設值是 未指定。

*T4*<br/>
樣板參數 4，其預設值是 未指定。

*T5*<br/>
樣板參數 5，其預設值是 未指定。

*T6*<br/>
樣板參數 6，其預設值是 未指定。

*T7*<br/>
樣板參數 7，其預設值是 未指定。

*T8*<br/>
樣板參數 8，其預設值是 未指定。

*T9*<br/>
樣板參數 9，其預設值是 未指定。

## <a name="remarks"></a>備註

建置`InterfaceList`以遞迴方式套用指定的範本參數引數型別。

**InterfaceListHelper**範本會使用範本參數*T0*定義中的第一個資料成員`InterfaceList`結構，然後按一下 以遞迴方式套用**InterfaceListHelper**任何剩餘的範本參數的範本。 **InterfaceListHelper**停止時沒有任何剩餘的範本參數。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`TypeT`|InterfaceList 類型的同義字。|

## <a name="inheritance-hierarchy"></a>繼承階層

`InterfaceListHelper`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)