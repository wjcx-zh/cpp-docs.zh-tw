---
title: BoolStruct 結構
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: d79ea93bf95040efe79e3e3c57ceb3397fd257de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643400"
---
# <a name="boolstruct-structure"></a>BoolStruct 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>備註

`BoolStruct`結構會定義是否`ComPtr`管理介面的物件存留期。 `BoolStruct` 會在內部使用[BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)運算子。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

名稱                          | 描述
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct:: Member](#member) | 指定[ComPtr](../windows/comptr-class.md) ，或不是，管理介面的物件存留期。

## <a name="inheritance-hierarchy"></a>繼承階層

`BoolStruct`

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="member"></a>Boolstruct:: Member

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
int Member;
```

### <a name="remarks"></a>備註

指定[ComPtr](../windows/comptr-class.md) ，或不是，管理介面的物件存留期。
