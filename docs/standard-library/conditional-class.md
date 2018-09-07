---
title: conditional 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a553c2975dd5a58673bd4caa6e7c9ba25d33183
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106609"
---
# <a name="conditional-class"></a>conditional 類別

根據指定的條件選取這兩種類型之一。

## <a name="syntax"></a>語法

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>參數

*B*<br/>
判斷這個選取之類型的值。

*T1*<br/>
B 為 true 時的類型結果。

*T2*<br/>
B 為 false 時的類型結果。

## <a name="remarks"></a>備註

範本成員 typedef`conditional<B, T1, T2>::type`評估為*T1*當*B*評估 **，則為 true**，並且判斷值為*T2*時*B*評估為**false**。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
