---
title: Move 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 65fe85e95453165430c7ef3cfd4c4bb2babd9868
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213703"
---
# <a name="move-function"></a>Move 函式

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>參數

*T*<br/>
引數型別。

*arg*<br/>
要移動的引數。

## <a name="return-value"></a>傳回值

參考或右值參考特性（如果有的話）之後的參數*arg*已移除。

## <a name="remarks"></a>備註

將指定的引數從一個位置移動到另一個位置。

如需詳細資訊，請參閱右值參考宣告子的**移動語義**一節[： & &](../../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>需求

**標頭：** 內部。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
