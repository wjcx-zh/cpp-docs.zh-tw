---
title: codecvt_utf8_utf16 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0d3df3a6d9727722758f6af8b1dae2619b6bd0c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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
