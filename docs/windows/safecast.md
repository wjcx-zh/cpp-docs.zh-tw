---
title: SafeCast |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2872f1639a11d537dd79b878a166a3afb5fd8667
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719159"
---
# <a name="safecast"></a>SafeCast

將一種類型的編號，另一種類型的轉換。

## <a name="syntax"></a>語法

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>參數

*From*<br/>
[in]要轉換的來源點數。 這必須是型別`T`。

*若要*<br/>
[out]新的數字類型的參考。 這必須是型別`U`。

## <a name="return-value"></a>傳回值

**true**如果沒有發生錯誤;**false**發生錯誤。

## <a name="remarks"></a>備註

這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計的單一轉換作業，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。

> [!NOTE]
> 這個方法應該只用於時必須保護單一作業。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。

如需範本類型 T 和 U 的詳細資訊，請參閱[SafeInt 函式](../windows/safeint-functions.md)。

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** Microsoft::Utilities

## <a name="see-also"></a>另請參閱

[SafeInt 函式](../windows/safeint-functions.md)  
[SafeInt 程式庫](../windows/safeint-library.md)  
[SafeInt 類別](../windows/safeint-class.md)