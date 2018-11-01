---
title: Platform::STAThreadAttribute 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 9073dc6e802aa2ed6bfa4fde2a09dd8a0864687b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555649"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute 類別

指出應用程式的執行緒模型為單一執行緒 Apartment (STA)。

## <a name="syntax"></a>語法

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[STAThreadAttribute 建構函式 1](#ctor)|初始化類別的新執行個體。|

### <a name="public-methods"></a>公用方法

STAThreadAttribute 屬性繼承自[platform:: object 類別](../cppcx/platform-object-class.md)。 STAThreadAttribute 也會多載或具有下列成員：

|名稱|描述|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|判斷指定的物件是否等於目前的物件。|
|[STAThreadAttribute::GetHashCode](#gethashcode)|傳回這個執行個體的雜湊碼。|
|[STAThreadAttribute::ToString](#tostring)|傳回代表目前物件的字串。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Platform`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform

## <a name="ctor"></a> STAThreadAttribute constructor

初始化 STAThreadAttribute 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
public:STAThreadAttribute();
```

## <a name="equals"></a> STAThreadAttribute::Equals

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

## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode

傳回這個執行個體的雜湊碼。

### <a name="syntax"></a>語法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>傳回值

這個執行個體的雜湊碼。

## <a name="tostring"></a> STAThreadAttribute::ToString

傳回代表目前物件的字串。

### <a name="syntax"></a>語法

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>傳回值

表示目前物件的字串。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)