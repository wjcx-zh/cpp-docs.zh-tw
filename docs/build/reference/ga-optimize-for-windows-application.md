---
title: -GA （針對 Windows 應用程式最佳化） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
dev_langs:
- C++
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61bf8844a5471a97214ca6f3d3b5b473c9cd6217
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194659"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (針對 Windows 應用程式最佳化)
在執行緒區域儲存區 (TLS) 的變數存取的.exe 檔案更有效率的程式碼的結果。  
  
## <a name="syntax"></a>語法  
  
```  
/GA  
```  
  
## <a name="remarks"></a>備註  
 **/GA**速度存取資料宣告[__declspec （thread)](../../cpp/declspec.md)在以 Windows 為基礎的程式。 當設定這個選項時， [__tls_index](/windows/desktop/ProcThread/thread-local-storage)巨集假設為 0。  
  
 使用 **/GA** DLL 可能會導致錯誤的程式碼產生的。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)