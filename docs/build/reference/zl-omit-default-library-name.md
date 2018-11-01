---
title: /Zl (省略預設程式庫名稱)
ms.date: 11/04/2016
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: ba30efd76e94749dd261f3528535d674b5e155e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621906"
---
# <a name="zl-omit-default-library-name"></a>/Zl (省略預設程式庫名稱)

省略.obj 檔案的預設 C 執行階段程式庫名稱。 根據預設，編譯器會將程式庫名稱置入 .obj 檔案中，以將連結器導向至正確的程式庫。

## <a name="syntax"></a>語法

```
/Zl
```

## <a name="remarks"></a>備註

如需有關預設程式庫的詳細資訊，請參閱[使用執行階段程式庫](../../build/reference/md-mt-ld-use-run-time-library.md)。

您可以使用 **/Zl**來編譯您打算將放入程式庫.obj 檔案。 雖然省略的程式庫名稱儲存只有少量供單一.obj 檔案，儲存的總空間包含許多物件模組文件庫中是空間的重要。

此選項是進階的選項。 設定此選項會移除您的應用程式，導致連結時期錯誤，如果您的應用程式相依於這項支援可能需要某些 C 執行階段程式庫支援。 如果您使用此選項，您必須提供必要的元件，以其他方式。

使用[/NODEFAULTLIB （忽略程式庫）](../../build/reference/nodefaultlib-ignore-libraries.md)。 若要直接連結器忽略所有.obj 檔案中的程式庫參考。

如需詳細資訊，請參閱 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

進行編譯時 **/Zl**，`_VC_NODEFAULTLIB`定義。  例如: 

```
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**省略預設程式庫名稱**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)