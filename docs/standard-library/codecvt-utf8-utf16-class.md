---
title: codecvt_utf8_utf16 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fba4925b6392969aceb1c00ac4c0f4e47b3b63a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842080"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

代表[地區設定](../standard-library/locale-class.md) Facet，其可在 UTF-16 編碼的寬字元以及 UTF-8 編碼的位元組資料流之間進行轉換。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>參數

`Elem` 寬字元項目類型。
`Maxcode` 地區設定 facet 的字元數上限。
`Mode` 地區設定 facet 的組態資訊。

## <a name="remarks"></a>備註

位元組資料流可寫入二進位檔案或文字檔中。

## <a name="requirements"></a>需求

標頭：<codecvt> 命名空間：std
