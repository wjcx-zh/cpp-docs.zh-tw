---
title: 編譯器錯誤 C2026 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6b2952daa8cc7b3642cca5ba278990fde7d1ebe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167661"
---
# <a name="compiler-error-c2026"></a>編譯器錯誤 C2026
字串太大，尾端字元已經截斷  
  
 字串的長度超過 16380 單一位元組字元的限制。  
  
 串連相鄰的字串之前, 的字串長度不能超過 16380 單一位元組字元。  
  
 此長度大約一半的 Unicode 字串也會產生此錯誤。  
  
 如果您有定義，如下所示的字串，它會產生 C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 您可能會破壞它，如下所示：  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 您可能想要儲存特別大的字串常值 （32k 或以上） 自訂資源或外部檔案中。 請參閱[建立新的自訂或資料資源](../../windows/creating-a-new-custom-or-data-resource.md)如需詳細資訊。