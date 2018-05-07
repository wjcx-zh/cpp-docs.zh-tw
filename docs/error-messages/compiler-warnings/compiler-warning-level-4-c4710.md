---
title: 編譯器警告 （層級 4） C4710 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c1cc77d8ee5393fe600ceadd9c1335d76e32efe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4710"></a>編譯器警告 (層級 4) C4710
'function': 未內嵌函式  
  
 指定的函式已選取的內嵌展開，但編譯器無法執行內嵌。  
  
 編譯器會判斷進行內嵌。 **內嵌**關鍵字、 like**註冊**關鍵字，用於做為提示編譯器。 編譯器會使用啟發學習法來判斷是否應該內嵌特定函式，以加速程式碼的速度、 進行編譯時，或應該要讓程式碼較小的空間進行編譯時的特定函式內嵌。 針對空間編譯時，編譯器將會只有內嵌非常小的函式。  
  
 在某些情況下，編譯器不會內嵌特定函式機械原因。 請參閱[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)因素編譯器內嵌函式的清單。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。