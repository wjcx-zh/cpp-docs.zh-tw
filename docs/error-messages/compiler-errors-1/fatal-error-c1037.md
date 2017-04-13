---
title: "嚴重錯誤 C1037 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1037
dev_langs:
- C++
helpviewer_keywords:
- C1037
ms.assetid: 79103bca-ccfb-42e7-aef9-9b90c15b162f
caps.latest.revision: 7
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
ms.openlocfilehash: 892ce10f7d19266ce45d559ce35bc82946887c52
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1037"></a>嚴重錯誤 C1037
無法開啟目的檔名稱  
  
 所指定的物件檔案[/Fo](../../build/reference/fo-object-file-name.md)無法開啟。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  無效的檔名。  
  
2.  記憶體不足，無法開啟檔案。  
  
3.  另一個處理序正在使用檔案。  
  
4.  唯讀檔具有相同的名稱。  
  
 在 Visual C++ .NET (編譯器的 1300 版) 中，有一個錯誤是檔名 (或檔名的目錄路徑) 包含 MBCS 字元時，需要正確地設定使用者地區設定。 設定系統地區設定是不夠的；必須設定使用者地區設定，才能處理 MBCS 字元。
