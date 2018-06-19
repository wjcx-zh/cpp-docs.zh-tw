---
title: 編譯器錯誤 C2856 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2856
dev_langs:
- C++
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac67538a10d39bc68059b0a7d1aaf73a381abb2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244129"
---
# <a name="compiler-error-c2856"></a>編譯器錯誤 C2856
\#pragma hdrstop 不可以是 #if 區塊內  
  
 `hdrstop` Pragma 不能放在條件式編譯區塊的主體內。  
  
 移動`#pragma hdrstop`陳述式，並未包含在區域`#if/#endif`區塊。