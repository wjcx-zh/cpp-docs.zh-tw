---
title: is_trivially_copyable 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19bed4a455ea2b0b894ba842f349aa304e9f261d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964679"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable 類別

測試類型是否是可透過極簡方式複製的類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>參數

*T*要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是可完整複製類型，否則為 false。 可透過極簡方式複製的類型沒有任何非極簡的複製作業、移動作業或解構函式。 一般而言，如果能以位元複製方式實作複製作業，該複製作業即可視為極簡。 內建類型和可透過極簡方式複製的類型陣列，都是可透過極簡方式複製的類型。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
