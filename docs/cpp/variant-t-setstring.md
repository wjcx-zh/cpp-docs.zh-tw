---
title: _variant_t::SetString |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52ea719a2c9296ca1e64d881ac150994c041e206
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018726"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Microsoft 專屬**

將字串指派給這個 `_variant_t` 物件。

## <a name="syntax"></a>語法

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>參數

*pSrc*<br/>
字元字串的指標。

## <a name="remarks"></a>備註

將 ANSI 字串轉換為 Unicode `BSTR` 字串，並將它指派給這個 `_variant_t` 物件。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)