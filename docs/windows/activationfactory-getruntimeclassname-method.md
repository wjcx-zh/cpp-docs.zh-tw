---
title: 'Activationfactory:: Getruntimeclassname 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
dev_langs:
- C++
helpviewer_keywords:
- GetRuntimeClassName method
ms.assetid: 74e34f0a-9c51-4b40-89f5-45c6c5886ece
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fbae13c6ce70533b8338d47893b6007a3032abab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416301"
---
# <a name="activationfactorygetruntimeclassname-method"></a>ActivationFactory::GetRuntimeClassName 方法

取得物件的執行階段類別名稱，目前**ActivationFactory**具現化。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>參數

*runtimeName*<br/>
這項作業完成時，包含物件的執行階段類別名稱的字串的控制代碼的目前**ActivationFactory**具現化。

## <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ActivationFactory 類別](../windows/activationfactory-class.md)