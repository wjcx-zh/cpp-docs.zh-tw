---
title: decay 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 23c2cff37e67e78ba68c37468c110d7a3725b785
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394052"
---
# <a name="decay-class"></a>decay 類別

由值來傳遞時，會產生類型。 可產生非參考、非 const、靜態類型，或從函式或陣列類型建立類型的指標。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>參數

*T*<br/>
要修改的類型。

## <a name="remarks"></a>備註

您可使用 decay 範本產生類型，如同將類型作為引數由值來傳遞一樣。 範本類別成員 typedef `type` 類型所儲存的修改類型，是在下列階段定義：

- 類型 `U` 定義為 `remove_reference<T>::type`。

- 如果 `is_array<U>::value` 為 true，則修改的類型 `type` 為 `remove_extent<U>::type *`。

- 否則，如果 `is_function<U>::value` 為 true，則修改的類型 `type` 為 `add_pointer<U>::type`。

- 否則，修改的類型 `type` 為 `remove_cv<U>::type`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
