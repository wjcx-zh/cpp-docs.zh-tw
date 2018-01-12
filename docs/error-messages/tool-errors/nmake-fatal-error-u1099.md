---
title: "NMAKE 嚴重錯誤 U1099 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1099
dev_langs: C++
helpviewer_keywords: U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bf8d662960e5857686f3f8301cc8481f350d4b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 嚴重錯誤 U1099
堆疊溢位  
  
 正在處理 makefile 太過複雜目前堆疊配置 NMAKE 中的項目。 NMAKE 具有 0x3000 (12 K) 的配置。  
  
 若要增加 NMAKE 的堆疊配置，請執行[editbin /stack](../../build/reference/stack.md)公用程式使用較大的堆疊選項：  
  
 **editbin /STACK:reserve NMAKE。EXE**  
  
 其中*保留*是大於目前的堆疊配置 NMAKE 中的數字。