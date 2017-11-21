---
title: "-Qfast_transcendentals （強制快速超越函式） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Qfast_transcendentals
dev_langs: C++
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f5242621074f956c258957297bb1b220e086e70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Force Fast Transcendentals)
產生超越函式的內嵌程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
/Qfast_transcendentals  
```  
  
## <a name="remarks"></a>備註  
 這個編譯器選項會強制將超越函式轉換成內嵌程式碼，以改善執行速度。 此選項時沒有作用只能搭配**/fp： 除了**或**/fp： 精確**。 產生超越函式的內嵌程式碼已經是預設行為下的**/fp: fast**。  
  
 這個選項不相容**/fp: strict**。 請參閱[/fp （指定浮點行為）](../../build/reference/fp-specify-floating-point-behavior.md)的浮動點編譯器選項的詳細資訊。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [/Q 選項 （低階運算）](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)