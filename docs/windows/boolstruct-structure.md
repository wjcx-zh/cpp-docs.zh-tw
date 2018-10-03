---
title: BoolStruct 結構 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74a292f2253d29730e8ee9104ea81308081c0496
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234264"
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
