---
title: ActivationFactoryCallback 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7979dd21d68c5b1e2606573a5271fc8deafdfb07
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604176"
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

*activationId*  
控制代碼指定的執行階段類別名稱的字串。

*ppFactory*  
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

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)