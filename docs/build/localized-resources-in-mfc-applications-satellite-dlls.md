---
title: MFC 應用程式中的當地語系化資源：附屬 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
ms.openlocfilehash: e9f9b751da6339cbe8f352bdb7eee4b7af2c359b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657991"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC 應用程式中的當地語系化資源：附屬 DLL

MFC 7.0 和更新的版本會提供附屬 Dll，此功能可協助建立當地語系化為多種語言的應用程式中的增強的支援。 附屬 dll[資源專用 DLL](../build/creating-a-resource-only-dll.md) ，其中包含特定語言的當地語系化的應用程式的資源。 當應用程式開始執行時，MFC 會自動載入當地語系化的資源最適合的環境。 例如，您可能有兩個附屬 Dll，其中包含您的資源和另一個包含德文翻譯的法文翻譯的英文語言資源的應用程式。 在英文的系統上執行應用程式時，它會使用英文的資源。 如果在法文的系統上執行，它會使用法文資源;如果在安裝德文系統上執行，它會使用德文的資源。

若要在 MFC 應用程式時，MFC 會嘗試載入附屬 DLL 中支援當地語系化的資源包含已當地語系化資源特定的語言。 附屬 Dll 會命名為*ApplicationNameXXX*.dll，其中*ApplicationName* .exe 或.dll 使用 MFC，名稱與*XXX*是語言的三個字母代碼（例如，'繁體中文' 或 'DEU'） 的資源。

MFC 會嘗試依序停止時找到下列語言版本的每個載入的資源 DLL:

1. 目前使用者的預設 UI 語言，傳回的 GetUserDefaultUILanguage() Win32 API。

1. 目前使用者的預設 UI 語言，而不需要任何特定次語言 （也就是 ENC [加拿大英文] 變成 [美國繁體中文英文]）。

1. 系統的預設 UI 語言，因為從 GetSystemDefaultUILanguage() API 傳回。 在其他平台，這是作業系統本身的語言。

1. 系統的預設 UI 語言，而不需要任何特定次語言。

1. 假的語言，與 3 個字母代碼 loc。

如果 MFC 找不到任何附屬 Dll，它會使用任何資源都包含在應用程式本身。

例如，假設應用程式 LangExample.exe 使用 MFC，並會在系統上執行多個使用者介面;系統 UI 語言為 ENU [美國英文] 和目前使用者的 UI 語言設成 FRC [加拿大法文]。 MFC 會尋找下列 Dll 順序如下：

1. LangExampleFRC.dll （使用者的 UI 語言）。

1. LangExampleFRA.dll （而不需要子語言，在此範例為法文 （法國） 使用者的 UI 語言。

1. LangExampleENU.dll （系統 UI 語言）。

1. LangExampleLOC.dll。

如果找到任何這些 Dll，MFC 會 LangExample.exe 中使用的資源。

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)<br/>
[TN057：MFC 元件的當地語系化](../mfc/tn057-localization-of-mfc-components.md)