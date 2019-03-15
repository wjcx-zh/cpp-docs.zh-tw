---
title: 建置 C/C++ 並存組件
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 037fde58366ea4548ce3c7ff56c38cfc1a58aa17
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815186"
---
# <a name="building-cc-side-by-side-assemblies"></a>建置 C/C++ 並存組件

A[並排顯示組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-)是資源的集合-一組 Dll、 windows 類別、 COM 伺服器、 類型程式庫或介面 — 適用於應用程式在執行階段使用。 Dll 重新封裝組件中的主要優點是，同時應用程式可以使用多個版本的組件，並可服務目前已安裝的組件的更新版本。

Visual c + + 應用程式可能使用應用程式的不同部分中的一或多個 Dll。 在執行階段 Dll 會載入到主要的處理程序，並執行必要的程式碼。 應用程式依賴作業系統來尋找要求的 Dll、 了解什麼其他相依的 Dll 必須載入，然後將它們載入要求的 DLL 一起。 在 Windows 作業系統版本早於 Windows XP、 Windows Server 2003 和 Windows Vista 作業系統載入器會搜尋相依的 Dll，應用程式的本機資料夾或指定系統路徑上的另一個資料夾中。 在 Windows XP、 Windows Server 2003 和 Windows Vista，作業系統載入器也可以搜尋使用的相依 Dll[資訊清單](/windows/desktop/sbscs/manifests)檔案，並包含這些 Dll 的並排顯示組件的搜尋。

根據預設，當 DLL 以 Visual Studio 中，它會有[應用程式資訊清單](/windows/desktop/SbsCs/application-manifests)內嵌做為 RT_MANIFEST 資源 id 等於 2。 如同可執行檔，此資訊清單會描述此 dll 的相依性，對其他組件。 這是假設 DLL 不是並排顯示組件的一部分，並不會相依於此 DLL 的應用程式使用應用程式資訊清單載入它，而是依賴作業系統載入器的系統路徑上找到此 DLL。

> [!NOTE]
> 請務必針對使用應用程式資訊清單有資訊清單內嵌為資源 id 等於 2 的 DLL。 如果在執行階段以動態方式載入的 DLL (例如，使用[LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)函式)，作業系統載入器載入 DLL 的資訊清單中指定的相依組件。 Dll 的外部應用程式資訊清單不會檢查期間`LoadLibrary`呼叫。 如果沒有內嵌資訊清單，則載入器可能會嘗試載入不正確的組件的版本，或在無法找到相依的組件。

一或多個相關可以重新封裝成有對應的並排顯示組件的 Dll[組件資訊清單](/windows/desktop/SbsCs/assembly-manifests)，其中描述哪些檔案形成上其他的並存組件，以及組件的相依性組件。

> [!NOTE]
> 如果組件包含一個 DLL 時，建議您組件資訊清單嵌入這個 DLL 做為資源識別碼等於 1，並提供私用組件與 DLL 相同的名稱。 例如，如果 DLL 的名稱是 mylibrary.dll，name 屬性的值用於\<組件識別 > 的資訊清單的項目也可以是 mylibrary。 在某些情況下，當文件庫副檔名為.dll 以外 （例如，MFC ActiveX 控制項專案建立.ocx 程式庫） 可以建立的外部組件資訊清單。 在此情況下，組件和其資訊清單的名稱必須不同於 DLL （例如，MyAssembly，MyAssembly.manifest 和 mylibrary.ocx） 的名稱。 不過仍建議命名有 extension.dll，並將資訊清單內嵌為資源，以降低未來的維護成本，此組件的這類程式庫。 如需作業系統如何搜尋私用組件的詳細資訊，請參閱[組件搜尋序列](/windows/desktop/SbsCs/assembly-searching-sequence)。

這項變更可能會允許部署為相對應的 Dll[私用組件](/windows/desktop/Msi/private-assemblies)應用程式本機資料夾中，或作為[共用組件](/windows/desktop/Msi/shared-assemblies)WinSxS 組件快取。 幾個步驟具有可供遵循以達到正確的執行階段行為，這個新的組件;將描述這些[建立並排顯示組件的指導方針](/windows/desktop/SbsCs/guidelines-for-creating-side-by-side-assemblies)。 正確地撰寫組件之後，它可部署為任一的共用或私用組件相依於它的應用程式一起。 安裝時並排顯示組件做為共用的組件，貴用戶中的指導方針所述任一個後續[安裝的 Windows XP 上的並排顯示共用的 Win32 組件](/windows/desktop/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp)，或使用[合併模組](/windows/desktop/msi/merge-modules). 安裝時並排顯示組件做為私用組件，您可能只複製相對應的 DLL、 資源和組件資訊清單，做為安裝程序的一部分在目標電腦上的應用程式本機資料夾以確保這個組件可以在執行階段載入器找到 (請參閱[組件搜尋序列](/windows/desktop/SbsCs/assembly-searching-sequence))。 另一種方式是使用[Windows Installer](/windows/desktop/Msi/windows-installer-portal)並遵循所述的指導方針[私人使用的 Windows XP 上的應用程式的 Win32 組件安裝](/windows/desktop/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp)。

## <a name="see-also"></a>另請參閱

[建置C/C++ 隔離應用程式](building-c-cpp-isolated-applications.md)<br/>
[建置 C/C++ 隔離應用程式和並存組件](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
