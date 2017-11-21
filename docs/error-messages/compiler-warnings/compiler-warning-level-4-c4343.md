---
title: "編譯器警告 （層級 4） C4343 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4343
dev_langs: C++
helpviewer_keywords: C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6c45c8a2a595d819ecc6eeb2eb8b69a3b5f864e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4343"></a>編譯器警告 (層級 4) C4343
\#pragma optimize("g",off) 覆寫了 /Og 選項  
  
 這個警告 (僅適用於 Itanium 處理器系列 (IPF) 編譯器) 報告 pragma [optimize](../../preprocessor/optimize.md) 已覆寫 [/Og](../../build/reference/og-global-optimizations.md) 編譯器選項。  
  
 下列範例會產生 C4343：  
  
```  
// C4343.cpp  
// compile with: /Og /W4 /LD  
// processor: IPF  
#pragma optimize ("g", off)   // C4343  
```