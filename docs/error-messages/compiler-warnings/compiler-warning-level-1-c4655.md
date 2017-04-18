---
title: "編譯器警告 （層級 1） C4655 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4655
dev_langs:
- C++
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
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
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 058086bb4617f59f53de706b38477bd868e297d3
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4655"></a>編譯器警告 (層級 1) C4655
**'**   
 ***符號*': 變數型別是新自從上次建置，或以不同的方式在其他地方定義**  
  
 自從上次成功組建後，您已變更或加入新的資料類型。 [編輯後繼續] 不支援對現有資料類型的變更。  
  
 這個警告後面[嚴重錯誤 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 如需詳細資訊，請參閱[支援的程式碼變更](/visualstudio/debugger/supported-code-changes-cpp)。  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>移除這個警告，而不結束目前的偵錯工作階段  
  
1.  請將資料類型改回錯誤之前的狀態。  
  
2.  從 [偵錯]  功能表選擇 [套用程式碼變更] 。  
  
### <a name="to-remove-this-warning-without-changing-your-source-code"></a>移除這個警告，而不變更您的程式碼  
  
1.  從 [偵錯]  功能表選擇 [停止偵錯] 。  
  
2.  從 [建置]  功能表選擇 [建置] 。
