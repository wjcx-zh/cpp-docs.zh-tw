---
title: 編譯器錯誤 C2767 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2767
dev_langs:
- C++
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5ac628d1e02c53b0ed0872873ef23ef708df982
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234779"
---
# <a name="compiler-error-c2767"></a>編譯器錯誤 C2767
管理或 WinRTarray 維度不相符： 預期 N 引數-提供 M  
  
 Managed 或 WinRT 陣列宣告的格式錯誤。 如需詳細資訊，請參閱 [陣列](../../windows/arrays-cpp-component-extensions.md)。  
  
 下列範例會產生 C2767，並說明如何加以修正：  
  
```  
// C2767.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>(2,3); // C2767  
   array<int> ^p2 = new array<int>(2);   // OK  
}  
```