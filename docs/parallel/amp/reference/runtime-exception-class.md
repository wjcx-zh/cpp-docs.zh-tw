---
title: runtime_exception 類別
ms.date: 03/27/2019
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: ff54357055d373db98f469b071edc75fce75e0b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336789"
---
# <a name="runtime_exception-class"></a>runtime_exception 類別

C++加速大規模並行性 (AMP) 庫中異常的基本類型。

### <a name="syntax"></a>語法

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[runtime_exception建構函數](#ctor)|將 `runtime_exception` 類別的新執行個體初始化。|
|[*runtime_exception析構器](#dtor)|銷毀`runtime_exception`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_error_code](#get_error_code)|返回導致異常的錯誤代碼。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[運算子*](#operator_eq)|將指定`runtime_exception`物件的內容複製到此物件中。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`exception`

`runtime_exception`

## <a name="requirements"></a>需求

**標題:** amprt.h

**命名空間：** 並行

## <a name="runtime_exception-constructor"></a><a name="ctor"></a>runtime_exception建構函數

初始化類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
導致異常的錯誤的說明。

*_Hresult*<br/>
導致異常的錯誤的 HRESULT。

*_Other*<br/>
要複製的 `runtime_exception` 物件。

### <a name="return-value"></a>傳回值

`runtime_exception` 物件。

## <a name="runtime_exception-destructor"></a><a name="dtor"></a>*runtime_exception析構器

銷毀物件。

### <a name="syntax"></a>語法

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a><a name="get_error_code"></a>get_error_code

返回導致異常的錯誤代碼。

### <a name="syntax"></a>語法

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>傳回值

導致異常的錯誤的 HRESULT。

## <a name="operator"></a><a name="operator_eq"></a>運算子*

將指定`runtime_exception`物件的內容複製到此物件中。

### <a name="syntax"></a>語法

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的 `runtime_exception` 物件。

### <a name="return-value"></a>傳回值

對此`runtime_exception`物件的引用。

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)
