---
title: Platform::MTAThreadAttribute 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 700eeae226be48c1f6659d621f2f5c0ed397bb7f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213043"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute 類別

指出應用程式的執行緒模型為多執行緒 Apartment (MTA)。

## <a name="syntax"></a>語法

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[MTAThreadAttribute](#ctor)的函式1構造函式|初始化類別的新執行個體。|

### <a name="public-methods"></a>公用方法

MTAThreadAttribute 屬性繼承自[Platform：： Object 類別](../cppcx/platform-object-class.md)。 MTAThreadAttribute 也會多載或具有下列成員：

|名稱|說明|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|判斷指定的物件是否等於目前的物件。|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|傳回這個執行個體的雜湊碼。|
|[MTAThreadAttribute::ToString](#tostring)|傳回代表目前物件的字串。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Platform`

### <a name="requirements"></a>需求

**中繼資料：** platform.winmd

**命名空間：** Platform

## <a name="mtathreadattribute-constructor"></a><a name="ctor"></a>MTAThreadAttribute 的構造函式

初始化 MTAThreadAttribute 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
public:MTAThreadAttribute();
```

## <a name="mtathreadattributeequals"></a><a name="equals"></a>MTAThreadAttribute：： Equals

判斷指定的物件是否等於目前的物件。

### <a name="syntax"></a>語法

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>參數

*obj*<br/>
要比較的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果物件相等，則為，否則為 **`false`** 。

## <a name="mtathreadattributegethashcode"></a><a name="gethashcode"></a>MTAThreadAttribute：： GetHashCode

傳回這個執行個體的雜湊碼。

### <a name="syntax"></a>語法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>傳回值

這個執行個體的雜湊碼。

## <a name="mtathreadattributetostring"></a><a name="tostring"></a>MTAThreadAttribute：： ToString

傳回代表目前物件的字串。

### <a name="syntax"></a>語法

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>傳回值

代表目前物件的字串。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)
