---
title: MS 為視覺工作室中的C++專案構建參考
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 96987a252d12f718025dd55deecad5c6bac26872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336205"
---
# <a name="msbuild-reference-for-c-projects"></a>C++ 專案的 MSBuild 參考

MSBuild 是 Visual Studio 中所有專案的本機構建系統,包括C++專案。 在 Visual Studio 整合式開發環境 (IDE) 中產生專案時,它會呼叫 msbuild.exe 工具,該工具又會消耗 .vcxproj 專案檔以及各種 .target 和 .props 檔。 通常,我們強烈建議使用 Visual Studio IDE 設置專案屬性並調用 MSBuild。 如果操作不正確,手動編輯專案檔可能會導致嚴重問題。

如果由於某種原因希望直接從命令行使用 MSBuild,請參閱[從命令行使用 MSBuild。](../msbuild-visual-cpp.md) 有關 MSBuild 的詳細資訊,請參閱可視化工作室文檔中的[MSBuild。](/visualstudio/msbuild/msbuild)

## <a name="in-this-section"></a>本節內容

[C++ 專案的 MSBuild 內部項目](msbuild-visual-cpp-overview.md)<br/>
有關如何存儲和使用屬性和目標的資訊。

[建置命令和屬性的一般巨集](common-macros-for-build-commands-and-properties.md)<br/>
描述可用於定義屬性(如路徑和產品版本)的宏(編譯時間常量)。

[建立 C++專案建立的檔案型態](file-types-created-for-visual-cpp-projects.md)<br/>
描述 Visual Studio 為不同的項目類型創建的各種檔。

[視覺化工作室C++專案範本](visual-cpp-project-types.md)<br>
描述可用於C++的基於MSBuild的項目類型。

[C++ 新項目範本](using-visual-cpp-add-new-item-templates.md)<br>
描述來源檔以及可以添加到 Visual Studio 專案的其他專案。

[預寫的標頭檔](../creating-precompiled-header-files.md)如何使用預編譯的標頭檔以及如何創建自己的自定義預編譯代碼以加快生成時間。

[視覺化工作室項目屬性參考](property-pages-visual-cpp.md)<br/>
在可視化工作室 IDE 中設置的專案屬性的參考文檔。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)
