---
title: _bstr_t::operator +=、+
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: b9eddca85d66f4978e1b33299ca655cd880cf45e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181144"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=、+

**Microsoft 專屬**

將字元附加至 `_bstr_t` 物件的結尾或串連兩個字串。

## <a name="syntax"></a>語法

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>參數

*s1*<br/>
`_bstr_t` 物件。

*s2*<br/>
多位元組字串。

*s3*<br/>
Unicode 字串。

## <a name="remarks"></a>備註

這些運算子會執行字串串連：

- **operator + = （** *s1* **）** 將封裝 `BSTR`*中的字元附加至此*物件封裝 `BSTR`的結尾。

- **operator + （**  *s1*  **）** 傳回新的 `_bstr_t`，這是藉由串連這個物件的 `BSTR` 與*s1*的所形成。

- **operator + （**  *s2*  **&#124;**  *s1*  **）** 傳回新的 `_bstr_t`，這是藉由串連多位元組字元串*s2*（轉換成 Unicode），並將 `BSTR` 封裝在*s1*中所形成。

- **operator + （** *s3* **，** *s1* **）** 傳回新的 `_bstr_t`，其由串連 Unicode 字串*s3*與以*s1*封裝的 `BSTR` 形成。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
