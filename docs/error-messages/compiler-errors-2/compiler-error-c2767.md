---
title: "編譯器錯誤 C2767 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2767
dev_langs: C++
helpviewer_keywords: C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8fe74f9374a6fb74a514fd2655b2e1dbadf02639
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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