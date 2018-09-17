---
title: 堆疊使用方式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 827a129c0b7a444cc5b48ba68a3e360712e1c08e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721535"
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