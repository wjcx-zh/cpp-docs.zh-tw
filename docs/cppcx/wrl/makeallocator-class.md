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
ms.openlocfilehash: dc0d83f2550646572a4eff2bec7850037c6dbf6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371327"
---
# <a name="makeallocator-class"></a>MakeAllocator 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

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

*有弱參考支援*<br/>
**為**支援弱引用的物件分配記憶體;為不支援弱引用的物件分配記憶體**為 false。**

## <a name="remarks"></a>備註

為可啟動類分配記憶體,無論是否具有弱引用支援。

重寫類`MakeAllocator`以實現使用者定義的記憶體分配模型。

`MakeAllocator`通常用於防止在構造期間物件引發時記憶體洩漏。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------
[製造定位器::製造定位器](#makeallocator)        | 將 `MakeAllocator` 類別的新執行個體初始化。
[製造定位器::\製造定位器](#tilde-makeallocator) | 取消初始化類的`MakeAllocator`當前實例。

### <a name="public-methods"></a>公用方法

名稱                                 | 描述
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[製造定位器::分配](#allocate) | 分配記憶體並將其與當前`MakeAllocator`物件關聯。
[製造者::D埃塔奇](#detach)     | 將[配置](#allocate)方法分配的記憶體與當前`MakeAllocator`物件分離。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`MakeAllocator`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="makeallocatorallocate"></a><a name="allocate"></a>製造定位器::分配

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>傳回值

如果成功,則指向分配的記憶體的指標;否則, `nullptr`.

### <a name="remarks"></a>備註

分配記憶體並將其與當前`MakeAllocator`物件關聯。

分配的記憶體的大小是當前`MakeAllocator`範本參數指定的類型的大小。

開發人員只需重寫`Allocate()`該方法,以實現不同的記憶體分配模型。

## <a name="makeallocatordetach"></a><a name="detach"></a>製造者::D埃塔奇

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>備註

將[配置](#allocate)方法分配的記憶體與當前`MakeAllocator`物件分離。

如果調用`Detach()`,則負責`Allocate`刪除 方法提供的記憶體。

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>製造定位器::製造定位器

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
MakeAllocator();
```

### <a name="remarks"></a>備註

將 `MakeAllocator` 類別的新執行個體初始化。

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>製造定位器::\製造定位器

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>備註

取消初始化類的`MakeAllocator`當前實例。

如有必要,此析構函數還會刪除基礎分配的記憶體。
