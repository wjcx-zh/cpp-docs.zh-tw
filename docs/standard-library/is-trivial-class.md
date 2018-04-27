---
title: is_trivial 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_trivial
dev_langs:
- C++
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7f6da587ec523db28b133f4219d5c35faa11734a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="istrivial-class"></a>is_trivial 類別

測試類型是否為 trivial 類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>參數

`T` 要查詢的類型。

## <a name="remarks"></a>備註

如果類型 `T` 是 trivial 類型，則類型述詞的執行個體為 true，否則為 false。 trivial 類型是純量類型、可完整複製類別類型、這些類型的陣列和 cv 限定版本。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
