---
title: "連結器工具警告 LNK4254 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e17bcd03f92114c1b7cd21e63220cf6372c17bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4254"></a>連結器工具警告 LNK4254
區段 'section1' （位移） 合併到 'section2' (offset) 有不同的屬性  
  
 一個區段的內容已合併到另一個，但兩個區段的屬性不同。 您的程式可能會產生非預期的結果。 例如，您想要讀取的資料可能現在只能在可寫入區段。  
  
 若要解決 LNK4254，修改或刪除合併要求。  
  
 當以 x86 為目標電腦和 Visual c + +，（ARM、 MIPS、 SH4 和縮圖） 的 Windows CE 目標。CRT 區段為唯讀。 如果您的程式碼相依於先前的行為 (。CRT 區段是讀取/寫入），您就可以看到未預期的行為。  
  
 如需詳細資訊，請參閱：  
  
-   [/MERGE （結合區段）](../../build/reference/merge-combine-sections.md)  
  
-   [comment (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK4254。  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```