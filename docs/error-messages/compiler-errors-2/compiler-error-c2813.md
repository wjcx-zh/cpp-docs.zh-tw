---
title: "編譯器錯誤 C2813 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: 9
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: fc5f5437751abf6bcb11299e8484a199275db970
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2813"></a>編譯器錯誤 C2813
\#使用 /mp 時不支援匯入  
  
 如果您在編譯器命令中指定，就會發出 C2813 **/MP**編譯器選項和編譯，以及一或多個檔案的兩個或多個檔案包含[#import](../../preprocessor/hash-import-directive-cpp.md)前置處理器指示詞。 [#Import](../../preprocessor/hash-import-directive-cpp.md)指示詞會從指定的型別程式庫中產生 c + + 類別，然後將這些類別寫入至兩個標頭檔。 [#Import](../../preprocessor/hash-import-directive-cpp.md)指示詞不支援，因為如果多個編譯單位匯入相同的型別程式庫，這些單位衝突當他們嘗試同時寫入相同的標頭檔。  
  
 這個編譯器錯誤和**/MP**編譯器選項會在新[!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)]。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2813。 "compile with:" 註解中的命令列表示編譯器使用 **/MP** 和 **/c** 編譯器選項來編譯數個檔案。 至少其中一個檔案包含[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞。 我們為了測試這個範例使用相同的檔案兩次。  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```
