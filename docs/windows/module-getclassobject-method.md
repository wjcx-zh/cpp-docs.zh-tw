---
title: 'Module:: getclassobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e0c8996823de35bbfd85d595556db933f34238a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599218"
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject 方法

擷取快取的 class factory。

## <a name="syntax"></a>語法

```cpp
 HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>參數

*clsid*  
類別識別碼。

*riid*  
您要求的介面識別碼。

*ppv*  
傳回的物件指標。

*伺服器名稱*  
中指定的伺服器名稱`ActivatableClassWithFactory`， `ActivatableClassWithFactoryEx`，或`ActivatableClass`巨集; 或是**nullptr**取得預設的伺服器名稱。

## <a name="return-value"></a>傳回值

## <a name="remarks"></a>備註

這個方法僅適用於 COM，而不是 Windows 執行階段。 這個方法只會公開`IClassFactory`方法。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱
[Module 類別](../windows/module-class.md)