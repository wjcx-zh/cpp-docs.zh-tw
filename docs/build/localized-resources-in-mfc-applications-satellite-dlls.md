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
ms.openlocfilehash: 1f512cc17832564b5eb530b97f8bfb2642c43d43
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220736"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC 應用程式中的當地語系化資源：附屬 DLL

MFC 7.0 版和更新版本提供對附屬 Dll 的增強支援，這項功能有助於建立針對多種語言當地語系化的應用程式。 附屬 DLL 是[僅限資源的 dll](creating-a-resource-only-dll.md) ，其中包含針對特定語言當地語系化的應用程式資源。 當應用程式開始執行時，MFC 會自動載入最適合環境的當地語系化資源。 例如，您可以有一個應用程式，其中包含具有兩個附屬 Dll 的英文語言資源，其中一個是您的資源的法文翻譯，另一個包含德文轉譯。 當應用程式在英文版系統上執行時，它會使用英文資源。 如果在法文系統上執行，它會使用法文資源;如果在德文系統上執行，它會使用德文的資源。

為了支援 MFC 應用程式中的當地語系化資源，MFC 會嘗試載入附屬 DLL，其中包含當地語系化為特定語言的資源。 附屬 Dll 名為*ApplicationNameXXX*，其中*APPLICATIONNAME*是使用 MFC 的 .exe 或 .dll 的名稱，而*XXX*則是資來源語言的三個字母代碼（例如，' 繁體中文 ' 或 ' DEU '）。

MFC 會嘗試依序載入下列每一個語言的資源 DLL，並在找到時停止：

1. 目前使用者的預設 UI 語言，如同從 GetUserDefaultUILanguage （） WIN32 API 傳回。

1. 目前使用者的預設 UI 語言（也就是，ENC [加拿大英文]）會變成繁體中文 [美式英文]）。

1. 從 GetSystemDefaultUILanguage （） API 傳回的系統預設 UI 語言。 在其他平臺上，這是作業系統本身的語言。

1. 系統的預設 UI 語言，不含任何特定語言。

1. 具有3個字母代碼 LOC 的假語言。

如果 MFC 找不到任何附屬 Dll，則會使用應用程式本身所包含的任何資源。

例如，假設應用程式 LangExample 使用 MFC，並在多個使用者介面系統上執行;系統 UI 語言是繁體中文 [美式英文]，而目前使用者的 UI 語言設定為 FRC [加拿大法文]。 MFC 會依下列順序尋找下列 Dll：

1. LangExampleFRC （使用者的 UI 語言）。

1. LangExampleFRA （不含子語言的使用者 UI 語言，在此範例中為法文（法國））。

1. LangExampleENU （系統的 UI 語言）。

1. LangExampleLOC。

如果找不到這些 Dll，MFC 會使用 LangExample 中的資源。

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)<br/>
[TN057：MFC 元件的當地語系化](../mfc/tn057-localization-of-mfc-components.md)
