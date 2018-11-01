---
title: RaiseException 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: af0b35e1014f79c7907711b95200c241d31b6117
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594749"
---
# <a name="raiseexception-function"></a>RaiseException 函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>參數

*hr*<br/>
引發; 例外狀況的例外狀況代碼也就是在作業失敗的 HRESULT。

*dwExceptionFlags*<br/>
表示具持續性例外狀況 （旗標值會是零） 或 noncontinuable （旗標值為非零值） 的例外狀況的旗標。 根據預設，例外狀況是無法繼續。

## <a name="remarks"></a>備註

引發的例外狀況，在呼叫的執行緒。

如需詳細資訊，請參閱 Windows`RaiseException`函式。

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)