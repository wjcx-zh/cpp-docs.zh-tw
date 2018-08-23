---
title: MakeAllocator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e27be8eaddfc22474f15d7f9358050273252bf8a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610320"
---
# <a name="makeallocator-class"></a>MakeAllocator 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<
   typename T,
   bool hasWeakReferenceSupport =
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>, T)>
 class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>參數

*T*  
類型名稱。

*hasWeakReferenceSupport*  
**true**支援弱式參考的物件配置記憶體**false**不支援弱式參考的物件配置記憶體。

## <a name="remarks"></a>備註

配置記憶體可啟動類別，包含或不含弱式參考支援。

覆寫**MakeAllocator**類別來實作使用者定義的記憶體配置模型。

**MakeAllocator**通常用來防止記憶體流失，如果在建構期間擲回的物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[MakeAllocator::MakeAllocator 建構函式](../windows/makeallocator-makeallocator-constructor.md)|初始化的新執行個體**MakeAllocator**類別。|
|[MakeAllocator::~MakeAllocator 解構函式](../windows/makeallocator-tilde-makeallocator-destructor.md)|取消初始化目前的執行個體**MakeAllocator**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[MakeAllocator::Allocate 方法](../windows/makeallocator-allocate-method.md)|配置記憶體，並將它與目前相關聯**MakeAllocator**物件。|
|[MakeAllocator::Detach 方法](../windows/makeallocator-detach-method.md)|解除配置的記憶體[Allocate](../windows/makeallocator-allocate-method.md)方法，從目前**MakeAllocator**物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`MakeAllocator`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)