---
title: '-FU (命名強制 #using 檔案) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e804aa48752d1f100e4c843fae9c0d5c70ae8b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423146"
---
# <a name="fu-name-forced-using-file"></a>/FU (命名強制的 #using 檔案)

您可以使用替代檔案將名稱傳遞給編譯器選項[#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)原始程式碼中。

## <a name="syntax"></a>語法

> **/FU** *檔案*

## <a name="arguments"></a>引數

*file*<br/>
指定要在此編譯中參考的中繼資料檔案。

## <a name="remarks"></a>備註

/FU 參數只接受一個檔名。 若要指定多個檔案，對每一個檔案都要使用 /FU。

如果您使用 C + + /cli CLI 以及參考要使用的中繼資料[Friend 組件](../../dotnet/friend-assemblies-cpp.md)功能，您無法使用 **/FU**。 您必須在程式碼中使用 `#using` (搭配使用 `[as friend]` 屬性) 來參考中繼資料。 Friend 組件不支援在 Visual c + + 元件擴充功能中 C + + /CX。

如需有關如何建立組件或模組的 common language runtime (CLR) 的資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。 如需如何建置在 C + + /CX 中，請參閱[建置應用程式和程式庫](../../cppcx/building-apps-and-libraries-c-cx.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **進階**屬性頁。

1. 修改**強制 #using**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>。

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](../../build/reference/output-file-f-options.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)