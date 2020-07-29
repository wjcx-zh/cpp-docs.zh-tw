---
title: _variant_t 擷取器
ms.date: 11/04/2016
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
ms.openlocfilehash: a1b7c713b5d82ff54250b622f2d4afe17abac468
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185602"
---
# <a name="_variant_t-extractors"></a>_variant_t 擷取器

**Microsoft 特定的**

從封裝的物件解壓縮資料 `VARIANT` 。

## <a name="syntax"></a>語法

```
operator short( ) const;
operator long( ) const;
operator float( ) const;
operator double( ) const;
operator CY( ) const;
operator _bstr_t( ) const;
operator IDispatch*( ) const;
operator bool( ) const;
operator IUnknown*( ) const;
operator DECIMAL( ) const;
operator BYTE( ) const;
operator VARIANT() const throw();
operator char() const;
operator unsigned short() const;
operator unsigned long() const;
operator int() const;
operator unsigned int() const;
operator __int64() const;
operator unsigned __int64() const;
```

## <a name="remarks"></a>備註

從封裝的中解壓縮原始資料 `VARIANT` 。 如果不 `VARIANT` 是正確的型別， `VariantChangeType` 就會用來嘗試轉換，並在失敗時產生錯誤：

- **operator short （）** 將 **`short`** 整數值解壓縮。

- **運算子 long （）** 將 **`long`** 整數值解壓縮。

- **運算子 float （）** 解壓縮 **`float`** 數值。

- **運算子 double （）** 將 **`double`** 整數值解壓縮。

- **運算子 CY （）** 解壓縮 `CY` 物件。

- **operator bool （）** 解壓縮 **`bool`** 值。

- **運算子 DECIMAL （）** 解壓縮 `DECIMAL` 值。

- **OPERATOR BYTE （）** 解壓縮 `BYTE` 值。

- **運算子 _bstr_t （）** 解壓縮字串，其封裝在 `_bstr_t` 物件中。

- **運算子 IDispatch \* （）** 會從封裝的中抽取一個分配介面指標 `VARIANT` 。 `AddRef`會在產生的指標上呼叫，因此您可以由您呼叫 `Release` 來釋放它。

- **運算子 IUnknown \* （）** 會從封裝的中，解壓縮 COM 介面指標 `VARIANT` 。 `AddRef`會在產生的指標上呼叫，因此您可以由您呼叫 `Release` 來釋放它。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
