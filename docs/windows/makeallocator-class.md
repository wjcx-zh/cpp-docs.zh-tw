---
title: MakeAllocator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6cb6574172747712fa2670b4444b17bec047a8cf
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169732"
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

*T*<br/>
類型名稱。

*hasWeakReferenceSupport*<br/>
`true` 為支援弱式參考的物件配置記憶體`false`不支援弱式參考的物件配置記憶體。

## <a name="remarks"></a>備註

配置記憶體可啟動類別，包含或不含弱式參考支援。

覆寫`MakeAllocator`類別來實作使用者定義的記憶體配置模型。

`MakeAllocator` 通常用來防止記憶體流失，如果在建構期間擲回的物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------
[Makeallocator:: Makeallocator](#makeallocator)        | 初始化 `MakeAllocator` 類別的新執行個體。
[MakeAllocator:: ~ MakeAllocator](#tilde-makeallocator) | 取消初始化目前的執行個體`MakeAllocator`類別。

### <a name="public-methods"></a>公用方法

名稱                                 | 描述
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[Makeallocator:: Allocate](#allocate) | 配置記憶體，並將它與目前關聯`MakeAllocator`物件。
[Makeallocator:: Detach](#detach)     | 解除配置的記憶體[Allocate](#allocate)方法，從目前`MakeAllocator`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`MakeAllocator`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="allocate"></a>Makeallocator:: Allocate

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>傳回值

如果成功，已配置的記憶體; 指標否則， `nullptr`。

### <a name="remarks"></a>備註

配置記憶體，並將它與目前關聯`MakeAllocator`物件。

配置的記憶體大小是由目前指定之型別的大小`MakeAllocator`樣板參數。

開發人員必須覆寫只`Allocate()`方法，以實作不同的記憶體配置模型。

## <a name="detach"></a>Makeallocator:: Detach

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>備註

解除配置的記憶體[Allocate](#allocate)方法，從目前`MakeAllocator`物件。

如果您呼叫`Detach()`，您必須負責刪除所提供的記憶體`Allocate`方法。

## <a name="makeallocator"></a>Makeallocator:: Makeallocator

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
MakeAllocator();
```

### <a name="remarks"></a>備註

初始化 `MakeAllocator` 類別的新執行個體。

## <a name="tilde-makeallocator"></a>MakeAllocator:: ~ MakeAllocator

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>備註

取消初始化目前的執行個體`MakeAllocator`類別。

如有必要，此解構函式也會刪除基礎配置的記憶體。
