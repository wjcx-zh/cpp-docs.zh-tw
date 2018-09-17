---
title: -MD、-MT、-LD （使用執行階段程式庫） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
dev_langs:
- C++
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee8e59fbc88e63343d4da75a4cbf95d4f83bf815
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701359"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD、/MT、/LD (使用執行階段程式庫)

指出多執行緒模組是否為 DLL，並指定執行階段程式庫的正式版本或偵錯版本。

## <a name="syntax"></a>語法

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>備註

|選項|描述|
|------------|-----------------|
|**/MD**|讓應用程式使用多執行緒特定與 DLL 特定版本的執行階段程式庫。 定義 `_MT` 和 `_DLL`，並讓編譯器將程式庫名稱 MSVCRT.lib 放入 .obj 檔。<br /><br /> 使用這個選項編譯的應用程式，都以靜態方式連結至 MSVCRT.lib。 此程式庫提供可讓連結器解析外部參考的程式碼層。 實際的工作程式碼包含在 MSVCR*versionnumber*。DLL，必須可在執行階段與 MSVCRT.lib 連結的應用程式。|
|**/MDd**|定義 `_DEBUG`、`_MT` 和 `_DLL`，並讓應用程式使用偵錯多執行緒特定與 DLL 特定版本的執行階段程式庫。 它也會讓編譯器將程式庫名稱 MSVCRTD.lib 放入 .obj 檔中。|
|**/MT**|讓應用程式使用多執行緒、靜態版本的執行階段程式庫。 定義 `_MT`，並讓編譯器將程式庫名稱 LIBCMT.lib 置入 .obj 檔案中，讓連結器能夠使用 LIBCMT.lib 解析外部符號。|
|**/MTd**|定義 `_DEBUG` 和 `_MT`。 這個選項也會讓編譯器將程式庫名稱 LIBCMTD.lib 放入 .obj 檔中，使連結器可以使用 LIBCMTD.lib 解析外部符號。|
|**/LD**|建立 DLL。<br /><br /> 傳遞 **/DLL**連結器選項。 連結器會尋找 (並非必要) `DllMain` 函式。 如果您沒有撰寫 `DllMain` 函式，連結器將會插入一個會傳回 TRUE 的 `DllMain` 函式。<br /><br /> 連結 DLL 啟始程式碼。<br /><br /> 如果在命令列上未指定匯出 (.exp) 檔案，則會建立匯入程式庫 (.lib)。 您應將匯入程式庫連結至呼叫 DLL 的應用程式。<br /><br /> 解譯[/Fe （命名 EXE 檔案）](../../build/reference/fe-name-exe-file.md)為命名 DLL，而不是.exe 檔案。 根據預設，程式名稱會變成*basename*.dll 而不是*basename*.exe。<br /><br /> 意指 **/MT**除非您明確指定，否則 **/MD**。|
|**/LDd**|建立偵錯 DLL。 定義 `_MT` 和 `_DEBUG`。|

如需有關 C 執行階段程式庫和您使用編譯時使用的程式庫[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)，請參閱[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

傳遞至連結器中的指定引動過程的所有模組必須有使用相同的執行階段程式庫編譯器選項都編譯 (**/MD**， **/MT**， **/LD**)。

如需如何使用執行階段程式庫的偵錯版本的詳細資訊，請參閱[C 執行階段程式庫參考](../../c-runtime-library/c-run-time-library-reference.md)。

知識庫文件 Q140584 中也有關於如何選擇適當 C 執行階段程式庫的討論。

如需詳細資訊的 Dll，請參閱 < [Visual c + + Dll](../../build/dlls-in-visual-cpp.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 依序展開**C/c + +** 資料夾。

1. 選取 **程式碼產生**屬性頁。

1. 修改**執行階段程式庫**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)