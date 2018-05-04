---
title: -GH （啟用 _pexit 攔截函式） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _pexit
dev_langs:
- C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57e11c27af36eb539b22f3833a73341ff3065e97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (啟用 _pexit 攔截函式)
呼叫`_pexit`函式的每個方法或函式結尾。  
  
## <a name="syntax"></a>語法  
  
```  
/GH  
```  
  
## <a name="remarks"></a>備註  
 `_pexit`函式不是任何文件庫的一部分，並由您提供的定義`_pexit`。  
  
 除非您計劃來明確呼叫`_pexit`，您不需要提供原型。 此函式必須出現，如同它有下列的原型，和必須在項目上推入的所有暫存器內容和結束時顯示未變更的內容：  
  
```  
void __declspec(naked) _cdecl _pexit( void );  
```  
  
 `_pexit` 類似於`_penter`; 請參閱[/Gh (啟用 _penter 攔截函式)](../../build/reference/gh-enable-penter-hook-function.md)如需如何撰寫的範例`_pexit`函式。  
  
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