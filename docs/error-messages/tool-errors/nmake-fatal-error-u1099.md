---
title: NMAKE 嚴重錯誤 U1099 |Microsoft Docs
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
ms.openlocfilehash: f3ef75a1435d8c922087fcdd21d1941961bc82cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113379"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 嚴重錯誤 U1099

堆疊溢位

正在處理 makefile 太過複雜 NMAKE 中目前的堆疊配置的項目。 NMAKE 有 0x3000 （12 萬） 配置。

若要增加 NMAKE 的堆疊配置，請執行[editbin /stack](../../build/reference/stack.md)公用程式使用較大的堆疊選項：

**editbin /STACK:reserve NMAKE。EXE**

何處*保留*是數字大於 NMAKE 中目前的堆疊配置。