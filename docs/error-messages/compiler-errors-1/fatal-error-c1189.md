---
title: "嚴重錯誤 C1189 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1189
dev_langs: C++
helpviewer_keywords: C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2330d49f817012fc2e0381a0991f709ada74ea32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1189"></a>嚴重錯誤 C1189
\#錯誤： 使用者提供錯誤訊息  
  
 所產生 C1189`#error`指示詞。 開發人員碼指示詞指定的錯誤訊息的文字。 如需詳細資訊，請參閱[#error 指示詞 （C/c + +）](../../preprocessor/hash-error-directive-c-cpp.md)。  
  
 下列範例會產生 C1189。 在範例中，開發人員會發出自訂錯誤訊息因為`_WIN32`未定義識別項：  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 您也可能會看到這個錯誤，如果您使用建置 ATL 專案**/robust** MIDL 編譯器選項。 使用**/ 強固**參數只建置[!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)]和更新版本的 Windows。 若要更正此錯誤，請使用下列其中一個程序：  
  
-   變更 dlldatax.c 檔中的這一行：  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 變更為：  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   使用**進階**中的 屬性頁**MIDL**要移除的屬性頁面資料夾**/ 強固**切換，然後指定**/no_robust**切換。 如需詳細資訊，請參閱[MIDL 屬性頁： 進階](../../ide/midl-property-pages-advanced.md)。  
  
## <a name="see-also"></a>請參閱  
 [#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)