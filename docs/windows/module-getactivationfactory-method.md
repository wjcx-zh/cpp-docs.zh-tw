---
title: 'Module:: getactivationfactory 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e87ea3b0e44732d4271385073c48fd92e1aa114
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608923"
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory 方法

取得啟用 factory 模組。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>參數

*pActivatibleClassId*  
執行階段類別的 IID。

*ppIFactory*  
指定的執行階段類別 IActivationFactory。

*伺服器名稱*  
在目前模組的 class factory 子集的名稱。 指定用於的伺服器名稱[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)巨集，或指定**nullptr**取得預設的伺服器名稱。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，GetActivationFactory 所傳回的 HRESULT。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Module 類別](../windows/module-class.md)  
[ActivatableClass 巨集](../windows/activatableclass-macros.md)