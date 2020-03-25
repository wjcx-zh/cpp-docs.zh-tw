---
title: Visual Studio 中專案C++的 MSBuild 參考
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: ec1285a760d438a94863181a1b099e6db153c268
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168898"
---
# <a name="msbuild-reference-for-c-projects"></a>C++ 專案的 MSBuild 參考

MSBuild 是 Visual Studio 中所有專案的原生組建系統，包括C++專案。 當您在 Visual Studio 整合式開發環境（IDE）中建立專案時，它會叫用 msbuild.exe 工具，而後者會使用 .vcxproj 專案檔，以及各種 .targets 和 .props 檔案。 一般而言，我們強烈建議使用 Visual Studio IDE 來設定專案屬性和叫用 MSBuild。 如果未正確完成，手動編輯專案檔可能會導致嚴重的問題。

如果基於某些原因而想要直接從命令列使用 MSBuild，請參閱[從命令列使用 msbuild](../msbuild-visual-cpp.md)。 如需有關 MSBuild 的一般詳細資訊，請參閱 Visual Studio 檔中的[msbuild](/visualstudio/msbuild/msbuild) 。

## <a name="in-this-section"></a>本節內容

[C++ 專案的 MSBuild 內部項目](msbuild-visual-cpp-overview.md)<br/>
如何儲存和使用屬性和目標的相關資訊。

[建置命令和屬性的一般巨集](common-macros-for-build-commands-and-properties.md)<br/>
描述可以用來定義路徑和產品版本等屬性的宏（編譯時間常數）。

[為專案建立的C++檔案類型](file-types-created-for-visual-cpp-projects.md)<br/>
描述 Visual Studio 為不同的專案類型建立的各種檔案類型。

[Visual Studio C++專案範本](visual-cpp-project-types.md)<br>
描述適用于C++的 MSBuild 型專案類型。

[C++ 新項目範本](using-visual-cpp-add-new-item-templates.md)<br>
說明您可以加入至 Visual Studio 專案的來源檔案和其他專案。

先行[編譯標頭檔](../creating-precompiled-header-files.md)如何使用先行編譯標頭檔，以及如何建立您自己的自訂先行編譯器代碼，以加速組建時間。

[Visual Studio 專案屬性參考](property-pages-visual-cpp.md)<br/>
在 Visual Studio IDE 中設定之專案屬性的參考檔。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)
