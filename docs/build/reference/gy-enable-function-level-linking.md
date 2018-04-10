---
title: -Gy （啟用函式階層連結） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
dev_langs:
- C++
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ebe272b12a503a310319526f53f312a033a0ee26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="gy-enable-function-level-linking"></a>/Gy (啟用函式階層連結)
允許編譯器以封裝函式 (COMDAT) 的形式來封裝個別函式。  
  
## <a name="syntax"></a>語法  
  
```  
/Gy[-]  
```  
  
## <a name="remarks"></a>備註  
 連結器需要函式個別的封裝為 Comdat 來排除或排序的 DLL 或.exe 檔案中的個別函式。  
  
 您可以使用連結器選項[/editandcontinue （最佳化）](../../build/reference/opt-optimizations.md) .exe 檔案中排除未參考的包裝函式。  
  
 您可以使用連結器選項[/ORDER （Put 函式順序）](../../build/reference/order-put-functions-in-order.md) .exe 檔案中指定的順序包含封裝函式。  
  
 如果具現化呼叫，必定封裝內嵌函式 (發生，例如，如果內嵌已關閉，或您採取函式位址)。 此外，在類別宣告中定義的 c + + 成員函式會自動封裝;其他函數則不會，並選取此選項需要將它們編譯為包裝函式。  
  
> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)選項，用於編輯後繼續 」，會自動設定**/Gy**選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**程式碼產生**屬性頁。  
  
4.  修改**函式層級啟用連結**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)