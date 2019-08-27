---
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: 879ebe6a75d76a84ef4250b95c41e02eccba5517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458649"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

代表[地區設定](../standard-library/locale-class.md) Facet，其可在 UTF-16 編碼的寬字元以及 UTF-8 編碼的位元組資料流之間進行轉換。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>參數

*Elem*\
寬字元項目類型。

*Maxcode*\
地區設定 Facet 的最大字元數。

*下*\
地區設定 Facet 的設定資訊。

## <a name="remarks"></a>備註

位元組資料流可寫入二進位檔案或文字檔中。

## <a name="requirements"></a>需求

標頭\<: codecvt >

命名空間: std
