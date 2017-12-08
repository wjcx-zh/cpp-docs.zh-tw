---
title: "編譯器錯誤 C2813 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1eb1d5a0175cb151735c7799d10403cf8eac4944
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2813"></a>編譯器錯誤 C2813
\#使用 /mp 時不支援匯入  
  
 如果您在編譯器命令中指定 **/MP** 編譯器選項以及要編譯的兩個以上檔案，而且一個或多個檔案包含[#import](../../preprocessor/hash-import-directive-cpp.md) 前置處理器指示詞，則會發出 C2813。 [#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞會從所指定類型程式庫的類型中產生 C++ 類別，然後將這些類別寫入至兩個標頭檔。 不支援 [#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞，因為如果多個編譯單位匯入相同的類型程式庫，而這些單位在嘗試同時寫入相同的標頭檔時會衝突。  
  
 這個編譯器錯誤和**/MP**編譯器選項不熟悉 Visual Studio 2008 中。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2813。 "compile with:" 註解中的命令列表示編譯器使用 **/MP** 和 **/c** 編譯器選項來編譯數個檔案。 其中至少有一個檔案包含 [#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞。 我們為了測試這個範例使用相同的檔案兩次。  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```