---
title: SafeLessThan |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThan
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a5824b1e3ba050cf8c6d9c0f7b56231211f1f59a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377190"
---
# <a name="safelessthan"></a>SafeLessThan

判斷一個數字是否小於另一個。

## <a name="syntax"></a>語法

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in]第一個數字。 這必須是型別`T`。

*u*<br/>
[in]第二個的號碼。 這必須是型別`U`。

## <a name="return-value"></a>傳回值

**真**如果*t*是小於*u*; 否則為**false**。

## <a name="remarks"></a>備註

這個方法會增強標準的比較運算子，因為**SafeLessThan**可讓您比較兩種不同的數字。

這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計的單一比較作業，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。

> [!NOTE]
> 此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用`SafeInt`類別，而不是呼叫個別獨立函式。

如需範本類型的詳細資訊`T`並`U`，請參閱[SafeInt 函式](../windows/safeint-functions.md)。

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** Microsoft::Utilities

## <a name="see-also"></a>另請參閱

[SafeInt 函式](../windows/safeint-functions.md)<br/>
[SafeInt 程式庫](../windows/safeint-library.md)<br/>
[SafeInt 類別](../windows/safeint-class.md)<br/>
[SafeLessThanEquals](../windows/safelessthanequals.md)<br/>
[SafeGreaterThan](../windows/safegreaterthan.md)<br/>
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)