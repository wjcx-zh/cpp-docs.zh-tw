---
title: "編譯器警告 （層級 1） C4650 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af10d05562c0c60c6a010e105441533362d058df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4650"></a>編譯器警告 (層級 1) C4650
先行編譯標頭; 不在偵錯資訊只有全域符號標頭中的可使用  
  
 先行編譯標頭檔不是使用 Microsoft 符號偵錯資訊編譯。  
  
 當連結時，產生的可執行檔或動態連結程式庫檔案不會包含先行編譯標頭中包含的本機符號的偵錯資訊。  
  
 要避免此警告，請重新編譯使用先行編譯標頭檔[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令列選項。