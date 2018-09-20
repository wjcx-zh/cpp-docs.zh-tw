---
title: 'Module:: registercomobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7cccebf6e1c6004a2416f4fdeb254369f9aa7b72
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410308"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject 方法

讓其他應用程式可以連線到它們，請註冊一個或多個 COM 物件。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);

```

### <a name="parameters"></a>參數

*伺服器名稱*<br/>
完整伺服器名稱。

*clsid*<br/>
若要註冊的 Clsid 的陣列。

*處理站*<br/>
正在發行其可用性的類別物件的 IUnknown 介面的陣列。

*Cookie*<br/>
作業完成後，物件的陣列的指標識別類別的值，已註冊。 稍後會使用這些值，撤銷。

*count*<br/>
若要註冊的 Clsid 數目。

## <a name="return-value"></a>傳回值

S_OK 如果成功;否則，例如指出原因的 CO_E_OBJISREG HRESULT 作業失敗。

## <a name="remarks"></a>備註

COM 物件會向 CLSCTX 列舉型別的 CLSCTX_LOCAL_SERVER 列舉值。

連線到已註冊的物件的型別由目前的組合*comflag*樣板參數和 REGCLS 列舉型別的 REGCLS_SUSPENDED 列舉值。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Module 類別](../windows/module-class.md)