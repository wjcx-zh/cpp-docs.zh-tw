---
title: "&lt;memory&gt; 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 78383fb0f2fa2b8456b5c9a1b6df43ad9f6c06f3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 列舉
||  
|-|  
|[pointer_safety](#pointer_safety)|  
  
##  <a name="pointer_safety"></a>  pointer_safety 列舉  
 `get_pointer_safety` 的可能傳回值列舉。  
  
class pointer_safety { relaxed, preferred, strict };  
  
### <a name="remarks"></a>備註  
 已限定範圍的 `enum` 會定義 `get_pointer_safety()` 能傳回的值：  
  
 `relaxed` -- 以相同方式處理不是以安全方式衍生的指標 (顯然是已宣告或配置之物件的指標) 和以安全方式衍生的指標。  
  
 `preferred` -- 與先前一樣，但對於不是以安全方式衍生的指標不應取值。  
  
 `strict` -- 可能以不同方式處理不是以安全方式衍生的指標和以安全方式衍生的指標。  
  
## <a name="see-also"></a>請參閱  
 [\<memory>](../standard-library/memory.md)



