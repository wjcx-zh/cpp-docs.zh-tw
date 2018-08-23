---
title: FactoryCache 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df2335a49d2d5daf862db7cea7eb413c01164bee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609024"
---
# <a name="factorycache-structure"></a>FactoryCache 結構

支援的 Windows 執行階段 c + + 樣板程式庫基礎結構，並不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>備註

包含的 class factory 和 wrt 識別已註冊的值或 COM 類別物件的位置。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[FactoryCache::cookie 資料成員](../windows/factorycache-cookie-data-member.md)|包含的值，識別已註冊的 Windows 執行階段或 COM 類別物件，並稍後用來取消註冊的物件。|
|[FactoryCache::factory 資料成員](../windows/factorycache-factory-data-member.md)|指向 Windows 執行階段或 COM class factory。|

## <a name="inheritance-hierarchy"></a>繼承階層

`FactoryCache`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)