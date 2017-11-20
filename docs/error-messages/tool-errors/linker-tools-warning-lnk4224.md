---
title: "連結器工具警告 LNK4224 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4224
dev_langs: C++
helpviewer_keywords: LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cc1e54f2dbe3af96194fb6af0fae99292e49b545
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4224"></a>連結器工具警告 LNK4224
不再支援選項。忽略  
  
 已指定無效、 過時的連結器選項，並且忽略。  
  
 例如，如果 /comment 指示詞會出現在可能會發生 LNK4224。 obj/Comment 指示詞會有透過加入[註解 （C/c + +）](../../preprocessor/comment-c-cpp.md) pragma，使用已被取代的 exestr 選項。 使用 dumpbin [/所有](../../build/reference/all.md).obj 檔中檢視的連結器指示詞。  
  
 可能的話，請修改.obj 檔的來源，並移除 pragma。 如果您忽略這個警告，則可能導致編譯與**/clr: pure**將不會如預期般執行。  
  
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