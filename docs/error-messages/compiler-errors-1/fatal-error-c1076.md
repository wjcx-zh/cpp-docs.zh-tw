---
title: 嚴重錯誤 C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: ca5117342d406983e8cba675c2589d2431d09d38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204174"
---
# <a name="fatal-error-c1076"></a>嚴重錯誤 C1076

> 編譯器限制：已達到內部堆積限制；請使用 /Zm 以指定更高的限制

這項錯誤可能會因為符號太多或樣板具現化太多而產生。 從 Visual Studio 2015 開始，這則訊息可能是由於太多平行組建程式造成的 Windows 虛擬記憶體壓力所造成。 在此情況下，除非您使用 `#pragma hdrstop` 指示詞，否則應該忽略使用 **/zm**選項的建議。

若要解決此錯誤：

1. 如果先行編譯的標頭使用 `#pragma hdrstop` 指示詞，請使用[/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)選項，將編譯器記憶體限制設定為[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)錯誤訊息中指定的值。 如需有關如何在 Visual Studio 中設定此值的詳細資訊，請參閱[/zm （指定先行編譯標頭檔的記憶體配置限制）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)中的「備註」一節。

1. 請考慮將使用 **/maxcpucount**選項指定的平行處理常式數目減少為 MSBUILD。EXE 搭配使用 **/mp**選項與 CL。CONVERT.EXE. 如需詳細資訊，請參閱先行[編譯標頭檔（PCH）問題和建議](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)。

1. 如果您是在 64 位元作業系統上使用 32 位元裝載的編譯器，請改用 64 位元裝載的編譯器。 如需詳細資訊，請參閱[如何：在命令列上啟用C++ 64 位的視覺化檢視](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)組。

1. 排除不必要的包含檔案。

1. 排除不必要的全域變數，例如動態地配置記憶體，而不宣告大型陣列。

1. 排除未使用到的宣告。

如果在組建開始之後立即發生 C1076，則為 **/zm**指定的值可能對您的程式而言太高。 減少 **/zm**值。
