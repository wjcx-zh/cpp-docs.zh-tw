---
title: 連結器工具警告 LNK4224 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a051e341a22871b4229617b3958cb68dedc2921
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4224"></a>連結器工具警告 LNK4224
不再支援選項。忽略  
  
 已指定無效、 過時的連結器選項，並且忽略。  
  
 例如，如果 /comment 指示詞會出現在可能會發生 LNK4224。 obj/Comment 指示詞會有透過加入[註解 （C/c + +）](../../preprocessor/comment-c-cpp.md) pragma，使用已被取代的 exestr 選項。 使用 dumpbin [/所有](../../build/reference/all.md).obj 檔中檢視的連結器指示詞。  
  
 可能的話，請修改.obj 檔的來源，並移除 pragma。 如果您忽略這個警告，則可能導致編譯與 **/clr: pure**將不會如預期般執行。  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK4224。  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```