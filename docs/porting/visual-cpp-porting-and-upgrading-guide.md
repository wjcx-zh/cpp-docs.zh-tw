---
title: Microsoft C++移植和升級指南
description: 將 Microsoft C++程式碼升級至最新版本的 Visual Studio。
ms.date: 11/05/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: 04c3950d637c01031e78d0d95e13232143ceb232
ms.sourcegitcommit: 4dde7914608508e47c21cae03ac58fe953a0c29b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119497"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Microsoft C++移植和升級指南

本主題提供將 Microsoft C++程式碼升級至最新版本 Visual Studio 的指南。 如果您要從 Visual Studio 2008 或更早版本中建立的專案升級，您必須先使用 Visual Studio 2010 將專案轉換成 MSBuild 格式，然後在 Visual Studio 2019 中開啟專案。 針對在 Visual Studio 2010 到2015中建立的專案，只要在 Visual Studio 2019 中開啟專案。 如需完整指示，請參閱[從舊版 Visual Studio C++升級專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)。

Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 中的工具組都是二進位相容的，可讓您升級至較新版本的編譯器，而不必升級程式庫相依性。 如需詳細資訊，請參閱[ C++ 2015 和2019之間的二進位相容性](binary-compat-2015-2017.md)。

升級使用開放原始碼程式庫的專案時，或想要在多個平臺上執行時，我們建議您遷移至以 CMake 為基礎的專案。 如需詳細資訊，請參閱[Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)

## <a name="reasons-to-upgrade-c-code"></a>升級C++程式碼的理由

如果繼承應用程式在安全的環境中順利執行，而不是在進行中開發，則升級可能不會有太大的動機。 不過，如果應用程式需要進行中的維護，或是新的功能開發（包括效能或安全性改善），則您可能會考慮基於下列任何原因來升級程式碼：

- 相同的程式碼執行速度會更快，因為編譯器優化已改善。

- 現代化C++功能和程式設計實務消除了許多常見的錯誤原因，並產生比舊版 C 樣式慣用語更容易維護的程式碼。

- 由於編譯器和連結器的效能改進，組建時間會大幅加快。

- 較佳的標準一致性。 [/Permissive-](../build/reference/permissive-standards-conformance.md)編譯器選項可讓您識別 Microsoft C++編譯器先前允許但不符合目前C++標準的程式碼。

- 更好的執行時間安全性，包括更安全的[C 運行]()時間程式庫功能和編譯器功能，例如[防護檢查](../build/reference/guard-enable-guard-checks.md)和位址 sanitizers （Visual Studio 2019 版本16.4）。

## <a name="multitargeting-vs-upgrading"></a>多目標與升級的比較

如果無法選擇將您的程式碼基底升級為新的工具組，您仍然可以使用最新版本的 Visual Studio 來建立和編輯以舊版工具組和程式庫編譯的專案。 在 Visual Studio 2019 中，您可以利用下列功能：

- 新式靜態分析工具，包括C++核心指導方針檢查和 Clang，協助您找出原始程式碼中的潛在問題。

- 根據您選擇的現代化樣式自動進行格式設定，可讓舊版程式碼更容易閱讀。

如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)。

## <a name="in-this-section"></a>本節內容

|標題|描述|
|-----------|-----------------|
|[升級C++舊版 Visual Studio 的專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|如何將您的程式碼基底升級至 Visual Studio 2019 和編譯器的適用于 v142。|
|[用於升級C++程式碼的 IDE 工具](ide-tools-for-upgrading-code.md)|有助於升級程式的實用 IDE 功能。|
|[C++2015與2019之間的二進位相容性](binary-compat-2015-2017.md)|從適用于 v142 專案依來源使用 v140 程式庫。|
|[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)|搭配舊版編譯器和程式庫使用 Visual Studio 2019。|
|[Visual C++ 變更歷程記錄 2003 - 2015](visual-cpp-change-history-2003-2015.md)|Microsoft C++程式庫中的所有變更清單，以及從 Visual Studio 2003 到2015的組建工具，可能需要在您的程式碼中進行變更。|
|[從 2003 到 2015 的 Visual C++ 新功能](visual-cpp-what-s-new-2003-through-2015.md)|Microsoft C++的所有「新功能」資訊（從 Visual Studio 2003 到 Visual Studio 2015）。|
|[移植和升級：範例和案例研究](porting-and-upgrading-examples-and-case-studies.md)|在本節中，我們將移植和升級幾個範例和應用程式，並討論這些經驗和結果。 您可能發現閱讀這些內容有助於了解移植和升級程序的相關作業。 我們將在整個過程中討論升級的秘訣和訣竅，並示範如何修正特定錯誤。|
|[移植到通用 Windows 平台](porting-to-the-universal-windows-platform-cpp.md)|包含將程式碼移植到 Windows 10 的相關資訊。|
|[針對 UNIX 使用者的 Visual C++ 簡介](introduction-to-visual-cpp-for-unix-users.md)|提供資訊給剛開始使用 Visual C++，並想更有效率使用它的 UNIX 使用者。|
|[在 Windows 上執行 Linux 程式](porting-from-unix-to-win32.md)|討論將 UNIX 應用程式移轉至 Windows 的選擇。|

## <a name="see-also"></a>請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[Visual Studio 中 C++ 編譯器中的新功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual Studio 中的 C++ 一致性改善](../overview/cpp-conformance-improvements.md)<br/>
