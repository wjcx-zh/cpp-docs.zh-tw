---
title: HandleT 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6da9451d6f009bad6163efec23bb6f920a56df49
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590526"
---
# <a name="handlet-class"></a>HandleT 類別

物件表示的控制代碼。

## <a name="syntax"></a>語法

```cpp
template <
   typename HandleTraits
>
class HandleT;
```

### <a name="parameters"></a>參數

*HandleTraits*  
執行個體[HandleTraits](../windows/handletraits-structure.md)結構定義的控制代碼的一般特性。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`Traits`|`HandleTraits` 的同義字。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[HandleT::HandleT 建構函式](../windows/handlet-handlet-constructor.md)|初始化的新執行個體**HandleT**類別。|
|[HandleT::~HandleT 解構函式](../windows/handlet-tilde-handlet-destructor.md)|取消初始化的執行個體**HandleT**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[HandleT::Attach 方法](../windows/handlet-attach-method.md)|將指定的控制代碼與目前**HandleT**物件。|
|[HandleT::Close 方法](../windows/handlet-close-method.md)|關閉目前**HandleT**物件。|
|[HandleT::Detach 方法](../windows/handlet-detach-method.md)|取消目前的關聯**HandleT**從其基礎控制代碼的物件。|
|[HandleT::Get 方法](../windows/handlet-get-method.md)|取得基礎控制代碼的值。|
|[HandleT::IsValid 方法](../windows/handlet-isvalid-method.md)|指出是否目前**HandleT**物件表示的控制代碼。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[HandleT::InternalClose 方法](../windows/handlet-internalclose-method.md)|關閉目前**HandleT**物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[HandleT::operator= 運算子](../windows/handlet-operator-assign-operator.md)|將指定的值移**HandleT**物件與目前**HandleT**物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[HandleT::handle_ 資料成員](../windows/handlet-handle-data-member.md)|包含所表示的控制代碼**HandleT**物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`HandleT`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)