---
title: SafeEquals |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeEquals function
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1aca5faeacc8559eff434a63d4caf63f32bbe59f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372106"
---
# <a name="safeequals"></a>SafeEquals

比較兩個數字，以判斷它們是否相等。

## <a name="syntax"></a>語法

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in]要比較的第一個數字。 這必須為類型 T。

*u*<br/>
[in]要比較的第二個點數。 這必須為類型 U。

## <a name="return-value"></a>傳回值

**真**如果*t*並*u*相等，否則為**false**。

## <a name="remarks"></a>備註

此方法會增強`==`因為**SafeEquals**可讓您比較兩種不同的數字。

這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計的單一比較作業，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。

> [!NOTE]
> 此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。

如需範本類型 T 和 U 的詳細資訊，請參閱[SafeInt 函式](../windows/safeint-functions.md)。

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** Microsoft::Utilities

## <a name="see-also"></a>另請參閱

[SafeInt 函式](../windows/safeint-functions.md)<br/>
[SafeInt 程式庫](../windows/safeint-library.md)<br/>
[SafeInt 類別](../windows/safeint-class.md)<br/>
[SafeNotEquals](../windows/safenotequals.md)