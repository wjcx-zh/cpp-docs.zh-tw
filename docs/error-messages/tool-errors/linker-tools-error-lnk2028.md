---
title: "連結器工具錯誤 LNK2028 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2028
dev_langs: C++
helpviewer_keywords: LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7441dcd893e3e814d738f228d002a947e7f43c8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2028"></a>連結器工具錯誤 LNK2028
「 exported_function 」 (decorated_name) 參考在函數 」 function_containing_function_call 」 (decorated_name)  
  
 當嘗試以原生函式匯入純映像，請記住，隱含的呼叫慣例，原生或純編譯之間不同而有所不同。  
  
## <a name="example"></a>範例  
 此程式碼範例會產生含匯出、 原生函式的呼叫慣例是隱含的元件[__cdecl](../../cpp/cdecl.md)。  
  
```  
// LNK2028.cpp  
// compile with: /LD  
__declspec(dllexport) int func() {  
   return 3;  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會建立使用原生函式的純用戶端。 不過，下方的呼叫慣例**/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2028。  
  
```  
// LNK2028_b.cpp  
// compile with: /clr:pure lnk2028.lib  
// LNK2028 expected  
int func();  
  
int main() {  
   return func();  
}  
```