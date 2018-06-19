---
title: 命令列錯誤 D8016 |Microsoft 文件
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
ms.openlocfilehash: d6f9709da189403f2594d76751430d30554bffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300614"
---
# <a name="command-line-error-d8016"></a>命令列錯誤 D8016
'選項 1' 和 '選項 2' 的命令列選項不相容  
  
 命令列選項不能同時指定。  
  
 檢查環境變數，例如 CL，選項規格。  
  
 **/clr**意味著 **/EHa**，而且您無法指定任何其他 **/EH**編譯器選項搭配 **/clr**。 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 您可能會在更新之後，收到 D8016 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 6.0 專案： 專案更新精靈程序可能會讓 **/RTC**專案中每個原始程式碼檔，它會覆寫 **/RTC**設定專案。  若要解決，請變更 **/RTC**設定專案中每個原始程式碼檔的預設設定，這表示的專案設定 **/RTC**每個檔案將會生效。  
  
 請參閱[/RTC （執行階段錯誤檢查）](../../build/reference/rtc-run-time-error-checks.md)有關變更的資訊 **/RTC**屬性設定。