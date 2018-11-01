---
title: '_bstr_t:: wchar_t *、 _bstr_t:: char*'
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
ms.openlocfilehash: da1e93a4bed195f2951e47f52bf2016cff1df3ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572938"
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t:: wchar_t *、 _bstr_t:: char*

**Microsoft 專屬**

將 BSTR 字元做為窄字元或寬字元陣列傳回。

## <a name="syntax"></a>語法

```
operator const wchar_t*( ) const throw( ); 
operator wchar_t*( ) const throw( ); 
operator const char*( ) const; 
operator char*( ) const;
```

## <a name="remarks"></a>備註

這些運算子可用來擷取 `BSTR` 物件所封裝的字元資料。 指派新值給傳回的指標並不會修改原始 BSTR 資料。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)