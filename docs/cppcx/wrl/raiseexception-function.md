---
title: RaiseException 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 3270057bf5b1b27a98bef1ab236291eab15d27ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213625"
---
# <a name="raiseexception-function"></a>RaiseException 函式

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>參數

*工時*<br/>
引發之例外狀況的例外狀況代碼。也就是失敗作業的 HRESULT。

*dwExceptionFlags*<br/>
表示持續性例外狀況的旗標（旗標值為零），或狀況例外狀況（旗標值不是零）。 根據預設，例外狀況為狀況。

## <a name="remarks"></a>備註

在呼叫執行緒中引發例外狀況。

如需詳細資訊，請參閱 Windows `RaiseException` 函式。

## <a name="requirements"></a>需求

**標頭：** 內部。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
