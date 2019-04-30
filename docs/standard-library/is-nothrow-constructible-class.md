---
title: is_nothrow_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 9ea11d54d49bf8f6ae6416f9663c2593cc66ea3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383603"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible 類別

測試當使用指定的引數類型時，類型是否是可建構的類型且已知不會擲回。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

*Args*<br/>
引數類型的建構函式中要比對*T*。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 類型*T*使用中的引數類型是可建構*Args*，並建構函式已知的編譯器不會擲回; 否則為 false。 型別*T*是可建構如果變數定義`T t(std::declval<Args>()...);`而言是否格式正確。 兩者*T*和中的所有型別*Args*必須是完整類型**void**，或界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
