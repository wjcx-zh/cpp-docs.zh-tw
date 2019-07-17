---
title: hash 結構
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: ef620867a5c31c7bd2030803edd6eaea6bbb5726
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243715"
---
# <a name="hash-structure"></a>hash 結構

樣板類別將它的方法定義為傳回 `val.hash_code()`。 方法會定義雜湊函式，用來將 [type_index](../standard-library/type-index-class.md) 類型的值對應到索引值的分佈。

## <a name="syntax"></a>語法

```cpp
template <> struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;
};
```

## <a name="specialized-types"></a>特製化的類型

### <a name="system_error"></a> \<system_error >

```cpp
template <class T> struct hash;
template <> struct hash<error_code>;
template <> struct hash<error_condition>;
```

## <a name="see-also"></a>另請參閱

[\<typeindex>](../standard-library/typeindex.md)<br/>
