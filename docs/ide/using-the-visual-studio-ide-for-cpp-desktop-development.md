---
title: 使用 Visual Studio IDE 進行 C++ 桌面程式開發
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 7a9559f1aac9f0bd26b35dd03729ab86ad695b04
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182768"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>使用 Visual Studio IDE 進行 C++ 桌面程式開發

Visual Studio 整合式開發環境 (IDE) 提供一組功能，可協助您管理大型和小型程式碼專案、撰寫及重構程式碼，並使用靜態分析和強大的偵錯工具來偵測及修正錯誤。 此文件集是設計來引導您完成管理專案、撰寫、測試和偵錯程式碼，然後將它部署到另一部電腦所需的每個步驟。

## <a name="prerequisites"></a>必要條件

如果您尚未安裝 Visual Studio，請立即安裝。 如需下載連結和簡略的逐步解說，請參閱[在 Visual Studio 中安裝 C++ 支援](../build/vscpp-step-0-installation.md)。 如需有關安裝 Visual Studio 的詳細資訊，以及發生問題時的疑難排解提示，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。 安裝 Visual Studio 時，請務必選擇**含有 C++ 的桌面開發**工作負載，以包含 C++ 編譯器、工具和程式庫，因為在預設情況下並未安裝。

這些逐步解說假設您已安裝 Visual Studio 和 Windows 桌面開發所需的 C++ 元件。 我們也假設您了解 C++ 語言的基本概念。 如果您需要了解 C++，有許多書籍和網路資源。 一個很好的起點是 Standard C++ Foundation 網站的 [Get Started](https://isocpp.org/get-started) (開始) 頁面。

如果您尚未安裝 Visual Studio，請立即安裝。 一般來說，即使需要使用 Visual Studio 2017 或 Visual Studio 2015 編譯器來編譯您的程式碼，我們都非常建議您使用 Visual Studio 2019。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](../porting/use-native-multi-targeting.md)。

**Visual Studio 2019 安裝**

若要取得 Visual Studio 2019，您可以從 [Visual Studio 下載](https://www.visualstudio.com/downloads/)進行下載。 當您安裝 Visual Studio 時請務必包含 C++ 開發工具，因為預設不會安裝。 如需如何安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

**Visual Studio 2017 安裝**

若要取得 Visual Studio 2017，您可以從[下載舊版 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)進行下載。 當您安裝 Visual Studio 時請務必包含 C++ 開發工具，因為預設不會安裝。 如需如何安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)，並將頁面上的版本選擇器設為 **Visual Studio 2017**。

**Visual Studio 2015 安裝**

若要安裝 Visual Studio 2015，請前往[下載舊版 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 執行安裝程式，並選擇 [自訂安裝]  ，然後選擇 C++ 元件。

一旦您的 Visual Studio 安裝完成，便可以繼續進行。

## <a name="get-started"></a>開始使用

若要開始使用 Visual Studio IDE 建置 C++ 應用程式，請依序逐一完成下列每個主題。 每個主題都建置在於先前主題中完成的工作：

- [逐步解說：使用專案和解決方案 (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [逐步解說：建置專案 (C++)](walkthrough-building-a-project-cpp.md)

- [逐步解說：測試專案 (C++)](walkthrough-testing-a-project-cpp.md)

- [逐步解說：偵錯專案 (C++)](walkthrough-debugging-a-project-cpp.md)

- [逐步解說：部署程式 (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>後續步驟

當您完成這些逐步解說之後，便可以開始建置自己的專案。 如需 C++ 開發的詳細資訊和資源，請參閱 [Visual Studio 中的 Visual C++](../overview/visual-cpp-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio Visual Studio 使用者開發入門](/visualstudio/ide/get-started-developing-with-visual-studio)