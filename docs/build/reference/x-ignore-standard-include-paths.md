---
title: -X (忽略標準 Include 路徑) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
dev_langs:
- C++
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5d246c43a1f234426b33ac640b3e1bb706d2f72
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376464"
---
# <a name="x-ignore-standard-include-paths"></a>/X (忽略標準 Include 路徑)
防止編譯器搜尋 include 檔 PATH 和 INCLUDE 環境變數中指定的目錄中。  
  
## <a name="syntax"></a>語法  
  
```  
/X  
```  
  
## <a name="remarks"></a>備註  
 您可以使用這個選項搭配[（其他 Include 目錄） /I](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) 選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**前置處理器**屬性頁。  
  
4.  修改**忽略標準 Include 路徑**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>。  
  
## <a name="example"></a>範例  
 下列命令，在`/X`告訴編譯器忽略在 PATH 和 INCLUDE 環境變數所指定的位置和`/I`指定目錄中用來尋找 include 檔：  
  
```  
CL /X /I \ALT\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)