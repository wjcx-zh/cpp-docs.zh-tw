---
title: /Zl (省略預設程式庫名稱)
ms.date: 11/04/2016
f1_keywords:
- /zl
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: c72377314abf755469075c7a4b431f4b8a64ee7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438630"
---
# <a name="zl-omit-default-library-name"></a>/Zl (省略預設程式庫名稱)

從 .obj 檔案中省略預設的 C 執行時間程式庫名稱。 根據預設，編譯器會將程式庫名稱置入 .obj 檔案中，以將連結器導向至正確的程式庫。

## <a name="syntax"></a>語法

```
/Zl
```

## <a name="remarks"></a>備註

如需預設程式庫的詳細資訊，請參閱[使用執行時間程式庫](md-mt-ld-use-run-time-library.md)。

您可以使用 **/zl**來編譯您打算放入程式庫中的 .obj 檔案。 雖然省略程式庫名稱只會針對單一 .obj 檔案儲存少量的空間，但在包含多個物件模組的程式庫中，儲存的總空間相當重要。

此選項是 [advanced] 選項。 設定此選項會移除應用程式可能需要的某些 C 執行時間程式庫支援，如果您的應用程式相依于這項支援，則會導致連結時錯誤。 如果您使用此選項，您必須以其他方式提供必要的元件。

使用[/NODEFAULTLIB （忽略程式庫）](nodefaultlib-ignore-libraries.md)。 指示連結器忽略所有 .obj 檔案中的程式庫參考。

如需詳細資訊，請參閱 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

使用 **/zl**進行編譯時，會定義 `_VC_NODEFAULTLIB`。  例如：

```cpp
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

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] 資料夾。

1. 按一下 [ **Advanced** ] 屬性頁。

1. 修改 [**省略預設程式庫名稱**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
