---
title: 'Module:: unregistercomobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3409e0e2c1cac5f3934902523edd2653839989ed
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575754"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject 方法

取消註冊一或多個 COM 物件，這是為了避免與它們連線的其他應用程式。

## <a name="syntax"></a>語法

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>參數

*伺服器名稱*  
（未使用）

*Cookie*  
識別要取消註冊的類別物件的值的指標陣列。 建立陣列[RegisterCOMObject](../windows/module-registercomobject-method.md)方法。

*count*  
若要取消註冊的類別數目。

## <a name="return-value"></a>傳回值

如果這項作業是成功則為 S_OK否則，錯誤的 HRESULT，指出的原因，作業失敗。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱
[Module 類別](../windows/module-class.md)