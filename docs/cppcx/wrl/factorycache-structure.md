---
title: FactoryCache 結構
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 507d35179b9fa86399e56b18171800f41eaf1f10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371496"
---
# <a name="factorycache-structure"></a>FactoryCache 結構

支援 Windows 運行時 C++範本庫基礎結構,並且不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>備註

包含類工廠的位置和標識已註冊的 wrt 或 COM 類物件的值。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

名稱                              | 描述
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[工廠緩存::餅乾](#cookie)   | 包含標識已註冊的 Windows 運行時或 COM 類物件的值,以後用於取消註冊該物件。
[工廠緩存::工廠](#factory) | 指向 Windows 運行時或 COM 類工廠。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`FactoryCache`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間:** 微軟::WRL::D

## <a name="factorycachecookie"></a><a name="cookie"></a>工廠緩存::餅乾

支援 Windows 運行時 C++範本庫基礎結構,並且不打算直接從代碼中使用。

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>備註

包含標識已註冊的 Windows 運行時或 COM 類物件的值,以後用於取消註冊該物件。

## <a name="factorycachefactory"></a><a name="factory"></a>工廠緩存::工廠

支援 Windows 運行時 C++範本庫基礎結構,並且不打算直接從代碼中使用。

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>備註

指向 Windows 運行時或 COM 類工廠。
