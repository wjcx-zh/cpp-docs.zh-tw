---
title: 嚴重錯誤 C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751670"
---
# <a name="fatal-error-c1076"></a>嚴重錯誤 C1076

> 編譯器限制：已達到內部堆積限制；請使用 /Zm 以指定更高的限制

這項錯誤可能會因為符號太多或樣板具現化太多而產生。 從 Visual Studio 2015 開始，此訊息可能會造成從 Windows 虛擬記憶體不足的壓力過多的平行組建程序所造成。 在此情況下，建議使用 **/Zm**應該忽略選項，除非您使用`#pragma hdrstop`指示詞。

若要解決這個錯誤：

1. 如果使用先行編譯標頭`#pragma hdrstop`指示詞時，使用[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)選項將編譯器記憶體限制設定中指定的值為[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)錯誤訊息。 如需詳細資訊，包括如何在 Visual Studio 中設定此值，請參閱 < 備註 > 一節[/Zm （指定先行編譯標頭記憶體配置上限）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。

1. 請考慮減少使用指定的平行處理序數目 **/maxcpucount** MSBUILD 的選項。搭配 EXE **/MP** CL 選項。EXE。 如需詳細資訊，請參閱 <<c0> [ 先行編譯標頭 (PCH) 問題和建議](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)。

1. 如果您是在 64 位元作業系統上使用 32 位元裝載的編譯器，請改用 64 位元裝載的編譯器。 如需詳細資訊，請參閱[如何：啟用在命令列上 64 位元 Visual c + + 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。

1. 排除不必要的包含檔案。

1. 排除不必要的全域變數，例如動態地配置記憶體，而不宣告大型陣列。

1. 排除未使用到的宣告。

如果為指定的值在建置開始之後，馬上出現 c1076 **/Zm**可能是您的程式而言太高。 減少 **/Zm**值。