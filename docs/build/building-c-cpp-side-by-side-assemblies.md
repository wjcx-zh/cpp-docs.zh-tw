---
title: 建置 C/C++ 並存組件
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493332"
---
# <a name="building-cc-side-by-side-assemblies"></a>建置 C/C++ 並存組件

[並存元件](/windows/win32/SbsCs/about-side-by-side-assemblies-)是可供應用程式在執行時間使用的資源集合（一組 dll、windows 類別、COM 伺服器、類型程式庫或介面）。 在元件中重新封裝 Dll 的主要優點是，應用程式可以同時使用多個版本的元件，而且可以在更新版本時服務目前安裝的元件。

C + + 應用程式可能會在應用程式的不同部分使用一或多個 Dll。 在執行時間，Dll 會載入到主要進程中，並執行必要的程式碼。 應用程式會依賴作業系統來尋找要求的 Dll、瞭解需要載入哪些其他相依 Dll，然後將它們與要求的 DLL 一起載入。 在 windows XP、Windows Server 2003 和 Windows Vista 之前的 Windows 作業系統版本中，作業系統載入器會在應用程式的本機資料夾或系統路徑上指定的另一個資料夾中，搜尋相依的 Dll。 在 Windows XP、Windows Server 2003 和 Windows Vista 上，作業系統載入器也可以使用[資訊清單](/windows/win32/sbscs/manifests)檔案搜尋相依的 dll，並搜尋包含這些 dll 的並存元件。

根據預設，當 DLL 以 Visual Studio 建立時，它會將[應用程式資訊清單](/windows/win32/SbsCs/application-manifests)內嵌為 RT_MANIFEST 資源，其識別碼等於2。 就像是可執行檔，此資訊清單會描述此 DLL 在其他元件上的相依性。 這假設 DLL 不是並存元件的一部分，而且相依于此 DLL 的應用程式不會使用應用程式資訊清單來載入它，而是依賴作業系統載入器在系統路徑上尋找此 DLL。

> [!NOTE]
> 使用應用程式資訊清單的 DLL 必須將資訊清單內嵌為識別碼等於2的資源，這是很重要的。 如果 DLL 在執行時間以動態方式載入（例如，使用[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)函式），作業系統載入器會載入 dll 資訊清單中指定的相依元件。 在`LoadLibrary`呼叫期間，不會檢查 dll 的外部應用程式資訊清單。 如果資訊清單不是內嵌的，載入器可能會嘗試載入不正確的元件版本，或找不到尋找相依元件。

一或多個相關的 Dll 可以使用對應的[組件資訊清單](/windows/win32/SbsCs/assembly-manifests)重新封裝成並存元件，其中描述哪些檔案會形成元件，以及元件在其他並存元件上的相依性。

> [!NOTE]
> 如果元件包含一個 DLL，建議您將組件資訊清單內嵌在此 DLL 中，做為 ID 等於1的資源，並為私用元件提供與 DLL 相同的名稱。 例如，如果 DLL 的名稱是 mylibrary，則在資訊清單的\<assemblyIdentity> 元素中使用的 name 屬性值也可能是 mylibrary。 在某些情況下，當程式庫具有 .dll 以外的副檔名時（例如，MFC ActiveX 控制項專案會建立 .ocx 程式庫），可以建立外部組件資訊清單。 在此情況下，元件的名稱和資訊清單必須與 DLL 的名稱不同（例如，MyAssembly、MyAssembly 和 mylibrary）。 不過，仍建議您將這類程式庫重新命名為具有副檔名 .dll，並將資訊清單內嵌為資源，以減少此元件未來的維護成本。 如需作業系統如何搜尋私用元件的詳細資訊，請參閱[元件搜尋順序](/windows/win32/SbsCs/assembly-searching-sequence)。

這項變更可能會允許部署對應的 Dll 作為應用程式本機資料夾中的[私用元件](/windows/win32/Msi/private-assemblies)，或當做 WinSxS 組件快取中的[共用元件](/windows/win32/Msi/shared-assemblies)。 必須遵循幾個步驟，才能達到此新元件的正確執行時間行為;它們會在[建立並存元件的指導方針](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies)中加以描述。 在正確撰寫元件之後，它可以部署為共用或私用元件，以及與其相依的應用程式。 將並存元件安裝為共用元件時，您可以遵循安裝 Win32 元件中所述的指導方針，[以在 WINDOWS XP 上並存共用](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp)，或使用[合併模組](/windows/win32/msi/merge-modules)。 將並存元件安裝為私用元件時，您可以直接將對應的 DLL、資源和組件資訊清單複製到目的電腦上的應用程式本機資料夾，以確保載入器可以在執行時間找到這個元件（請參閱[元件搜尋順序](/windows/win32/SbsCs/assembly-searching-sequence)）。 另一種方式是使用[Windows Installer](/windows/win32/Msi/windows-installer-portal) ，並遵循安裝 Win32 元件中所述的指導方針，在[Windows XP 上進行應用程式的私用](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp)。

## <a name="see-also"></a>請參閱

[建立 C/c + + 隔離應用程式](building-c-cpp-isolated-applications.md)<br/>
[建立 C/c + + 隔離應用程式和並存元件](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
