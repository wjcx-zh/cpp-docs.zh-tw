---
title: 命令列錯誤 D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: c1e2e3e28f8556416f58d68f8ef1df4b220bc54c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399963"
---
# <a name="command-line-error-d8016"></a>命令列錯誤 D8016

'1' 和 'option2' 命令列選項不相容

命令列選項不能同時指定。

請檢查環境變數，例如 CL，選項規格。

**/clr**意味著 **/EHa**，而且您無法指定任何其他 **/EH**編譯器選項加 **/clr**。 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

您可能會接到 D8016 更新視覺效果C++6.0 的專案： 專案更新精靈程序可讓 **/RTC**專案中每個來源的程式碼檔案，其會覆寫 **/RTC**設定專案。  若要解決，請變更 **/RTC**設定的專案中每個原始程式碼檔案的預設設定，這表示的專案設定 **/RTC**每個檔案將會生效。

請參閱[/RTC （執行階段錯誤檢查）](../../build/reference/rtc-run-time-error-checks.md)有關變更的資訊 **/RTC**屬性設定。