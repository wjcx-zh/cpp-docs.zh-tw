---
title: GetActivationFactory 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
ms.openlocfilehash: 430b4ed3f6a02fd3db2bcab05fbb7f21f5367b5c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213976"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory 函式

抓取範本參數所指定之類型的啟用 factory。

## <a name="syntax"></a>語法

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>參數

*T*<br/>
範本參數，指定啟用處理站的類型。

*activatableClassId*<br/>
啟用 factory 可以產生的類別名稱。

*工廠*<br/>
當此作業完成時，為型*別 T*之啟動 factory 的參考。

## <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，就會出現錯誤 HRESULT，指出此作業失敗的原因。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Windows：： Foundation

## <a name="see-also"></a>另請參閱

[Windows::Foundation 命名空間](windows-foundation-namespace.md)
