---
title: Platform::ArrayReference 類別
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: e9dd16ad6c3f53c5562b0419197a582c06fbc642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354794"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference 類別

`ArrayReference` 是最佳化類型，當您想要使用輸入資料填入 C-style 陣列時，可以使用它來替代輸入參數中的 [Platform::Array^](../cppcx/platform-array-class.md) 。

## <a name="syntax"></a>語法

```cpp
class ArrayReference
```

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[陣列參考::陣列參考](#ctor)|將 `ArrayReference` 類別的新執行個體初始化。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[陣列參考::運算子() 運算子](#operator-call)|將這個 `ArrayReference` 轉換成 `Platform::Array<T>^*`。|
|[ArrayReference::operator= 運算子](#operator-assign)|將另一個 `ArrayReference` 的內容指派給這個執行個體。|

## <a name="exceptions"></a>例外狀況

### <a name="remarks"></a>備註

使用 `ArrayReference` 填滿 C-style 陣列時，可避免先複製到 `Platform::Array` 變數然後複製到 C-style 陣列時所牽涉到的額外複製作業。 當您使用 `ArrayReference`時，只會有一項複製作業。 有關代碼範例,請參閱[陣列和 WriteOnlyarray](../cppcx/array-and-writeonlyarray-c-cx.md)。

### <a name="requirements"></a>需求

**受支援的最小用戶端:** 視窗 8

**受支援的伺服器最少:** 視窗伺服器 2012

**命名空間：** Platform

**標頭：** vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a>陣列參考::數位參考建構函數

初始化平臺的新實例[::數位引用](../cppcx/platform-arrayreference-class.md)類。

### <a name="syntax"></a>語法

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>參數

*資料阿格*<br/>
陣列資料的指標。

*尺寸阿格*<br/>
來源陣列中的元素數目。

*其他阿格*<br/>
將會移動其資料來初始化新執行個體的 `ArrayReference` 物件。

### <a name="remarks"></a>備註

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a>陣列參考::運算符= 運算子

使用移動語意將指定物件分配給目前[平台::ArrayReference 物件](../cppcx/platform-arrayreference-class.md)。

### <a name="syntax"></a>語法

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>參數

*其他阿格*<br/>
移至目前 `ArrayReference` 物件的物件。

### <a name="return-value"></a>傳回值

類型為 `ArrayReference` 之物件的參考。

### <a name="remarks"></a>備註

`Platform::ArrayReference` 是標準 C++ 類別樣板，而不是 ref 類別。

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a>陣列參考::運算子() 運算子

將當前[平臺::ArrayReference](../cppcx/platform-arrayreference-class.md)物件轉換回[平臺::陣列](../cppcx/platform-array-class.md)類。

### <a name="syntax"></a>語法

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>傳回值

`Array<TArg>^` 類型之物件的控制代碼

### <a name="remarks"></a>備註

[平臺:array參照](../cppcx/platform-arrayreference-class.md)是一個標準的C++類範本,[而平臺::陣列](../cppcx/platform-array-class.md)是一個 ref 類。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
