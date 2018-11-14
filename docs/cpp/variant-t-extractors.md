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
ms.openlocfilehash: ab97238cf13accf3db593b5c4a81550297a53d6d
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330225"
---
# <a name="variantt-extractors"></a>_variant_t 擷取器

**Microsoft 專屬**

資料擷取封裝`VARIANT`物件。

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

從封裝擷取未經處理資料`VARIANT`。 如果`VARIANT`已經是不是適當的類型，`VariantChangeType`用來嘗試轉換，而且在失敗時產生的錯誤：

- **運算子 short （)** 擷取**簡短**整數值。

- **運算子 long （)** 擷取**長**整數值。

- **運算子 float （)** 擷取**float**數值。

- **運算子 double （)** 擷取**double**整數值。

- **運算子 CY （）** 擷取`CY`物件。

- **運算子 bool （)** 擷取**bool**值。

- **運算子 DECIMAL （）** 擷取`DECIMAL`值。

- **運算子 BYTE （）** 擷取`BYTE`值。

- **運算子 _bstr_t （)** 擷取的字串，會封裝在`_bstr_t`物件。

- **運算子 IDispatch\*（)** 從封裝擷取分配介面指標`VARIANT`。 `AddRef` 如此稱呼，是在產生的指標，它可以決定是否要呼叫`Release`釋放它。

- **運算子 IUnknown\*（)** 從封裝擷取 COM 介面指標`VARIANT`。 `AddRef` 如此稱呼，是在產生的指標，它可以決定是否要呼叫`Release`釋放它。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)