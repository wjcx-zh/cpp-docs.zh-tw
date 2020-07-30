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
ms.openlocfilehash: 839002a614b54990fdc9180fa06737ff43039a4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226930"
---
# <a name="platformagile-class"></a>Platform::Agile 類別

以 Agile 物件來表示具有 MashalingBehavior=Standard 的物件，可大幅降低發生執行階段執行緒例外狀況的機會。 `Agile<T>` 可讓非 Agile 物件呼叫相同或不同的執行緒，或者從中被呼叫。 如需詳細資訊，請參閱[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>參數

*T*<br/>
非 Agile 類別的 typename。

### <a name="remarks"></a>備註

Windows 執行階段中的大部分類別都是 agile。 Agile 物件可以在相同或不同的執行緒中呼叫同處理序或跨處理序物件，或者從中被呼叫。 如果物件不是 Agile，請將非 Agile 物件包裝在 Agile 的 `Agile<T>` 物件中。 這樣就可以封送處理 `Agile<T>` 物件，且可以使用基礎的非 Agile 物件。

`Agile<T>` 類別是原生、標準 C++ 類別，需要 `agile.h`。 它代表非 Agile 物件和 Agile 物件的 *「內容」*(context)。 內容指定 Agile 物件的執行緒模型和封送處理行為。 作業系統使用內容來決定如何將物件封送處理。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[Agile：： Agile](#ctor)|初始化 Agile 類別的新執行個體。|
|[Agile::~Agile 解構函式](#dtor)|終結 Agile 類別的目前執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[Agile::Get](#get)|傳回目前 Agile 物件所代表的物件控制代碼。|
|[Agile::GetAddressOf](#getaddressof)|重新初始化目前 Agile 物件，然後傳回 `T`類型物件的控制代碼位址。|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|傳回目前 Agile 物件所代表的物件的控制代碼位址。|
|[Agile::Release](#release)|捨棄目前 Agile 物件的基礎物件和內容。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[Agile：： operator->](#operator-arrow)|擷取目前 Agile 物件所代表的物件控制代碼。|
|[Agile::operator=](#operator-assign)|將指定的值指派給目前 Agile 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Object`

`Agile`

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**標頭：** agile.h

## <a name="agileagile-constructor"></a><a name="ctor"></a>Agile：： Agile 函數

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

*object*<br/>
在此建構函式的第二個版本中，是用來初始化新 Agile 執行個體的物件。 在第三個版本中，是複製到新 Agile 執行個體的物件。 在第四個版本中，是移動到新 Agile 執行個體的物件。

### <a name="remarks"></a>備註

此建構函式的第一個版本是預設建構函式。 第二個版本從 `object` 參數指定之物件，初始化新的 Agile 執行個體類別。 第三個版本是複製建構函式。 第四個版本是移動建構函式。 這個建構函式不會擲回例外狀況。

## <a name="agileagile-destructor"></a><a name="dtor"></a>Agile：： ~ Agile 析構函式

終結 Agile 類別的目前執行個體。

## <a name="syntax"></a>語法

```cpp
~Agile();
```

### <a name="remarks"></a>備註

此解構函式也會釋放目前 Agile 物件表示的物件。

## <a name="agileget-method"></a><a name="get"></a>Agile：： Get 方法

傳回目前 Agile 物件所代表的物件控制代碼。

## <a name="syntax"></a>語法

```cpp
T^ Get() const;
```

### <a name="return-value"></a>傳回值

目前 Agile 物件所代表的物件控制代碼。

傳回值的類型實際上是不公開的內部類型。 保存傳回值的便利方式是將它指派給使用類型推算關鍵字所宣告的變數 **`auto`** 。 例如： `auto x = myAgileTvariable->Get();` 。

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a>Agile：： GetAddressOf 方法

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

這個作業釋放 `T` 類型物件的目前表示 (如果有的話)、重新初始化 Agile 物件的資料成員、取得目前執行緒內容，然後傳回可以代表非 Agile 物件的物件控制代碼變數位址。 若要讓 Agile 類別實例代表物件，請使用指派運算子（[agile：： operator =](#operator-assign)）將物件指派給 Agile 類別實例。

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a>Agile：： GetAddressOfForInOut 方法

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

## <a name="agilerelease-method"></a><a name="release"></a>Agile：： Release 方法

捨棄目前 Agile 物件的基礎物件和內容。

## <a name="syntax"></a>語法

```cpp
void Release() throw();
```

### <a name="remarks"></a>備註

捨棄目前 Agile 物件的基礎物件和內容 (如果存在的話)，然後將 Agile 物件的值設為 null。

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a>Agile：： operator- &gt; 運算子

擷取目前 Agile 物件所代表的物件控制代碼。

## <a name="syntax"></a>語法

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>傳回值

目前 Agile 物件所代表的物件控制代碼。

這個運算子實際傳回保密的內部類型。 保存傳回值的便利方式是將它指派給使用類型推算關鍵字所宣告的變數 **`auto`** 。

## <a name="agileoperator-operator"></a><a name="operator-assign"></a>Agile：： operator = 運算子

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

*object*<br/>
複製或移至目前 Agile 物件的物件或物件控制代碼。

*lp*<br/>
物件的 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

`T` 類型物件的控制代碼

### <a name="remarks"></a>備註

指派運算子的第一個版本會將參考類型的控制代碼複製到目前 Agile 物件。 第二個版本複製 Agile 類型的參考至目前 Agile 物件。 第三個版本移動 Agile 類型至目前 Agile 物件。 第四個版本移動 COM 物件的指標至目前 Agile 物件。

指派作業會自動保存目前 Agile 物件的內容。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)
