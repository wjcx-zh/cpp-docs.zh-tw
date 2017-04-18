---
title: "嚴重錯誤 C1852 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: f3e2b190ed3ec30c429bded2b6b695e1838cd078
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1852"></a>嚴重錯誤 C1852
'filename' 是無效的先行編譯標頭檔  
  
 檔案不是先行編譯標頭檔。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  使用 **/Yu** 或 **#pragma hdrstop**指定的檔案無效。  
  
2.  如果您未指定副檔名，編譯器會假設副檔名為 .pch。
