---
title: "-GH （啟用 _pexit 攔截函式） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _pexit
dev_langs: C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 620019d8a286fff472d6f4136bae3046556b367a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
  
 `_pexit`類似於`_penter`; 請參閱[/Gh (啟用 _penter 攔截函式)](../../build/reference/gh-enable-penter-hook-function.md)如需如何撰寫的範例`_pexit`函式。  
  
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