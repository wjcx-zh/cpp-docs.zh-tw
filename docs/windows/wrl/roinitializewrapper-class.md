---
title: RoInitializeWrapper 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
ms.openlocfilehash: b43d5bb2f553d298584ab2ae497c22637d3beb0d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335701"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 類別

初始化 Windows 執行階段。

## <a name="syntax"></a>語法

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>備註

`RoInitializeWrapper` 是為了方便起見，會初始化 Windows 執行階段，並會傳回 HRESULT，指出作業是否成功。 因為類別的解構函式會呼叫`::Windows::Foundation::Uninitialize`，執行個體`RoInitializeWrapper`必須在全域或最上層範圍中宣告。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                    | 描述
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | 初始化 `RoInitializeWrapper` 類別的新執行個體。
[RoInitializeWrapper::~RoInitializeWrapper](#tilde-roinitializewrapper) | 終結的目前執行個體`RoInitializeWrapper`類別。

### <a name="public-operators"></a>公用運算子

名稱                                       | 描述
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | 擷取所產生的 HRESULT`RoInitializeWrapper`建構函式。

## <a name="inheritance-hierarchy"></a>繼承階層

`RoInitializeWrapper`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="hresult"></a>RoInitializeWrapper::HRESULT()

HRESULT 值所產生的最後一個擷取`RoInitializeWrapper`建構函式。

```cpp
operator HRESULT()
```

## <a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

初始化 `RoInitializeWrapper` 類別的新執行個體。

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>參數

*flags*<br/>
其中一個的 RO_INIT_TYPE 列舉型別，指定 Windows 執行階段所提供的支援。

### <a name="remarks"></a>備註

`RoInitializeWrapper`類別叫用`Windows::Foundation::Initialize(flags)`。

## <a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::~RoInitializeWrapper

取消初始化 Windows 執行階段。

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>備註

`RoInitializeWrapper`類別叫用`Windows::Foundation::Uninitialize()`。
