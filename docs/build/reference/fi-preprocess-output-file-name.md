---
title: /Fi (前置處理輸出檔名稱)
ms.date: 08/12/2020
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 82bf09a8f01f656f90ad9971530b05f108fc95a4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561085"
---
# <a name="fi-preprocess-output-file-name"></a>`/Fi` (前置處理輸出檔的檔案名) 

指定 (前置處理[ `/P` 至檔案) ](p-preprocess-to-a-file.md)編譯器選項寫入前置處理輸出的輸出檔名稱。

## <a name="syntax"></a>語法

> **`/Fi`**_`pathname`_

### <a name="parameters"></a>參數

*`pathname`*\
編譯器選項所產生之輸出檔的相對或絕對路徑和檔案名 **`/P`** 。 或者， *`.i`* 當指定多個輸入檔時，輸出檔的目錄路徑。 請勿在選項與之間加上空格 **`/Fi`** *`pathname`* 。

## <a name="remarks"></a>備註

**`/Fi`** 搭配編譯器選項使用編譯器選項 **`/P`** 。 如果 **`/P`** 未指定， **`/Fi`** 會導致命令列警告 D9007。

如果您只指定目錄路徑 (以反斜線 **`\`**) 作為參數的路徑 *`pathname`* ，則會使用來源檔案的基底名稱作為前置處理的輸出檔案的基底名稱。 *`pathname`* 參數不需要特定的副檔名。 但是，如果您未指定副檔名，則會使用 ". i" 的副檔名。

### <a name="example"></a>範例

下列命令列前置 *`PROGRAM.cpp`* 操作、保留批註、加入指示詞 [`#line`](../../preprocessor/hash-line-directive-c-cpp.md) ，並將結果寫入至檔案 *`MYPROCESS.i`* ：

```cmd
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

此命令列會 *`main.cpp`* *`helper.cpp`* *`main.i`* *`helper.i`* 在名為 *`preprocessed`* ：

```cmd
CL /P /Fi".\\preprocessed\\" main.cpp helper.cpp
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟原始程式檔或專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **預處理器**] 屬性頁。

1. 將 [前置處理 **至檔** ] 屬性設定為 **[是]**。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. **`/Fi`** *`pathname`* 在 [**其他選項**] 方塊中，輸入編譯器選項。 設定專案的這個屬性時，只指定目錄路徑，而不是檔案名。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[`/P` (前置處理至檔案) ](p-preprocess-to-a-file.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
