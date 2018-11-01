---
title: is_trivially_copyable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: 181152bff1d7c2e4f97678b48310f744080822ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554360"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable 類別

測試類型是否是可透過極簡方式複製的類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是可完整複製類型，否則為 false。 可透過極簡方式複製的類型沒有任何非極簡的複製作業、移動作業或解構函式。 一般而言，如果能以位元複製方式實作複製作業，該複製作業即可視為極簡。 內建類型和可透過極簡方式複製的類型陣列，都是可透過極簡方式複製的類型。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
