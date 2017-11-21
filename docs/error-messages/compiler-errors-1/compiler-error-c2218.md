---
title: "編譯器錯誤 C2218 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2218
dev_langs: C++
helpviewer_keywords: C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ca2e431fdfeff3c9dc957bee46f84cfd2c04162
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2218"></a>編譯器錯誤 C2218
'__vectorcall' 無法搭配 '/arch:IA32' 使用  
  
 只有在包含 Streaming SIMD Extensions 2 (SSE2) (含) 以上版本的 x86 和 x64 處理器機器碼中才支援 `__vectorcall` 呼叫慣例。 如需詳細資訊，請參閱[__vectorcall](../../cpp/vectorcall.md)。  
  
 若要修正此錯誤，請將編譯器選項變更為以 SSE2、AVX 或 AVX2 指令集為目標。 如需詳細資訊，請參閱 [/arch (x86)](../../build/reference/arch-x86.md)。