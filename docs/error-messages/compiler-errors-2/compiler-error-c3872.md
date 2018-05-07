---
title: 編譯器錯誤 C3872 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3872
dev_langs:
- C++
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3259e87eb8939129ebc84c0a08acab2c7d7c509
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3872"></a>編譯器錯誤 C3872
'char'：不能在識別項中使用這個字元  
  
 C++ 編譯器會遵循 C++11 標準處理識別項中允許的字元。 識別項中只允許特定範圍的字元和通用字元名稱。 其他限制也適用於識別項的起始字元。 如需詳細資訊及允許的字元和通用字元名稱範圍清單，請參閱 [Identifiers](../../cpp/identifiers-cpp.md)。  
  
 編譯 C++/CLI 程式碼時，識別項中允許之字元範圍的限制較少。 使用 /clr 編譯之程式碼中的識別項應該遵循  [標準 ECMA-335：通用語言基礎結構 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。  
  
 下列範例會產生 C3872：  
  
```  
// C3872.cpp  
int main() {  
   int abc_\u0040;   // C3872, U+0040 is in base char set  
   int abc_\u3001;   // C3872, U+3001 is not in allowed range  
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range  
}  
```