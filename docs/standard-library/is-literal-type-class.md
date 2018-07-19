---
title: is_literal_type 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_literal_type
dev_langs:
- C++
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a14b2fe5a14eaf264377a1f818227d73e134b030
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957958"
---
# <a name="isliteraltype-class"></a>is_literal_type 類別

測試類型是否可用來作為 `constexpr` 變數，或是被 `constexpr` 函式建構、使用或傳回。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>參數

*T*要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是*常值型別*，否則為 false。 常值的型別是**void**，純量類型、 參考類型、 常值的型別，陣列或常值類別類型。 常值類別類型是一種擁有極簡解構函式的類別類型，它若不是匯總類型，就是至少有一個非移動、非複製 `constexpr` 建構函式，且其所有基底類別和非靜態資料成員都是非揮發性的常值類型。 雖然常值的類型一律是常值類型，但常值類型的概念還包括編譯器可在編譯階段評估為 `constexpr` 的任何項目。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
