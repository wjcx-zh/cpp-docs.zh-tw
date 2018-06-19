---
title: 連結器工具錯誤 LNK1301 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b4e298ad3815c741ff6c901ac39bf7838ed135d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299701"
---
# <a name="linker-tools-error-lnk1301"></a>連結器工具錯誤 LNK1301
LTCG clr 模組找不到，/LTCG:parameter 與不相容  
  
 以 /clr 和 /GL 編譯的模組已傳遞給連結器，以及其中一個特性指引最佳化 (PGO) 參數 /LTCG。  
  
 特性指引最佳化不適用於 /clr 模組。  
  
 如需詳細資訊，請參閱:  
  
-   [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/LTCG (連結時間產生程式碼)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  以 /clr 編譯，或沒有連結一個 /LTCG PGO 參數。  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK1301:  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```