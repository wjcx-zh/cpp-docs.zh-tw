---
title: /WINMD (產生 Windows 中繼資料)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 45d6492c87b7543a54d031f02dcf09e319150131
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449718"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (產生 Windows 中繼資料)

可讓產生的 Windows 執行階段中繼資料 (.winmd) 檔。

> **/WINMD**\[ **:** {**NO**\|**ONLY**}]

## <a name="arguments"></a>引數

**/WINMD**<br/>
通用 Windows 平台應用程式的預設設定。 連結器產生的二進位可執行檔和.winmd 中繼資料檔案。

**/WINMD:NO**<br/>
連結器會產生只有二進位可執行檔，但不是.winmd 檔案。

**/WINMD:ONLY**<br/>
連結器會產生只有.winmd 檔案，但不是二進位可執行檔的檔案。

## <a name="remarks"></a>備註

**/WINMD**連結器選項來控制 Windows 執行階段中繼資料 (.winmd) 檔案建立時，使用於 UWP 應用程式和 Windows 執行階段元件。 .Winmd 檔案是一種 DLL，其中包含 Windows 執行階段類型，並在執行階段元件，這些類型實作的情況下的中繼資料。 中繼資料會遵循[ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm)標準。

根據預設，輸出檔案名稱的表單*binaryname*.winmd。 若要指定不同的檔案名稱，請使用[/WINMDFILE](winmdfile-specify-winmd-file.md)選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **Windows 中繼資料**屬性頁。

1. 在 **產生 Windows 中繼資料**下拉式清單方塊中，選取您想要的選項。

## <a name="see-also"></a>另請參閱

[逐步解說：建立簡單的 Windows 執行階段元件，然後從 JavaScript 呼叫該](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[簡介 Microsoft 介面定義語言 3.0](/uwp/midl-3/intro)<br/>
[/WINMDFILE (指定 winmd 檔案)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (指定 winmd 金鑰檔)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (指定金鑰容器)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (部分簽署 winmd)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
