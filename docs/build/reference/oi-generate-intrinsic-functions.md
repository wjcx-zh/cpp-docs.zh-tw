---
title: "-Oi （產生內建函式） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs: C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d0a24830dbc67466e52f3f3c488dda7ac5b4778d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (產生內建函式)
取代一些函式呼叫與內建函式或其他特殊形式的函數，可協助您的應用程式的執行速度。  
  
## <a name="syntax"></a>語法  
  
```  
/Oi[-]  
```  
  
## <a name="remarks"></a>備註  
 使用內建函式的程式速度較快，因為它們不需額外負擔函式呼叫，但是可能是因為建立額外的程式碼較大。  
  
 請參閱[內建](../../preprocessor/intrinsic.md)如有內建形式之函式的詳細資訊。  
  
 **/Oi**只要求編譯器有些函式的呼叫取代內建函式，編譯器可能會呼叫函式 （並不取代函式呼叫內建） 如果會產生較佳的效能。  
  
 **x86 特定**  
  
 內建函式的浮點函式執行不會執行任何特殊檢查輸入值和因此工作限制的輸入，範圍中，有不同的例外狀況處理和具有相同名稱的程式庫常式比界限條件。 使用真正的內建形式表示遺失 IEEE 例外狀況處理，以及遺失`_matherr`和`errno`功能; 後者表示失去 ANSI 一致性。 不過，內建形式可以顯著地加快浮點密集的程式，且許多程式，如一致性問題有很少實際值。  
  
 您可以使用[Za](../../build/reference/za-ze-disable-language-extensions.md)編譯器選項，來覆寫產生真正的內建浮點選項。 在這種情況下，函式會產生為程式庫常式，將引數直接傳遞至浮點晶片，而不是將引數推送至程式堆疊。  
  
 **結束 x86 特定**  
  
 您也使用[內建](../../preprocessor/intrinsic.md)建立內建函式，或[函式 （C/c + +）](../../preprocessor/function-c-cpp.md)明確強制執行函式呼叫。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**最佳化**屬性頁。  
  
4.  修改**啟用內建函式**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [編譯器內建](../../intrinsics/compiler-intrinsics.md)