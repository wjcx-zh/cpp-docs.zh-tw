---
title: 編譯器警告 （層級 1） C4165 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4165
dev_langs:
- C++
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39487999f2aa74a5600d84d71917712e03b2d626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277562"
---
# <a name="compiler-warning-level-1-c4165"></a>編譯器警告 （層級 1） C4165
正在 'HRESULT' 轉換為 'bool';確定這是您想要？  
  
使用中的 HRESULT 時[如果](../../cpp/if-else-statement-cpp.md)陳述式，HRESULT 會轉換為[bool](../../cpp/bool-cpp.md)除非您明確地測試 HRESULT 的變數。 此警告預設為關閉。  
  
## <a name="example"></a>範例  
下列範例會產生 C4165  
  
```cpp  
// C4165.cpp  
// compile with: /W1  
#include <windows.h>  
#pragma warning(1:4165)  
  
extern HRESULT hr;  
int main() {  
   if (hr) {  
   // try either of the following ...  
   // if (FAILED(hr)) { // C4165 expected  
   // if (hr != S_OK) {  
   }  
}  
```