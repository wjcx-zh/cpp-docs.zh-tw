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
ms.openlocfilehash: 23544bc103de0d7b76cd73d403626ba93af6e31a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321634"
---
# <a name="cadapt-class"></a>CAdapt 類別

此範本用來包裝重新定義傳址 (address-of) 運算子的類別，以傳回物件位址以外的內容。

## <a name="syntax"></a>語法

```
template <class T>
class CAdapt
```

#### <a name="parameters"></a>參數

*T*<br/>
配接的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[適應::適應](#cadapt)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[C 適應::操作員康斯特 T&](#operator_const_t_amp)|返回對`m_T`的**const**引用。|
|[C 適應::運算子 T&](#operator_t_amp)|傳回 `m_T`的參考。|
|[C 適應::操作員<](#operator_lt)|將所配接類型的物件與 `m_T` 相比較。|
|[適應::操作員 |](#operator_eq)|將所配接類型的物件指派給 `m_T`。|
|[適應::操作員 |](#operator_eq_eq)|將所配接類型的物件與 `m_T` 相比較。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C 適應::m_T](#m_t)|要配接的資料。|

## <a name="remarks"></a>備註

`CAdapt` 是一個簡單的範本，用來包裝重新定義傳址運算子 (`operator &`) 的類別，以傳回物件位址以外的內容。 這些類別的範例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 類別，以及編譯器 COM 支援類別 `_com_ptr_t`。 這些類都重新定義了運算元的位址,以返回其一個數據成員的位址(在`CComBSTR`中為 BSTR,在其他類中為介面指標)。

`CAdapt`主要角色是隱藏*T*類定義的運算元位址,但仍保留已調整類的特徵。 `CAdapt`用持有*T*類型的`CAdapt`公共成員[(m_T),](#m_t)以及定義轉換運算符、比較運算子和複製構造函數來實現此角色,以允許將的專門化視為*T*類的物件。

配接器類別 `CAdapt` 非常實用，因為某些容器樣式類別預期能夠使用傳址運算子取得其內含物件的位址。 因此，重新定義傳址運算子可能會混淆此需求，而這通常會造成編譯錯誤，並且無法使用非配接的類型搭配只要該類型「可運作」的類別。 `CAdapt` 提供了解決這些問題的方式。

通常，當您要將 `CAdapt`、`CComBSTR`、`CComPtr` 或 `CComQIPtr` 儲存在容器樣式類別中時，會使用 `_com_ptr_t`。 在支援 C++11 標準之前，這對於 C++ 標準程式庫容器而言是最常要執行的工作，不過，C++11 標準程式庫容器會自動搭配具有多載 `operator&()` 的類型運作。 標準庫通過在內部使用[std:::地址](../../standard-library/memory-functions.md#addressof)來實現此目的,從而獲取對象的真實位址。

## <a name="requirements"></a>需求

**標題:** atlcomcli.h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>適應::適應

建構函數允許預設建構適配器物件、從已調整類型的物件複製或從其他適配器物件複製。

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*rSrc*<br/>
要複製到新構造的適配器物件的類型變數。

*rSrCA*<br/>
其包含數據的適配器物件應複製(或移動)到新構造的適配器物件。

## <a name="cadaptm_t"></a><a name="m_t"></a>C 適應::m_T

保存要調整的數據。

```
T m_T;
```

### <a name="remarks"></a>備註

此**公共**數據成員可直接或間接地與[操作員 const T&](#operator_const_t_amp)和運算符 T[&](#operator_t_amp)進行訪問。

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>C 適應::操作員孔 T&amp;

返回對[m_T](#m_t)成員的**const**引用,允許將適配器物件視為*T*類型的物件。

```
operator const T&() const;
```

### <a name="return-value"></a>傳回值

對**const**的`m_T`引用。

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>適應::運算子 T&amp;

返回對[m_T](#m_t)成員的引用,允許將適配器物件視為*T*類型的物件。

```
operator T&();
```

### <a name="return-value"></a>傳回值

`m_T` 的參考。

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>C 適應::操作員&lt;

將適應類型的物件與[m_T](#m_t)進行比較。

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>參數

*rSrc*<br/>
對要比較的物件的引用。

### <a name="return-value"></a>傳回值

和*rSrc*`m_T`之間的比較結果。

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>適應::操作員 |

賦值運算符將參數*rSrc*分配給數據成員[m_T](#m_t)並返回當前適配器物件。

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*rSrc*<br/>
對要複製的已調整類型的物件的引用。

*rSrCA*<br/>
對要移動的物件的引用。

### <a name="return-value"></a>傳回值

對當前物件的引用。

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>適應::操作員 |

將適應類型的物件與[m_T](#m_t)進行比較。

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>參數

*rSrc*<br/>
對要比較的物件的引用。

### <a name="return-value"></a>傳回值

*m_T*和*rSrc*比較的結果。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
