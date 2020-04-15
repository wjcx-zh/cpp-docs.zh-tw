---
title: Platform::Agile 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 0822cef10b199a5bc3b33f116065816e380bf8a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376505"
---
# <a name="platformagile-class"></a>Platform::Agile 類別

以 Agile 物件來表示具有 MashalingBehavior=Standard 的物件，可大幅降低發生執行階段執行緒例外狀況的機會。 `Agile<T>` 可讓非 Agile 物件呼叫相同或不同的執行緒，或者從中被呼叫。 有關詳細資訊,請參閱[線程和封送](../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>參數

*T*<br/>
非 Agile 類別的 typename。

### <a name="remarks"></a>備註

Windows 運行時中的大多數類都是敏捷的。 Agile 物件可以在相同或不同的執行緒中呼叫同處理序或跨處理序物件，或者從中被呼叫。 如果物件不是 Agile，請將非 Agile 物件包裝在 Agile 的 `Agile<T>` 物件中。 這樣就可以封送處理 `Agile<T>` 物件，且可以使用基礎的非 Agile 物件。

`Agile<T>` 類別是原生、標準 C++ 類別，需要 `agile.h`。 它代表非 Agile 物件和 Agile 物件的 *「內容」*(context)。 內容指定 Agile 物件的執行緒模型和封送處理行為。 作業系統使用內容來決定如何將物件封送處理。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[敏捷:敏捷](#ctor)|初始化 Agile 類別的新執行個體。|
|[Agile::~Agile 解構函式](#dtor)|終結 Agile 類別的目前執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Agile::Get](#get)|傳回目前 Agile 物件所代表的物件控制代碼。|
|[Agile::GetAddressOf](#getaddressof)|重新初始化目前 Agile 物件，然後傳回 `T`類型物件的控制代碼位址。|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|傳回目前 Agile 物件所代表的物件的控制代碼位址。|
|[Agile::Release](#release)|捨棄目前 Agile 物件的基礎物件和內容。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[敏捷::操作員->](#operator-arrow)|擷取目前 Agile 物件所代表的物件控制代碼。|
|[Agile::operator=](#operator-assign)|將指定的值指派給目前 Agile 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Object`

`Agile`

### <a name="requirements"></a>需求

**受支援的最小用戶端:** 視窗 8

**受支援的伺服器最少:** 視窗伺服器 2012

**命名空間：** Platform

**標頭：** agile.h

## <a name="agileagile-constructor"></a><a name="ctor"></a>敏捷:敏捷構造函數

初始化 Agile 類別的新執行個體。

## <a name="syntax"></a>語法

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>參數

*T*<br/>
樣板 typename 參數指定的類型。

*物件*<br/>
在此建構函式的第二個版本中，是用來初始化新 Agile 執行個體的物件。 在第三個版本中，是複製到新 Agile 執行個體的物件。 在第四個版本中，是移動到新 Agile 執行個體的物件。

### <a name="remarks"></a>備註

此建構函式的第一個版本是預設建構函式。 第二個版本從 `object` 參數指定之物件，初始化新的 Agile 執行個體類別。 第三個版本是複製建構函式。 第四個版本是移動建構函式。 這個建構函式不會擲回例外狀況。

## <a name="agileagile-destructor"></a><a name="dtor"></a>敏捷::*敏捷析構器

終結 Agile 類別的目前執行個體。

## <a name="syntax"></a>語法

```cpp
~Agile();
```

### <a name="remarks"></a>備註

此解構函式也會釋放目前 Agile 物件表示的物件。

## <a name="agileget-method"></a><a name="get"></a>敏捷:獲取方法

傳回目前 Agile 物件所代表的物件控制代碼。

## <a name="syntax"></a>語法

```cpp
T^ Get() const;
```

### <a name="return-value"></a>傳回值

目前 Agile 物件所代表的物件控制代碼。

傳回值的類型實際上是不公開的內部類型。 保存返回值的一種方便方法是將其分配給使用**自動**類型扣除關鍵字聲明的變數。 例如： `auto x = myAgileTvariable->Get();` 。

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a>敏捷::獲取方法

重新初始化目前 Agile 物件，然後傳回 `T`類型物件的控制代碼位址。

## <a name="syntax"></a>語法

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>參數

*T*<br/>
樣板 typename 參數指定的類型。

### <a name="return-value"></a>傳回值

`T` 類型物件的控制代碼位址。

### <a name="remarks"></a>備註

這個作業釋放 `T` 類型物件的目前表示 (如果有的話)、重新初始化 Agile 物件的資料成員、取得目前執行緒內容，然後傳回可以代表非 Agile 物件的物件控制代碼變數位址。 要使敏捷類實例表示物件,請使用賦值運算符[(Agile::運算符])](#operator-assign)將物件分配給敏捷類實例。

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a>敏捷::獲取forinout方法

傳回目前 Agile 物件所代表的物件的控制代碼位址。

## <a name="syntax"></a>語法

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>參數

*T*<br/>
樣板 typename 參數指定的類型。

### <a name="return-value"></a>傳回值

目前 Agile 物件所代表的物件的控制代碼位址。

### <a name="remarks"></a>備註

這個作業取得目前執行緒的內容，然後傳回基礎物件的控制代碼位址。

## <a name="agilerelease-method"></a><a name="release"></a>敏捷::發佈方法

捨棄目前 Agile 物件的基礎物件和內容。

## <a name="syntax"></a>語法

```cpp
void Release() throw();
```

### <a name="remarks"></a>備註

捨棄目前 Agile 物件的基礎物件和內容 (如果存在的話)，然後將 Agile 物件的值設為 null。

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a>敏捷::操作員-&gt;操作員

擷取目前 Agile 物件所代表的物件控制代碼。

## <a name="syntax"></a>語法

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>傳回值

目前 Agile 物件所代表的物件控制代碼。

這個運算子實際傳回保密的內部類型。 保存返回值的一種方便方法是將其分配給使用**自動**類型扣除關鍵字聲明的變數。

## <a name="agileoperator-operator"></a><a name="operator-assign"></a>敏捷::操作員+操作員

將指定的物件指派給目前 Agile 物件。

## <a name="syntax"></a>語法

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>參數

*T*<br/>
typename 樣板指定的類型。

*物件*<br/>
複製或移至目前 Agile 物件的物件或物件控制代碼。

*lp*<br/>
物件的 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

`T` 類型物件的控制代碼

### <a name="remarks"></a>備註

指派運算子的第一個版本會將參考類型的控制代碼複製到目前 Agile 物件。 第二個版本複製 Agile 類型的參考至目前 Agile 物件。 第三個版本移動 Agile 類型至目前 Agile 物件。 第四個版本移動 COM 物件的指標至目前 Agile 物件。

指派作業會自動保存目前 Agile 物件的內容。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)
