---
title: 'Safeint:: Safeint |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de318ab79638f63fae98856987340ad62534f695
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721341"
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt

建構**SafeInt**物件。

## <a name="syntax"></a>語法

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)  
```

### <a name="parameters"></a>參數

*i*<br/>
[in]新的值**SafeInt**物件。 這必須是類型 T 或 U，根據建構函式的參數。

*b*<br/>
[in]新的布林值**SafeInt**物件。

*u*<br/>
[in]A **SafeInt**為類型 u。新**SafeInt**物件會有相同的值*u*，但會是 t 型別

U 中儲存的資料型別**SafeInt**。 這可以是布林值、 字元或整數類型。 如果是整數類型，它可以是帶正負號或不帶正負號和介於 8 到 64 位元。

## <a name="remarks"></a>備註

如需範本類型的詳細資訊`T`並`E`，請參閱[SafeInt 類別](../windows/safeint-class.md)。

建構函式的輸入的參數*我*或是*u*，必須是布林值、 字元或整數類型。 如果它是參數的另一種**SafeInt**類別會呼叫[static_assert](../cpp/static-assert.md)表示無效的輸入的參數。

使用範本類型的建構函式`U`自動轉換為所指定之類型的 輸入的參數`T`。 **SafeInt**類別將不會遺失任何資料的資料轉換。 它會報告錯誤處理常式`E`如果無法轉換輸入資料`T`不會遺失資料。

如果您建立**SafeInt**從布林值的參數，您必須立即初始化的值。 您無法建構**SafeInt**使用程式碼`SafeInt<bool> sb;`。 這會產生編譯錯誤。

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** msl:: utilities

## <a name="see-also"></a>另請參閱

[SafeInt 程式庫](../windows/safeint-library.md)  
[SafeInt 類別](../windows/safeint-class.md)  
[SafeIntException 類別](../windows/safeintexception-class.md)