---
title: SafeLessThanEquals |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThanEquals function
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a291b7a2cd8c33e743a31d53c6330f67e915662a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713059"
---
# <a name="safelessthanequals"></a>SafeLessThanEquals

比較兩個數字。

## <a name="syntax"></a>語法

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in]要比較的第一個數字。 這必須是型別`T`。

*u*<br/>
[in]要比較的第二個點數。 這必須是型別`U`。

## <a name="return-value"></a>傳回值

**真**如果*t*小於或等於*u*; 否則為**false**。

## <a name="remarks"></a>備註

**SafeLessThanEquals**擴充一般比較運算子，可讓您比較兩種不同的數字。

這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計的單一比較作業，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。

> [!NOTE]
> 此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。

如需範本類型的詳細資訊`T`並`U`，請參閱[SafeInt 函式](../windows/safeint-functions.md)。

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** Microsoft::Utilities

## <a name="see-also"></a>另請參閱

[SafeInt 函式](../windows/safeint-functions.md)  
[SafeInt 程式庫](../windows/safeint-library.md)  
[SafeInt 類別](../windows/safeint-class.md)  
[SafeGreaterThan](../windows/safegreaterthan.md)  
[SafeLessThan](../windows/safelessthan.md)  
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)