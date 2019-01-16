---
title: ActivationFactoryCallback 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 93db10e19cce0658bf731c14e7ac76b575841bf3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336378"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback 函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>參數

*activationId*<br/>
控制代碼指定的執行階段類別名稱的字串。

*ppFactory*<br/>
這項作業完成時，都會對應至參數啟動處理站*activationId*。

## <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 可能的失敗的 Hresult 為 CLASS_E_CLASSNOTAVAILABLE 和 E_INVALIDARG。

## <a name="remarks"></a>備註

取得啟用 factory 做為指定的啟用識別碼。

Windows 執行階段會呼叫此回呼函式，來要求執行階段類別名稱指定的物件。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)