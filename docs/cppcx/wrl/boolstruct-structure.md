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
ms.openlocfilehash: 4f2a5acf6edb824cff2121c1b6444181b5cfcf98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371845"
---
# <a name="boolstruct-structure"></a>BoolStruct 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>備註

結構`BoolStruct`定義`ComPtr`是否管理介面的物件存留期。 `BoolStruct`由[BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype)運算子在內部使用。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

名稱                          | 描述
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[布爾斯特:成員](#member) | 指定[ComPtr](comptr-class.md)正在或不是管理介面的物件存留期。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`BoolStruct`

## <a name="requirements"></a>需求

**標題:** 內部.h

**命名空間:** 微軟::WRL::D

## <a name="boolstructmember"></a><a name="member"></a>布爾斯特:成員

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
int Member;
```

### <a name="remarks"></a>備註

指定[ComPtr](comptr-class.md)正在或不是管理介面的物件存留期。
