---
title: 'Module:: methodreleasenotifier 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cee634ab62e699b4de6af54a57b0fe3d6b5e9a40
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606604"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 類別

發行目前的模組中的最後一個物件時，會叫用事件處理常式。 物件和其指標-至-a-方法成員所指定的事件處理常式。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>參數

*T*  
成員函式是事件處理常式的物件類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Module::MethodReleaseNotifier::MethodReleaseNotifier 建構函式](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|初始化的新執行個體**module:: methodreleasenotifier**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Module::MethodReleaseNotifier::Invoke 方法](../windows/module-methodreleasenotifier-invoke-method.md)|呼叫目前相關聯的事件處理常式**module:: methodreleasenotifier**物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[Module::MethodReleaseNotifier::method_ 資料成員](../windows/module-methodreleasenotifier-method-data-member.md)|目前的事件處理常式會保留指標**module:: methodreleasenotifier**物件。|
|[Module::MethodReleaseNotifier::object_ 資料成員](../windows/module-methodreleasenotifier-object-data-member.md)|成員函式是目前的事件處理常式的物件會保留指標**module:: methodreleasenotifier**物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱
[Module 類別](../windows/module-class.md)