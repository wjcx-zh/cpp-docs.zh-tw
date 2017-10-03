---
title: codecvt_utf8_utf16 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 5decc22cae5c75a32803b603836bb2f4c848327d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16
代表[地區設定](../standard-library/locale-class.md) Facet，其可在 UTF-16 編碼的寬字元以及 UTF-8 編碼的位元組資料流之間進行轉換。

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>參數

`Elem`  
寬字元項目類型。  
`Maxcode`  
地區設定 Facet 的最大字元數。  
`Mode`  
地區設定 Facet 的設定資訊。  

## <a name="remarks"></a>備註

位元組資料流可寫入二進位檔案或文字檔中。  

## <a name="requirements"></a>需求

標頭：<codecvt> 命名空間：std

