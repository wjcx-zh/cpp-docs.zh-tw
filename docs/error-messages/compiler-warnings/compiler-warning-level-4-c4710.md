---
title: "編譯器警告 （層級 4） C4710 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0464d924c21a029a97a8f03d30f88127f3aea6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4710"></a>編譯器警告 (層級 4) C4710
'function': 未內嵌函式  
  
 指定的函式已選取的內嵌展開，但編譯器無法執行內嵌。  
  
 編譯器會判斷進行內嵌。 **內嵌**關鍵字、 like**註冊**關鍵字，用於做為提示編譯器。 編譯器會使用啟發學習法來判斷是否應該內嵌特定函式，以加速程式碼的速度、 進行編譯時，或應該要讓程式碼較小的空間進行編譯時的特定函式內嵌。 針對空間編譯時，編譯器將會只有內嵌非常小的函式。  
  
 在某些情況下，編譯器不會內嵌特定函式機械原因。 請參閱[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)因素編譯器內嵌函式的清單。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。