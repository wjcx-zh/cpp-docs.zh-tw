---
title: 命令列錯誤 D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 1bdef16b14488be86aff880db7c049f4bcddcdb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196959"
---
# <a name="command-line-error-d8016"></a>命令列錯誤 D8016

' option1 ' 和 ' option2 ' 命令列選項不相容

不能同時指定命令列選項。

檢查環境變數（例如 CL）中的選項規格。

**/clr**意指 **/eha**，而且您不能使用 **/Clr**來指定任何其他 **/EH**編譯器選項。 如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md)。

更新 Visual C++ 6.0 專案之後，您可能會收到 D8016：專案更新嚮導進程可能會針對專案中的每個原始程式碼檔啟用 **/rtc** ，這會覆寫專案的 **/rtc**設定。  若要解決此問題，請將專案中每個原始程式碼檔的 **/rtc**設定變更為預設值，這表示每個檔案的 **/rtc**的專案設定都會生效。

如需變更 **/rtc**屬性設定的詳細資訊，請參閱[/Rtc （執行階段錯誤檢查）](../../build/reference/rtc-run-time-error-checks.md) 。
