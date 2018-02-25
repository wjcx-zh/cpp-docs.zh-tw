---
title: "&lt;codecvt&gt; 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 287f25eb023d00d8cff6ce39992affa39687f721
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; 列舉
  
##  <a name="codecvt_mode"></a>  codecvt_mode 列舉  
 指定[地區設定](../standard-library/locale-class.md) Facet 的設定資訊。  
  
```  
enum codecvt_mode {  
    consume_header = 4,  
    generate_header = 2,  
    little_endian = 1  
 };  
```  
  
### <a name="remarks"></a>備註  
 列舉可定義三個常數，以提供 [\<codecvt>](../standard-library/codecvt.md) 中所宣告之地區設定 Facet 的設定資訊。 相異值如下：  
  
- `consume_header` 可在讀取多位元組序列時使用初始的標頭順序，並判斷後續多位元組序列的讀取位元組序。  
  
- `generate_header` 可在寫入多位元組序列時產生初始的標頭順序，以建議後續多位元組序列的寫入位元組序。  
  
- `little_endian` 可依位元組由小到大的順序 (而不是預設的位元組由大到小順序) 產生多位元組序列。  
  
 這些常數可以任意組合搭配使用 OR。  
  
## <a name="see-also"></a>請參閱  
 [\<codecvt>](../standard-library/codecvt.md)

