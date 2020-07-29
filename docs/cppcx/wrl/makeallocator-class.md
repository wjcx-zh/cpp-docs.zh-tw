---
title: MakeAllocator 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: 19d3ab294df8adc059424c97e5733ae9ebb75c9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218373"
---
# <a name="makeallocator-class"></a>MakeAllocator 類別

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
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
**`true`** 為支援弱式參考的物件配置記憶體;**`false`** 為不支援弱式參考的物件配置記憶體。

## <a name="remarks"></a>備註

配置可啟動類別的記憶體，包含或不含弱式參考支援。

覆寫 `MakeAllocator` 類別，以執行使用者定義的記憶體配置模型。

`MakeAllocator`通常用來避免物件在結構中擲回時的記憶體流失。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                  | 說明
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator：： MakeAllocator](#makeallocator)        | 初始化 `MakeAllocator` 類別的新執行個體。
[MakeAllocator：： ~ MakeAllocator](#tilde-makeallocator) | 將類別的目前實例 `MakeAllocator` 。

### <a name="public-methods"></a>公用方法

名稱                                 | 說明
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator：： Allocate](#allocate) | 配置記憶體，並將它與目前的物件產生關聯 `MakeAllocator` 。
[MakeAllocator：:D etach](#detach)     | 從目前的物件中，解除配置方法所[配置](#allocate)的記憶體 `MakeAllocator` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`MakeAllocator`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator：： Allocate

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>傳回值

如果成功，則為已配置記憶體的指標;否則為 **`nullptr`** 。

### <a name="remarks"></a>備註

配置記憶體，並將它與目前的物件產生關聯 `MakeAllocator` 。

配置的記憶體大小是目前範本參數所指定之類型的大小 `MakeAllocator` 。

開發人員只需要覆寫 `Allocate()` 方法，即可執行不同的記憶體配置模型。

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator：:D etach

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>備註

從目前的物件中，解除配置方法所[配置](#allocate)的記憶體 `MakeAllocator` 。

如果您呼叫 `Detach()` ，就必須負責刪除方法所提供的記憶體 `Allocate` 。

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator：： MakeAllocator

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
MakeAllocator();
```

### <a name="remarks"></a>備註

初始化 `MakeAllocator` 類別的新執行個體。

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator：： ~ MakeAllocator

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>備註

將類別的目前實例 `MakeAllocator` 。

此析構函式也會在必要時刪除基礎已配置的記憶體。
