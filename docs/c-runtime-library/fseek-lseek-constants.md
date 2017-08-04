---
title: "fseek, _lseek 常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
dev_langs:
- C++
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 7e0ee54703220eee179f186a6bdb1189f596c2c3
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="fseek-lseek-constants"></a>fseek, _lseek 常數
## <a name="syntax"></a>語法  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>備註  
 *origin* 引數會指定初始位置，而且可以是下列所示常數其中之一：  
  
|常數|意義|  
|--------------|-------------|  
|`SEEK_END`|檔案結尾|  
|`SEEK_CUR`|檔案指標的目前位置|  
|`SEEK_SET`|檔案開頭|  
  
## <a name="see-also"></a>另請參閱  
 [fseek、_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek、_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)   
 [全域常數](../c-runtime-library/global-constants.md)
