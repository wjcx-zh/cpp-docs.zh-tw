---
title: "編譯器錯誤 C2441 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2441
dev_langs: C++
helpviewer_keywords: C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 645e06a0685f00359d468a4a4b9bd3522921b511
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2441"></a>編譯器錯誤 C2441
'variable': 以 __declspec （process） 宣告的符號必須是 const 在 /clr: pure 模式  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 根據預設，變數是每個應用程式網域下**/clr: pure**。 變數標示`__declspec(process)`下**/clr: pure**容易發生錯誤，如果在一個應用程式定義域中修改和讀取在另一個。  
  
 因此，編譯器，將每個變數是程序會強制執行`const`下**/clr: pure**，只在所有應用程式定義域中的進行這些讀取。  
  
 如需詳細資訊，請參閱[程序](../../cpp/process.md)和[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2441。  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```