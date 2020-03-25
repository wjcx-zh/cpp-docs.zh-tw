---
title: ActivationFactoryCallback 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 0be4bebcc561cdf1df3f2502c8cc1927bdc65564
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214210"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback 函式

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>參數

*activationId*<br/>
指定執行時間類別名稱之字串的控制碼。

*ppFactory*<br/>
當此作業完成時，就是對應至參數*activationId*的啟動處理站。

## <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 可能的失敗 Hresult CLASS_E_CLASSNOTAVAILABLE 和 E_INVALIDARG。

## <a name="remarks"></a>備註

取得指定之啟用識別碼的啟用 factory。

Windows 執行階段會呼叫這個回呼函式，以要求其執行時間類別名稱所指定的物件。

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
