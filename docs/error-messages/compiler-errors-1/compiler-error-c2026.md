---
title: "編譯器錯誤 C2026 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: c429f81c64b7710b7edc2b8540d98e8c790e4062
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2026"></a>編譯器錯誤 C2026
字串太大，尾端字元已經截斷  
  
 字串的長度超過 16380 單一位元組字元的限制。  
  
 再進行串連相鄰的字串，字串長度不可超過 16380 單一位元組字元。  
  
 這個長度大約一半的 Unicode 字串也會產生此錯誤。  
  
 如果您有定義，如下所示的字串，將會產生 C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 您無法分解，如下所示︰  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 您可以自訂資源或外部檔案中儲存特別大的字串常值 （32k 以上）。 請參閱[建立新的自訂或資料資源](../../windows/creating-a-new-custom-or-data-resource.md)如需詳細資訊。
