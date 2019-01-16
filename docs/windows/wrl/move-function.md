---
title: Move 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 1a03216197462090f38d3bc2065fe227f0667919
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336365"
---
# <a name="move-function"></a>Move 函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
若要移動的引數。

## <a name="return-value"></a>傳回值

參數*arg*之後參考或右值參考的特性，如果有的話，已移除。

## <a name="remarks"></a>備註

將指定的引數從一個位置移到另一個。

如需詳細資訊，請參閱 <<c0>  **移動語意**一節[右值參考宣告子： & &](../../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)