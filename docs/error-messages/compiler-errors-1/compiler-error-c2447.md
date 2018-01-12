---
title: "編譯器錯誤 C2447 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2447
dev_langs: C++
helpviewer_keywords: C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30c8195467b9cf287ba9f7220555d903ba51c164
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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