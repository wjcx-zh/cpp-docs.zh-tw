---
title: NMAKE 嚴重錯誤 U1099 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7be09691de4212d07b1452ffe33725a3978fc053
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 嚴重錯誤 U1099
堆疊溢位  
  
 正在處理 makefile 太過複雜目前堆疊配置 NMAKE 中的項目。 NMAKE 具有 0x3000 (12 K) 的配置。  
  
 若要增加 NMAKE 的堆疊配置，請執行[editbin /stack](../../build/reference/stack.md)公用程式使用較大的堆疊選項：  
  
 **editbin /STACK:reserve NMAKE。EXE**  
  
 其中*保留*是大於目前的堆疊配置 NMAKE 中的數字。