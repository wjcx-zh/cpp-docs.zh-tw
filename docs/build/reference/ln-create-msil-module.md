---
title: "-LN （建立 MSIL 模組） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /LN
dev_langs: C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0278d59af9a62393f90a91655e3d7f0323e08118
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ln-create-msil-module"></a>/LN (建立 MSIL 模組)
指定不應將組件資訊清單插入輸出檔中。  
  
## <a name="syntax"></a>語法  
  
```  
/LN  
```  
  
## <a name="remarks"></a>備註  
 根據預設， **/LN**不在作用 （組件資訊清單插入輸出檔）。  
  
 當**/LN**使用時，其中[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)選項必須同時使用。  
  
 資訊清單中沒有組件中繼資料的 managed 的程式稱為 「 模組 」。 如果您使用編譯[/c （編譯而不連結）](../../build/reference/c-compile-without-linking.md)和**/LN**，指定[/NOASSEMBLY （建立 MSIL 模組）](../../build/reference/noassembly-create-a-msil-module.md)在連結器階段中建立輸出檔。  
  
 若要建立模組，如果您想要採取以元件為基礎的方法來建置組件。  也就是說，您可以撰寫型別，並將它們編譯成模組。  然後，您可以從一或多個模組產生的組件。  如需有關建立組件從模組的詳細資訊，請參閱[.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)或[Al.exe （組件連結器）](/dotnet/framework/tools/al-exe-assembly-linker)。  
  
 模組的預設副檔名為 .netmodule。  
  
 在[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]Visual c + + 2005年之前的版本，模組以建立**/clr:noAssembly**。  
  
 Visual C++ 連結器接受 .netmodule 檔案做為輸入，而連結器產生的輸出檔將是組件或 .netmodule (對連結器的任何輸入 .netmodule 沒有執行階段相依性)。  如需詳細資訊，請參閱 [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
-   指定[/NOASSEMBLY （建立 MSIL 模組）](../../build/reference/noassembly-create-a-msil-module.md)在連結器階段中建立輸出檔。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   無法以程式設計方式變更這個編譯器選項。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)