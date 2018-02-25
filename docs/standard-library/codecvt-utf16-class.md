---
title: codecvt_utf16 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3d999ffc40241169dab6847e882b1994beccc1b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="codecvtutf16"></a>codecvt_utf16
代表[地區設定](../standard-library/locale-class.md) Facet，其可在 UCS-2 或 UCS-4 編碼的寬字元以及 UTF-16LE 或 UTF-16BE 編碼的位元組資料流之間進行轉換。

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```
## <a name="parameters"></a>參數
`Elem`  
寬字元項目類型。  
`Maxcode`  
地區設定 Facet 的最大字元數。  
`Mode`  
地區設定 Facet 的設定資訊。  

## <a name="remarks"></a>備註
此範本類別可在 UCS-2 或 UCS-4 編碼的寬字元以及 UTF-16LE (若為位元組由小到大模式) 或 UTF-16BE 編碼的位元組資料流之間進行轉換。

位元組資料流應寫入二進位檔案中；如果寫入文字檔案中，則可能會損毀。

## <a name="requirements"></a>需求
標頭：\<codecvt> 命名空間：std