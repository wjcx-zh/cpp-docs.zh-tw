---
title: is_final 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_final
dev_langs:
- C++
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 101d987574ca789ce674c7ed01726847a66a4747
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962009"
---
# <a name="isfinal-class"></a>is_final 類別

測試類型是否是標示為 `final` 的類別類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>參數

*T*要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*標示為類別類型`final`，否則為 false。 如果*T*是類別類型，它必須是完整的型別。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[final 規範](../cpp/final-specifier.md)<br/>
