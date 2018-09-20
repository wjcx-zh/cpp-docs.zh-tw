---
title: SafeModulus |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeModulus
dev_langs:
- C++
helpviewer_keywords:
- SafeModulus function
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48feb16696243479849492171732b0d070ce032f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427910"
---
# <a name="safemodulus"></a>SafeModulus

執行模數作業上兩個數字。

## <a name="syntax"></a>語法

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>參數

*t*<br/>
[in]除數。 這必須是型別`T`。

*u*<br/>
[in]被除數。 這必須是型別`U`。

*結果*<br/>
[out]參數所在**SafeModulus**儲存結果。

## <a name="return-value"></a>傳回值

**true**如果沒有發生錯誤;**false**發生錯誤。

## <a name="remarks"></a>備註

這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計單一的模數運算，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。

> [!NOTE]
> 此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。

如需範本類型的詳細資訊`T`並`U`，請參閱[SafeInt 函式](../windows/safeint-functions.md)。

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** Microsoft::Utilities

## <a name="see-also"></a>另請參閱

[SafeInt 函式](../windows/safeint-functions.md)<br/>
[SafeInt 程式庫](../windows/safeint-library.md)<br/>
[SafeInt 類別](../windows/safeint-class.md)<br/>
[SafeDivide](../windows/safedivide.md)