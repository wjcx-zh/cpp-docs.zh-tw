---
title: Microsoft c + + 移植與升級指南
description: 將 Microsoft c + + 程式碼升級至最新版的 Visual Studio。
ms.date: 09/10/2020
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: b6cd3461ee16a44162fdb641170a2f05d9b77369
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039530"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Microsoft c + + 移植與升級指南

本文提供將 Microsoft c + + 程式碼升級至最新版本 Visual Studio 的指南。 針對 Visual Studio 2010 至2015中所建立的專案，只需在 Visual Studio 2019 中開啟專案。 您可以使用兩個步驟升級 Visual Studio 2008 或更早版本的專案。 使用 Visual Studio 2010，先將專案轉換成 MSBuild 格式。 然後，在 Visual Studio 2019 中開啟專案。 如需完整的指示，請參閱 [升級舊版 Visual Studio 的 c + + 專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)。

Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 中的工具組都是二進位相容的。 現在您可以升級至較新版本的編譯器，而不需要升級程式庫相依性。 如需詳細資訊，請參閱 [c + + 二進位相容性 2015-2019](binary-compat-2015-2017.md)。

升級使用開放原始碼程式庫的專案，或想要在多個平臺上執行時，建議您遷移至以 CMake 為基礎的專案。 如需詳細資訊，請參閱[Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)。

## <a name="reasons-to-upgrade-c-code"></a>升級 c + + 程式碼的原因

如果繼承應用程式順利執行，在安全的環境中，而且不是在開發中，就可能不會有太多的動機需要進行升級。 不過，在這些情況下，請考慮升級：您的應用程式需要持續進行維護。 或者，您正在進行新的功能開發，或進行效能或安全性改善。 升級帶來下列優點：

- 相同的程式碼可以執行得更快，因為我們已改善編譯器優化。

- 新式 c + + 功能和程式設計實務消除了許多常見的 bug 原因，並產生比舊版 C 樣式慣用語更容易維護的程式碼。

- 由於編譯器和連結器的效能改進，組建時間更快。

- 更好的標準一致性。 [/Permissive-](../build/reference/permissive-standards-conformance.md)編譯器選項可協助您識別不符合目前 c + + 標準的程式碼。 [新的預處理器](../preprocessor/preprocessor-experimental-overview.md)也支援程式碼的一致性。

- 更好的執行時間安全性，包括更安全的 [C 運行](../c-runtime-library/security-features-in-the-crt.md) 時間程式庫功能。 此外， (Visual Studio 2019 16.4 版) 的新功能，例如 [防護檢查](../build/reference/guard-enable-guard-checks.md) 和位址 sanitizers 等編譯器功能。

## <a name="multitargeting-vs-upgrading"></a>多目標與升級

可能無法選擇將您的程式碼基底升級為新的工具組。 您仍然可以使用最新的 Visual Studio 來建立和編輯使用較舊工具組和程式庫的專案。 在 Visual Studio 2019 中，您可以利用如下的功能：

- 新式靜態分析工具（包括 C++ Core Guidelines 檢查工具和 Clang），可協助您找出原始程式碼中的潛在問題。

- 根據您選擇的新式樣式自動格式化，可協助讓舊版程式碼更容易閱讀。

如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)。

## <a name="in-this-section"></a>本節內容

|Title|描述|
|-----------|-----------------|
|[從舊版 Visual Studio 升級 c + + 專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|如何將您的程式碼基底升級為 Visual Studio 2019 和編譯器適用于 v142。|
|[用來升級 C++ 程式碼的 IDE 工具](ide-tools-for-upgrading-code.md)|有助於升級程式的實用 IDE 功能。|
|[C++ 二進位相容性 2015-2019](binary-compat-2015-2017.md)|從適用于 v142 專案依原樣使用 v140 和 v141 程式庫。|
|[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)|搭配舊版的編譯器和程式庫使用 Visual Studio 2019。|
|[Visual C++ 變更歷程記錄 2003 - 2015](visual-cpp-change-history-2003-2015.md)|Microsoft c + + 程式庫中的所有變更清單，以及從 Visual Studio 2003 到2015的組建工具，可能需要變更您的程式碼。|
|[從 2003 到 2015 的 Visual C++ 新功能](visual-cpp-what-s-new-2003-through-2015.md)|Microsoft c + + 從 Visual Studio 2003 到 Visual Studio 2015 的所有「新功能」資訊。|
|[移植和升級：範例和案例研究](porting-and-upgrading-examples-and-case-studies.md)|在本節中，我們將移植和升級幾個範例和應用程式，並討論這些經驗和結果。 這些文章讓您瞭解移植和升級程式的相關事項。 我們將在整個過程中討論升級的秘訣和訣竅，並示範如何修正特定錯誤。|
|[移植到通用 Windows 平台](porting-to-the-universal-windows-platform-cpp.md)|包含將程式碼移植到 Windows 10 的相關資訊。|
|[針對 UNIX 使用者的 Visual C++ 簡介](introduction-to-visual-cpp-for-unix-users.md)|提供資訊給剛開始使用 Visual C++，並想更有效率使用它的 UNIX 使用者。|
|[在 Windows 上執行 Linux 程式](porting-from-unix-to-win32.md)|討論將 UNIX 應用程式移轉至 Windows 的選擇。|

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[Visual Studio 中 C++ 編譯器的新功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual Studio 中的 C++ 一致性改善](../overview/cpp-conformance-improvements.md)<br/>
