---
title: MSBuild 參考C++Visual Studio 中的專案
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: b6ec6b5d276cb7104cf61c229476596d2a2a7684
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024695"
---
# <a name="msbuild-reference-for-c-projects"></a>MSBuild 參考C++專案

MSBuild 是在 Visual Studio 中的所有專案的原生組建系統包括C++專案。 當您建置 Visual Studio 整合式的開發環境 (IDE) 中的專案時，它會叫用 msbuild.exe 工具，這接著會取用.vcxproj 專案檔和各種.targets 和.props 檔案。 一般情況下，我們強烈建議使用 Visual Studio IDE 來設定專案屬性，並叫用 MSBuild。 如果未正確完成手動編輯專案檔會造成嚴重的問題。

如果基於某些原因，您想要直接從命令列使用 MSBuild，請參閱[從命令列使用的 MSBuild](../msbuild-visual-cpp.md)。 如需 MSBuild 的詳細資訊在一般情況下，請參閱[MSBuild](/visualstudio/msbuild/msbuild) Visual Studio 文件中。

## <a name="in-this-section"></a>本節內容

[C++ 專案的 MSBuild 內部項目](msbuild-visual-cpp-overview.md)<br/>
如何屬性和目標儲存和取用的相關資訊。

[建置命令和屬性的一般巨集](common-macros-for-build-commands-and-properties.md)<br/>
描述可用來定義屬性，例如路徑和產品版本的巨集 （編譯時期常數）。

[檔案類型建立C++專案](file-types-created-for-visual-cpp-projects.md)<br/>
描述各種不同的專案類型，Visual Studio 會建立檔案。

[Visual StudioC++專案範本](visual-cpp-project-types.md)<br>
描述 MSBuild 型專案類型可供C++。

[C++ 新項目範本](using-visual-cpp-add-new-item-templates.md)<br>
描述原始程式檔和其他項目，您可以加入 Visual Studio 專案。

[先行編譯標頭檔](../creating-precompiled-header-files.md)如何使用先行編譯標頭檔，以及如何建立您自己自訂的先行編譯程式碼，以加速建置時間。

[Visual Studio 專案屬性參考](property-pages-visual-cpp.md)<br/>
在 Visual Studio IDE 中設定的專案屬性的參考文件。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)