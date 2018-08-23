---
title: 命令列錯誤 D8016 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c6ba57b7036aae652b9eb6d885f9105d8bf0826
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607599"
---
# <a name="command-line-error-d8016"></a>命令列錯誤 D8016
'1' 和 'option2' 命令列選項不相容  
  
 命令列選項不能同時指定。  
  
 請檢查環境變數，例如 CL，選項規格。  
  
 **/clr**意味著 **/EHa**，而且您無法指定任何其他 **/EH**編譯器選項加 **/clr**。 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 更新 Visual c + + 6.0 專案之後，您可能會取得 D8016： 專案更新精靈程序可讓 **/RTC**專案中每個來源的程式碼檔案，其會覆寫 **/RTC**專案設定。  若要解決，請變更 **/RTC**設定的專案中每個原始程式碼檔案的預設設定，這表示的專案設定 **/RTC**每個檔案將會生效。  
  
 請參閱[/RTC （執行階段錯誤檢查）](../../build/reference/rtc-run-time-error-checks.md)有關變更的資訊 **/RTC**屬性設定。