---
title: 編譯器警告 （層級 1） C4566 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4566
dev_langs:
- C++
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8044df3a37e54585f7f3b495b99314e258934f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284221"
---
# <a name="compiler-warning-level-1-c4566"></a>編譯器警告 (層級 1) C4566
通用字元名稱 'char' 所代表的字元無法在目前的字碼頁 （頁面）  
  
 並非每個 Unicode 字元可以表示您目前的 ANSI 字碼頁中。  
  
 窄字串 （單一位元組字元） 會轉換為多位元組字元，而不是寬字串 （雙位元組字元）。  
  
 下列範例會產生 C4566:  
  
```  
// C4566.cpp  
// compile with: /W1  
int main() {  
   char c1 = '\u03a0';   // C4566  
   char c2 = '\u0642';   // C4566  
  
   wchar_t c3 = L'\u03a0';   // OK  
   wchar_t c4 = L'\u0642';   // OK  
}  
```