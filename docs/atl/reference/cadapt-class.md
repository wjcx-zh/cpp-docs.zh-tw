---
title: CAdapt 類別
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 2ea8fc8a26642abf593c7f4df3928ff90e66e2b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229996"
---
# <a name="cadapt-class"></a>CAdapt 類別

此範本用來包裝重新定義傳址 (address-of) 運算子的類別，以傳回物件位址以外的內容。

## <a name="syntax"></a>語法

```cpp
template <class T>
class CAdapt
```

### <a name="parameters"></a>參數

*T*<br/>
配接的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CAdapt：： operator const T&](#operator_const_t_amp)|傳回的 **`const`** 參考 `m_T` 。|
|[CAdapt：： operator T&](#operator_t_amp)|傳回 `m_T`的參考。|
|[CAdapt：： operator <](#operator_lt)|將所配接類型的物件與 `m_T` 相比較。|
|[CAdapt：： operator =](#operator_eq)|將所配接類型的物件指派給 `m_T`。|
|[CAdapt：： operator = =](#operator_eq_eq)|將所配接類型的物件與 `m_T` 相比較。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CAdapt：： m_T](#m_t)|要配接的資料。|

## <a name="remarks"></a>備註

`CAdapt` 是一個簡單的範本，用來包裝重新定義傳址運算子 (`operator &`) 的類別，以傳回物件位址以外的內容。 這些類別的範例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 類別，以及編譯器 COM 支援類別 `_com_ptr_t`。 這些類別全都會重新定義傳址運算子，以傳回其中一個資料成員的位址（在案例中為 BSTR `CComBSTR` ，而在其他類別的情況下為介面指標）。

`CAdapt`的主要角色是隱藏類別*T*所定義的傳址運算子，但仍保留改編類別的特性。 `CAdapt`藉由保存類型*t*的公用成員、 [m_T](#m_t)，以及定義轉換運算子、比較運算子和複製的函式來 fulfils 此角色，以允許將的特殊化 `CAdapt` 視為*T*類型的物件。

配接器類別 `CAdapt` 非常實用，因為某些容器樣式類別預期能夠使用傳址運算子取得其內含物件的位址。 因此，重新定義傳址運算子可能會混淆此需求，而這通常會造成編譯錯誤，並且無法使用非配接的類型搭配只要該類型「可運作」的類別。 `CAdapt` 提供了解決這些問題的方式。

通常，當您要將 `CAdapt`、`CComBSTR`、`CComPtr` 或 `CComQIPtr` 儲存在容器樣式類別中時，會使用 `_com_ptr_t`。 在支援 C++11 標準之前，這對於 C++ 標準程式庫容器而言是最常要執行的工作，不過，C++11 標準程式庫容器會自動搭配具有多載 `operator&()` 的類型運作。 標準程式庫會在內部使用[std：： addressof](../../standard-library/memory-functions.md#addressof)來取得物件的真正位址。

## <a name="requirements"></a>需求

**標頭：** atlcomcli.h。h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt::CAdapt

這些函式可讓介面卡物件預設為結構化、從調整類型的物件複製，或從另一個介面卡物件複製。

```cpp
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*.Rsrc*<br/>
要進行調整以複製到新建立之介面卡物件的類型變數。

*rSrCA*<br/>
應將包含的資料複製（或移動）至新建立之介面卡物件的介面卡物件。

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt：： m_T

保存要調整的資料。

```cpp
T m_T;
```

### <a name="remarks"></a>備註

這個 **`public`** 資料成員可以直接或間接使用[Operator const T&](#operator_const_t_amp)和[運算子 t&](#operator_t_amp)來存取。

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt：： operator const T&amp;

傳回 **`const`** [m_T](#m_t)成員的參考，讓介面卡物件被視為*T*類型的物件。

```cpp
operator const T&() const;
```

### <a name="return-value"></a>傳回值

的 **`const`** 參考 `m_T` 。

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt：： operator T&amp;

傳回[m_T](#m_t)成員的參考，讓介面卡物件被視為*T*類型的物件。

```cpp
operator T&();
```

### <a name="return-value"></a>傳回值

`m_T` 的參考。

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt：： operator&lt;

比較調整類型的物件與[m_T](#m_t)。

```cpp
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>參數

*.Rsrc*<br/>
要比較之物件的參考。

### <a name="return-value"></a>傳回值

與 .Rsrc 之間的比較結果 `m_T` 。 *rSrc*

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt：： operator =

指派運算子會將引數 *.rsrc*指派給資料成員[m_T](#m_t)並傳回目前的介面卡物件。

```cpp
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*.Rsrc*<br/>
要複製之調整型別物件的參考。

*rSrCA*<br/>
要移動之物件的參考。

### <a name="return-value"></a>傳回值

目前物件的參考。

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt：： operator = =

比較調整類型的物件與[m_T](#m_t)。

```cpp
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>參數

*.Rsrc*<br/>
要比較之物件的參考。

### <a name="return-value"></a>傳回值

*M_T*和 *.rsrc*之間的比較結果。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
