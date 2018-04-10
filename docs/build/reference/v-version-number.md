---
title: -V （版本號碼） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a940000b5330c4eccdcabcc5a31f0c3e3e74d65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="v-version-number"></a>/V (版本號碼)
已取代。 .Obj 檔案中內嵌的文字字串。  
  
## <a name="syntax"></a>語法  
  
```  
/Vstring  
```  
  
## <a name="arguments"></a>引數  
 `string`  
 指定版本號碼或著作權聲明.obj 檔案中內嵌的字串。  
  
## <a name="remarks"></a>備註  
 Stringcan 標籤與版本號碼或著作權標示的.obj 檔案中。 如果是字串的一部分，任何空格或定位字元必須括在雙引號 （"）。 反斜線 (\\) 必須在前面任何雙引號內，如果是字串的一部分。 之間的空格**/V**和`string`是選擇性的。  
  
 您也可以使用[註解 （C/c + +）](../../preprocessor/comment-c-cpp.md)編譯器註解型別引數，編譯器的名稱和版本號碼放入.obj 檔案。  
  
 **/V**選項已被取代，開始在 Visual Studio 2005。**/V**主要是用於支援建立虛擬裝置驅動程式 (Vxd)，並建置 Vxd 已不再支援 Visual c + + 工具組。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)