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
ms.openlocfilehash: 685df7285e58e0cf2ceeded5ac27641364897298
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187696"
---
# <a name="_variant_t-extractors"></a>_variant_t 擷取器

**Microsoft 專屬**

從封裝的 `VARIANT` 物件中解壓縮資料。

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

從封裝的 `VARIANT`中解壓縮原始資料。 如果 `VARIANT` 還不是正確的類型，`VariantChangeType` 會用來嘗試轉換，並在失敗時產生錯誤：

- **operator short （）** 將**短**整數值解壓縮。

- **運算子 long （）** 解壓縮**長**整數值。

- **運算子 float （）** 抽取**浮點**數值。

- **運算子 double （）** 將**雙**整數值解壓縮。

- **運算子 CY （）** 解壓縮 `CY` 物件。

- **operator bool （）** 解壓縮**bool**值。

- **運算子 DECIMAL （）** 解壓縮 `DECIMAL` 值。

- **OPERATOR BYTE （）** 解壓縮 `BYTE` 值。

- **運算子 _bstr_t （）** 解壓縮字串，其封裝在 `_bstr_t` 物件中。

- **運算子 IDispatch\*（）** 從封裝的 `VARIANT`中，解壓縮一個分配介面指標。 系統會在產生的指標上呼叫 `AddRef`，因此您可以由您呼叫 `Release` 來釋放它。

- **運算子 IUnknown\*（）** 從封裝的 `VARIANT`中，解壓縮 COM 介面指標。 系統會在產生的指標上呼叫 `AddRef`，因此您可以由您呼叫 `Release` 來釋放它。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
