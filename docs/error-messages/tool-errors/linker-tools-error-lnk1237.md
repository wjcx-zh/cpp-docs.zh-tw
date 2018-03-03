---
title: "連結器工具錯誤 LNK1237 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee9ec0e197d51f76ff57ef06f5584c55df0a4746
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1237"></a>連結器工具錯誤 LNK1237
程式碼在產生期間，編譯器引入了符號 'symbol' 'module' 以 /GL 編譯的模組中定義的參考  
  
 程式碼產生期間，編譯器不應該引入解析定義編譯的符號**/GL**。 `symbol`是一種符號，已引進，而且稍後將解析成定義，以編譯**/GL**。  
  
 如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。  
  
 若要解決 LNK1237，未編譯的符號寬度**/GL**或使用[/INCLUDE （強制符號參考）](../../build/reference/include-force-symbol-references.md)強制符號參考。  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK1237。 若要解決這個錯誤，未初始化陣列 LNK1237_a.cpp 中的作業，並新增**/include: __chkstk**連結命令。  
  
```  
// LNK1237_a.cpp  
int main() {  
   char c[5000] = {0};  
}  
```  
  
```  
// LNK1237_b.cpp  
// compile with: /GS- /GL /c LNK1237_a.cpp  
// processor: x86  
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)  
extern "C" void _chkstk(size_t s) {}  
```