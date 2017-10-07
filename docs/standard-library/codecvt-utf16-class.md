---
title: codecvt_utf16 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt/std::codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 68b6b058d6962758a3b3e42fcde943699820fa12
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

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
