---
title: Platform::SizeT 實值類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 5add9212dc2655bc37cd357741073f855b009bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322154"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT 實值類別

表示物件的大小。 SizeT 是不帶正負號的資料類型。

## <a name="syntax"></a>語法

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>成員

|member|描述|
|------------|-----------------|
|[SizeT::SizeT 建構函式](#ctor)|使用指定的值，初始化類別的新執行個體。|

### <a name="requirements"></a>需求

**受支援的最小用戶端:** 視窗 8

**受支援的伺服器最少:** 視窗伺服器 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="sizetsizet-constructor"></a><a name="ctor"></a>大小T::SizeT建構函數

使用指定的值來初始化 SizeT 的新執行個體。

### <a name="syntax"></a>語法

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>參數

*值1*<br/>
32 位元不帶正負號的值。

*值2*<br/>
32 位元不帶正負號之值的指標。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
