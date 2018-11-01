---
title: NMAKE 嚴重錯誤 U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631214"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 嚴重錯誤 U1099

堆疊溢位

正在處理 makefile 太過複雜 NMAKE 中目前的堆疊配置的項目。 NMAKE 有 0x3000 （12 萬） 配置。

若要增加 NMAKE 的堆疊配置，請執行[editbin /stack](../../build/reference/stack.md)公用程式使用較大的堆疊選項：

**editbin /STACK:reserve NMAKE。EXE**

何處*保留*是數字大於 NMAKE 中目前的堆疊配置。