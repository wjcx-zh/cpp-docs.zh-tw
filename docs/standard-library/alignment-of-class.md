---
title: alignment_of 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9af19f046cf6de44448e3fcddf97584f58adc9ae
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="alignmentof-class"></a>alignment_of 類別

取得指定類型的對齊方式。 此結構是針對 [alignof](../cpp/alignof-and-alignas-cpp.md) 所實作。 若只需要查詢對齊值，請直接使用 `alignof`。 當您需要整數常數 (例如進行標記分派時)，請使用 alignment_of。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>參數

`Ty` 要查詢的類型。

## <a name="remarks"></a>備註

類型查詢會保存類型 `Ty` 的對齊值。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage 類別](../standard-library/aligned-storage-class.md)<br/>
