---
title: 'Platform:: mtathreadattribute 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2bac4ae71d98cb81eaa05bd3fd6fdf817145e22
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163747"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute 類別

指出應用程式的執行緒模型為多執行緒 Apartment (MTA)。

## <a name="syntax"></a>語法

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[MTAThreadAttribute 建構函式 1](#ctor)建構函式|初始化類別的新執行個體。|

### <a name="public-methods"></a>公用方法

MTAThreadAttribute 屬性繼承自[platform:: object 類別](../cppcx/platform-object-class.md)。 MTAThreadAttribute 也會多載或具有下列成員：

|名稱|描述|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|判斷指定的物件是否等於目前的物件。|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|傳回這個執行個體的雜湊碼。|
|[MTAThreadAttribute::ToString](#tostring)|傳回代表目前物件的字串。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Platform`

### <a name="requirements"></a>需求

**中繼資料：** platform.winmd

**命名空間：** Platform

## <a name="ctor"></a> MTAThreadAttribute 建構函式

初始化 MTAThreadAttribute 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
public:MTAThreadAttribute();
```

## <a name="equals"></a> MTAThreadAttribute::Equals

判斷指定的物件是否等於目前的物件。

### <a name="syntax"></a>語法

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>參數

*obj*<br/>
要比較的物件。

### <a name="return-value"></a>傳回值

**真**如果物件相等，否則**false**。

## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode

傳回這個執行個體的雜湊碼。

### <a name="syntax"></a>語法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>傳回值

這個執行個體的雜湊碼。

## <a name="tostring"></a> MTAThreadAttribute::ToString

傳回代表目前物件的字串。

### <a name="syntax"></a>語法

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>傳回值

表示目前物件的字串。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)