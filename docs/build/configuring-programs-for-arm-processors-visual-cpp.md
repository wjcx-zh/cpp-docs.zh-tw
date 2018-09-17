---
title: 適用於 ARM 處理器設定 Visual c + + |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce0e7e1f7c0936daed0fa6a51f6e254403205e0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714957"
---
# <a name="configure-visual-c-for-arm-processors"></a>適用於 ARM 處理器設定 Visual c + +

本文件的這一節包含如何使用 Visual C++ 建置工具，將 ARM 硬體做為目標。

## <a name="in-this-section"></a>本節內容

[ARM ABI 慣例概觀](../build/overview-of-arm-abi-conventions.md)描述用來暫存器使用方式，呼叫慣例和例外狀況處理在 ARM 上的 Windows 應用程式二進位介面。

[ARM64 ABI 慣例概觀](../build/arm64-windows-abi-conventions.md)描述 Windows 上 ARM64 用於暫存器使用方式，呼叫慣例和例外狀況處理的應用程式二進位介面。

[Visual c + + ARM 移轉常見問題](../build/common-visual-cpp-arm-migration-issues.md)描述 c + + 程式碼項目，通常假設為跨架構，具有可攜性，但這會產生比適用於 x86 和 x64 的 ARM 的不同的結果。

[ARM 例外狀況處理](../build/arm-exception-handling.md)描述期間在 ARM 上的 Windows 中處理結構化例外狀況的堆疊回溯的編碼配置。

[ARM64 例外狀況處理](../build/arm64-exception-handling.md)描述結構化例外狀況，在 Windows 上 ARM64 處理期間的堆疊回溯的編碼配置。

## <a name="related-sections"></a>相關章節

[ARM 內建函式](../intrinsics/arm-intrinsics.md)描述適用於使用 ARM 架構的處理器的編譯器內建函式。
