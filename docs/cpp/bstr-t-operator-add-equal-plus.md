---
title: '_bstr_t:: operator + =，+ |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a440e8b8d078c7849de2a0b29f1d50b140d70070
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044765"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=、+

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

- **operator + = (***s1***)** 在封裝中的字元附加至`BSTR`的*s1*到這個物件封裝結尾`BSTR`.

- **operator + (***s1***)** 傳回新`_bstr_t`，藉由串連此物件會形成`BSTR`與*s1*。

- **operator + (***s2***&#124;***s1***)** 傳回新`_bstr_t`，會串連起來所構成多位元組字串*s2*轉換為 Unicode，與`BSTR`中所封裝*s1*。

- **operator + (***s3* **，***s1***)** 傳回新`_bstr_t`，藉由串連 Unicode 字串格式*s3*具有`BSTR`中所封裝*s1*。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)