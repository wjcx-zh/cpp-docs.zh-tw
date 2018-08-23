---
title: -LN （建立 MSIL 模組） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /LN
dev_langs:
- C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca6d1933b684cc574bc4e0107b9f3f30364c908
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609458"
---
# <a name="ln-create-msil-module"></a>/LN (建立 MSIL 模組)
指定不應將組件資訊清單插入輸出檔中。  
  
## <a name="syntax"></a>語法  
  
```  
/LN  
```  
  
## <a name="remarks"></a>備註  
 根據預設， **/LN**沒有的作用 （組件資訊清單插入輸出檔）。  
  
 當 **/LN**使用時，其中[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)也必須使用的選項。  
  
 受管理的程式資訊清單中沒有組件中繼資料稱為 「 模組 」。 如果您使用編譯[/c （編譯而不連結）](../../build/reference/c-compile-without-linking.md)並 **/LN**，指定[/NOASSEMBLY （建立 MSIL 模組）](../../build/reference/noassembly-create-a-msil-module.md)在連結器階段中，若要建立輸出檔。  
  
 若要建立的模組，如果您想要建置組件時，將元件為基礎的方法。  也就是說，您可以撰寫型別，而且它們編譯成模組。  然後，您可以從一或多個模組來產生組件。  如需有關如何從模組建立組件的詳細資訊，請參閱 < [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)或是[Al.exe （組件連結器）](/dotnet/framework/tools/al-exe-assembly-linker)。  
  
 模組的預設副檔名為 .netmodule。  
  
 在 Visual c + + 2005年之前的 Visual c + + 版本中，模組以建立 **/clr:noAssembly**。  
  
 Visual C++ 連結器接受 .netmodule 檔案做為輸入，而連結器產生的輸出檔將是組件或 .netmodule (對連結器的任何輸入 .netmodule 沒有執行階段相依性)。  如需詳細資訊，請參閱 [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
-   指定[/NOASSEMBLY （建立 MSIL 模組）](../../build/reference/noassembly-create-a-msil-module.md)在連結器階段中，若要建立輸出檔。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   這個編譯器選項不能以程式設計方式變更。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)