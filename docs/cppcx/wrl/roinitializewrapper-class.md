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
ms.openlocfilehash: eba9162f17b98d13a9caf956b4f110b89dd81c37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371235"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 類別

初始化 Windows 運行時。

## <a name="syntax"></a>語法

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>備註

`RoInitializeWrapper`是初始化 Windows 運行時並返回指示操作是否成功的 HRESULT 的便利。 由於類析構函數調用`::Windows::Foundation::Uninitialize`,必須在全域`RoInitializeWrapper`或頂級作用域中聲明 的 實例。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                    | 描述
----------------------------------------------------------------------- | -----------------------------------------------------------------
[放大縮小字型功能 放大縮小字型功能](#roinitializewrapper)        | 將 `RoInitializeWrapper` 類別的新執行個體初始化。
[Ro初始化包裝器::\Ro初始化包裝器](#tilde-roinitializewrapper) | 銷毀`RoInitializeWrapper`類的當前實例。

### <a name="public-operators"></a>公用運算子

名稱                                       | 描述
------------------------------------------ | ------------------------------------------------------------------------
[放大縮小字型功能 放大縮小字型功能](#hresult) | 檢索`RoInitializeWrapper`建構函數生成的HRESULT。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`RoInitializeWrapper`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a>放大縮小字型功能 放大縮小字型功能

檢索最後`RoInitializeWrapper`一個構造函數生成的 HRESULT 值。

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a>放大縮小字型功能 放大縮小字型功能

將 `RoInitializeWrapper` 類別的新執行個體初始化。

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>參數

*標誌*<br/>
RO_INIT_TYPE枚舉之一,它指定 Windows 運行時提供的支援。

### <a name="remarks"></a>備註

類別`RoInitializeWrapper`呼叫`Windows::Foundation::Initialize(flags)`。

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a>Ro初始化包裝器::\Ro初始化包裝器

取消初始化 Windows 運行時。

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>備註

類別`RoInitializeWrapper`呼叫`Windows::Foundation::Uninitialize()`。
