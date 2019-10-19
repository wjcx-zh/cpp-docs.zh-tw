---
title: Platform::ArrayReference 類別
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: f7e587902f1c99b294ed79255397aeffccee26b5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587915"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference 類別

`ArrayReference` 是最佳化類型，當您想要使用輸入資料填入 C-style 陣列時，可以使用它來替代輸入參數中的 [Platform::Array^](../cppcx/platform-array-class.md) 。

## <a name="syntax"></a>語法

```cpp
class ArrayReference
```

### <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|[屬性]|描述|
|----------|-----------------|
|[ArrayReference：： ArrayReference](#ctor)|初始化 `ArrayReference` 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|[屬性]|描述|
|----------|-----------------|
|[ArrayReference::operator() 運算子](#operator-call)|將這個 `ArrayReference` 轉換成 `Platform::Array<T>^*`。|
|[ArrayReference::operator= 運算子](#operator-assign)|將另一個 `ArrayReference` 的內容指派給這個執行個體。|

## <a name="exceptions"></a>例外狀況

### <a name="remarks"></a>備註

使用 `ArrayReference` 填滿 C-style 陣列時，可避免先複製到 `Platform::Array` 變數然後複製到 C-style 陣列時所牽涉到的額外複製作業。 當您使用 `ArrayReference`時，只會有一項複製作業。 如需程式碼範例，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**標頭：** vccorlib.h

## <a name="ctor"></a>ArrayReference：： ArrayReference 函式

初始化[Platform：： ArrayReference](../cppcx/platform-arrayreference-class.md)類別的新實例。

### <a name="syntax"></a>語法

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>參數

*dataArg*<br/>
陣列資料的指標。

*sizeArg*<br/>
來源陣列中的元素數目。

*otherArg*<br/>
將會移動其資料來初始化新執行個體的 `ArrayReference` 物件。

### <a name="remarks"></a>備註

## <a name="operator-assign"></a>ArrayReference：： operator = 運算子

使用 move 語義，將指定的物件指派給目前的[Platform：： ArrayReference](../cppcx/platform-arrayreference-class.md)物件。

### <a name="syntax"></a>語法

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>參數

*otherArg*<br/>
移至目前 `ArrayReference` 物件的物件。

### <a name="return-value"></a>傳回值

類型為 `ArrayReference` 之物件的參考。

### <a name="remarks"></a>備註

`Platform::ArrayReference` 是標準 C++ 類別樣板，而不是 ref 類別。

## <a name="operator-call"></a>ArrayReference：： operator （）運算子

將目前的[Platform：： ArrayReference](../cppcx/platform-arrayreference-class.md)物件轉換回[Platform：： Array](../cppcx/platform-array-class.md)類別。

### <a name="syntax"></a>語法

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>傳回值

`Array<TArg>^` 類型之物件的控制代碼

### <a name="remarks"></a>備註

[Platform：： ArrayReference](../cppcx/platform-arrayreference-class.md)是標準C++類別範本，而[platform：： Array](../cppcx/platform-array-class.md)是 ref 類別。

## <a name="see-also"></a>請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
