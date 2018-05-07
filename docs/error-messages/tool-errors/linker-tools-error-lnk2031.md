---
title: 連結器工具錯誤 LNK2031 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 179702b3e162ad9f22fd887d60c5a5c2d0bc8559
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2031"></a>連結器工具錯誤 LNK2031
無法產生 p/invoke，如"function_declaration"decorated_name;中繼資料中遺漏的呼叫慣例  
  
 當嘗試以原生函式匯入純映像，請記住，隱含的呼叫慣例，原生或純編譯之間不同而有所不同。 如需純映像的詳細資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 此程式碼範例會產生含匯出、 原生函式的呼叫慣例是隱含的元件[__cdecl](../../cpp/cdecl.md)。  
  
```  
// LNK2031.cpp  
// compile with: /LD  
extern "C" {  
   __declspec(dllexport) int func() { return 3; }  
};  
```  
  
## <a name="example"></a>範例  
 下列範例會建立使用原生函式的純用戶端。 不過，下方的呼叫慣例 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2031。  
  
```  
// LNK2031_b.cpp  
// compile with: /clr:pure LNK2031.lib  
// LNK2031 expected  
extern "C" int func();  
  
int main() {  
   return func();  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用純映像的原生函式。 請注意明確 **__cdecl**呼叫慣例的規範。  
  
```  
// LNK2031_c.cpp  
// compile with: /clr:pure LNK2031.lib  
extern "C" int __cdecl func();  
  
int main() {  
   return func();  
}  
```