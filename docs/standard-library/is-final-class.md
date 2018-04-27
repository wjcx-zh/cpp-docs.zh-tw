---
title: is_final 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_final
dev_langs:
- C++
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3bf78255367b22b9b933b580d768f417f1ebab4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="isfinal-class"></a>is_final 類別

測試類型是否是標示為 `final` 的類別類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>參數

`T` 要查詢的類型。

## <a name="remarks"></a>備註

如果類型 `T` 是標示為 `final` 的類別類型，類型述詞執行個體的值就會是 true，否則會是 false。 如果 `T` 是類別類型，就必須是完整類型。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[final 規範](../cpp/final-specifier.md)<br/>
