---
title: 編譯器錯誤 C2447 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2f0f72bc1278792853e1886e302f4410fdbe2d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197035"
---
# <a name="compiler-error-c2447"></a>編譯器錯誤 C2447
'{' : 遺漏函式標頭 (舊樣式型式清單？)  
  
 編譯器在全域範圍遇到未預期的左大括號。 大部分情況下，這是由格式錯誤的函式標頭、錯置的宣告或分號分隔群組所造成。 若要解決這個問題，請確認左大括號後面的正確格式的函式標頭，而且之後沒有宣告或分號分隔群組。  
  
 這項錯誤也可能是因舊式 C 語言格式引數清單而造成。 若要解決此問題，請重構引數清單以使用現代樣式，也就是用括號括住。  
  
 下列範例會產生 C2447:  
  
```  
// C2447.cpp  
int c;  
{}       // C2447  
```