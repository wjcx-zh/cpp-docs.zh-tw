---
title: NMAKE 嚴重錯誤 U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: c963180059a48d9aa0b09103df1ed54f82b8a2f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193390"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 嚴重錯誤 U1099

堆疊溢位

正在處理的 makefile 對 NMAKE 中目前的堆疊配置而言太複雜。 NMAKE 有0x3000 （12K）的配置。

若要增加 NMAKE 的堆疊配置，請使用較大的堆疊選項來執行[editbin/stack](../../build/reference/stack.md)公用程式：

**editbin/STACK：保留 NMAKE。CONVERT.EXE**

其中*reserve*是大於 NMAKE 中目前堆疊配置的數位。
