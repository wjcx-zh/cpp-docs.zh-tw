---
title: -sdl （啟用其他安全性檢查） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
dev_langs:
- C++
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa984b488f74043b8c90876047516ebca23d4d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379532"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (啟用其他安全性檢查)
加入建議的安全性開發週期 (SDL) 檢查。 這些檢查包括額外的安全性相關警告 (視為錯誤)，以及其他安全程式碼產生功能。  
  
## <a name="syntax"></a>語法  
  
```  
/sdl[-]  
```  
  
## <a name="remarks"></a>備註  
 **/sdl**所提供的基準安全性檢查的超集，可讓[/GS](../../build/reference/gs-buffer-security-check.md)和覆寫 **/GS-**。 根據預設， **/sdl**已關閉。 **/sdl-** 停用其他安全性檢查。  
  
## <a name="compile-time-checks"></a>編譯時間檢查  
 **/sdl**可讓這些警告視為錯誤：  
  
|/sdl 啟用的警告|對應的命令列參數|描述|  
|------------------------------|-------------------------------------|-----------------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|一元減號運算子套用至不帶正負號的類型，產生不帶正負號的結果。|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|將負整數常數轉換為 unsigned 類型，產生一個可能無意義的結果。|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|使用`continue`，`break`或`goto`中的關鍵字`__finally` / `finally`區塊有未定義的行為異常終止期間。|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|初始化變數的程式碼不會執行。|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|使用了未初始化的區域變數。|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|使用了可能未初始化的本機指標變數。|  
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|當使用特定 C 執行階段 (CRT) 函式時發生緩衝區滿溢。|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|使用了函式標記為 pragma[取代](../../preprocessor/deprecated-c-cpp.md)。|  
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|使用了函式標示為[取代](../../cpp/deprecated-cpp.md)。|  
  
## <a name="runtime-checks"></a>執行階段檢查  
 當 **/sdl**已啟用，則編譯器會產生程式碼，以在執行階段執行這些檢查：  
  
-   Strict 模式可讓 **/GS**執行階段緩衝區滿溢偵測，相當於使用編譯`#pragma strict_gs_check(push, on)`。  
  
-   執行有限的指標淨化。 在未涉及取值的運算式中和沒有使用者定義解構函式的類型中，指標參考在呼叫 `delete` 之後設定為非有效位址。 這有助於防止過時的指標參考重複使用。  
  
-   執行類別成員初始化。 在物件具現化 (在建構函式執行之前)，自動將所有類別成員初始化為零。 這有助於避免使用未初始化的資料 (與建構函式未明確初始化的類別成員相關聯)。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[警告、 /sdl 和改善未初始化的變數偵測](http://go.microsoft.com/fwlink/p/?LinkId=331012)。  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +** 資料夾。  
  
3.  在**一般**頁面上，選取將選項從**SDL 檢查**下拉式清單。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)