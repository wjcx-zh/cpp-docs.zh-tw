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
ms.openlocfilehash: fbdf882367deb34570dd5b5ebb1b4001be739297
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373853"
---
# <a name="configure-visual-c-for-arm-processors"></a>適用於 ARM 處理器設定 Visual c + +

本文件的這一節包含如何使用 Visual C++ 建置工具，將 ARM 硬體做為目標。

## <a name="in-this-section"></a>本節內容

[ARM ABI 慣例概觀](../build/overview-of-arm-abi-conventions.md)<br/>
描述由 Windows on ARM 用於暫存器使用方式的應用程式二進位介面，呼叫慣例和例外狀況處理。

[ARM64 ABI 慣例概觀](../build/arm64-windows-abi-conventions.md)<br/>
描述 Windows 上 ARM64 用於暫存器使用方式，呼叫慣例和例外狀況處理的應用程式二進位介面。

[Visual C++ ARM 移轉時常見的問題](../build/common-visual-cpp-arm-migration-issues.md)<br/>
描述通常假定可跨架構移植的 C++ 程式碼項目，但其會針對 ARM 與 x86 和 x64 產生不同的結果。

[ARM 例外狀況處理](../build/arm-exception-handling.md)<br/>
描述在 Windows on ARM 中處理結構化例外狀況期間，堆疊回溯的編碼配置。

[ARM64 例外狀況處理。](../build/arm64-exception-handling.md)<br/>
描述在 ARM64 上的 Windows 中的結構化例外狀況處理期間的堆疊回溯的編碼配置。

## <a name="related-sections"></a>相關章節

[ARM 內建](../intrinsics/arm-intrinsics.md)<br/>
描述使用 ARM 架構之處理器的編譯器內建功能。
