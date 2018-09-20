---
title: 'Module:: registerwinrtobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 496b1ccac5b998ba08f4e2eccfe31ffd18f2c37d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431784"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject 方法

讓其他應用程式可以連線到它們，請註冊一個或多個 Windows 執行階段物件。

## <a name="syntax"></a>語法

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)  
```

### <a name="parameters"></a>參數

*伺服器名稱*<br/>
指定此作業所影響的物件子集的名稱。

*activatableClassIds*<br/>
若要註冊的可啟動 Clsid 的陣列。

*Cookie*<br/>
識別已註冊的類別物件的值。 此值稍後用來撤銷註冊。

*count*<br/>
若要註冊的物件數目。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，錯誤 HRESULT CO_E_OBJISREG 指出的原因，例如作業失敗。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Module 類別](../windows/module-class.md)