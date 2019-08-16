---
title: /GA (針對 Windows 應用程式最佳化)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
ms.openlocfilehash: 85efa03a3f3d267580cbb0442839afb18ac6c313
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492858"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (針對 Windows 應用程式最佳化)

為 .exe 檔案產生更有效率的程式碼, 以存取執行緒區域儲存區 (TLS) 變數。

## <a name="syntax"></a>語法

```
/GA
```

## <a name="remarks"></a>備註

**/GA**可加速存取以 Windows 為基礎的程式中以[__declspec (thread)](../../cpp/declspec.md)宣告的資料。 設定此選項時, 會將[__tls_index](/windows/win32/ProcThread/thread-local-storage)宏假設為0。

針對 DLL 使用 **/GA**可能會導致產生錯誤的程式碼。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] 資料夾。

1. 按一下 [命令列] 屬性頁。

1. 在 [其他選項] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
