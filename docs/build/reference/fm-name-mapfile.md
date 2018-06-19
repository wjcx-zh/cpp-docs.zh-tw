---
title: -Fm （命名對應檔） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fm
dev_langs:
- C++
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94a499b943fcd3213aa76876c65c3aac2dd79060
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374273"
---
# <a name="fm-name-mapfile"></a>/Fm (命名對應檔)
會告知連結器，以產生對應檔，其中包含對應的.exe 檔或 DLL 中的出現的順序中的區段清單。  
  
## <a name="syntax"></a>語法  
  
```  
/Fmpathname  
```  
  
## <a name="remarks"></a>備註  
 根據預設，對應檔會採用與對應 C 或 c + + 來源檔案的基底的名稱。副檔名對應。  
  
 指定 **/Fm**具有相同的效果就像您先前已指定[/MAP （產生對應檔）](../../build/reference/map-generate-mapfile.md)連結器選項。  
  
 如果您指定[/c （編譯而不連結）](../../build/reference/c-compile-without-linking.md)隱藏連結， **/Fm**沒有任何作用。  
  
 因為編譯器會加入前置底線的變數名稱，對應檔中的全域符號通常會有一或多個前置底線。 許多全域符號出現在對應檔會在內部使用，由編譯器和標準程式庫。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [輸出檔 (/ F) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)