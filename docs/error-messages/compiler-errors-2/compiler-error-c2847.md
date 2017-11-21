---
title: "編譯器錯誤 C2847 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2847
dev_langs: C++
helpviewer_keywords: C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8406ea786def9c3241a0ae1de8743d53e91f96cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2847"></a>編譯器錯誤 C2847
無法將 sizeof 套用於 Managed 或 WinRT 型別 'class'  
  
 [Sizeof](../../cpp/sizeof-operator.md)運算子會在編譯時期取得物件的值。 Managed 或 WinRT 型別、介面或實值型別的大小是動態的，因此無法在編譯時間得知。  
  
 例如，下列範例會產生 C2847：  
  
```  
// C2847.cpp  
// compile with: /clr  
ref class A {};  
  
int main() {  
   A ^ xA = gcnew A;  
   sizeof(*xA);   // C2847 cannot use sizeof on managed object  
}  
```  
