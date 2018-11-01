---
title: 堆疊使用方式
ms.date: 11/04/2016
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 5ee9da50a03e1137ed6543cd349481148c9127d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452217"
---
# <a name="stack-usage"></a>堆疊使用方式

目前的 RSP 位址以外的所有記憶體會被都視為 volatile： 期間的使用者偵錯工作階段中或中斷處理常式的 OS 或偵錯工具中，可能會覆寫這個記憶體。 因此，必須一律設定 RSP，然後再嘗試讀取或寫入至堆疊框架的值。

本章節將討論的本機變數的堆疊空間配置和**alloca**內建函式。

- [堆疊配置](../build/stack-allocation.md)

- [動態參數堆疊區域建構](../build/dynamic-parameter-stack-area-construction.md)

- [函式類型](../build/function-types.md)

- [malloc 對齊](../build/malloc-alignment.md)

- [alloca](../build/alloca.md)

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)