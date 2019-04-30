---
title: codecvt_utf8
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf8
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
ms.openlocfilehash: 3e3ddeccac2c18eedb96746f1c442c6b42349783
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405239"
---
# <a name="codecvtutf8"></a>codecvt_utf8

代表[地區設定](../standard-library/locale-class.md) Facet，其可在 UCS-2 或 UCS-4 編碼的寬字元以及 UTF-8 編碼的位元組資料流之間進行轉換。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>參數

*Elem*<br/>
寬字元項目類型。

*Maxcode*<br/>
地區設定 Facet 的最大字元數。

*模式*<br/>
地區設定 Facet 的設定資訊。

## <a name="remarks"></a>備註

位元組資料流可寫入二進位檔案或文字檔中。

## <a name="requirements"></a>需求

標頭： \<codecvt > \

命名空間： std
