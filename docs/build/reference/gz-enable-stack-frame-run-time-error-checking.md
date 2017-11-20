---
title: "-GZ (啟用堆疊框架執行階段錯誤檢查) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /gz
dev_langs: C++
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f3e4dc59154d64d79db0f4d15471b51ce67bed58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (啟用堆疊框架執行階段錯誤檢查)
執行相同的作業為[/RTC （執行階段錯誤檢查）](../../build/reference/rtc-run-time-error-checks.md)選項。 已取代。  
  
## <a name="syntax"></a>語法  
  
```  
/GZ  
```  
  
## <a name="remarks"></a>備註  
 **/GZ**僅供在 clr 中的使用 ([/Od （停用 （偵錯））](../../build/reference/od-disable-debug.md)) 建置。  
  
 **/GZ**自 Visual Studio 2005; 已被取代使用[/RTC （執行階段錯誤檢查）](../../build/reference/rtc-run-time-error-checks.md)改為。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)