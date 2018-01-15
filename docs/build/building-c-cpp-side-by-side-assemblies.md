---
title: "建置 C/c + + 並存組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c54f0e3b8bceff3daa92ecb3e0ee46d7fbeb666
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="building-cc-side-by-side-assemblies"></a>建置 C/C++ 並存組件
A [-並存組件](http://msdn.microsoft.com/library/windows/desktop/ff951640)是資源集合 — 的 Dll、 windows 類別、 COM 伺服器、 類型程式庫或介面群組 — 適用於應用程式在執行階段使用。 將 Dll 重新封裝組件中的主要優點是在同一時間應用程式可以使用多個版本的組件，並可服務目前已安裝的組件的更新版本。  
  
 Visual c + + 應用程式可能使用不同的部分應用程式中的一或多個 Dll。 在執行階段 Dll 會載入到主要程序，並執行必要的程式碼。 應用程式依賴若要尋找要求的 Dll，請了解哪些其他相依的 Dll 必須載入，然後將它們載入要求的 DLL 以及作業系統。 上的 Windows 作業系統版本早於 Windows XP、 Windows Server 2003 和 Windows Vista 中，作業系統載入器會搜尋應用程式的本機資料夾或另一個指定的系統路徑的資料夾中的相依 Dll。 在 Windows XP、 Windows Server 2003 和 Windows Vista，作業系統載入器也可以搜尋使用的相依 Dll[資訊清單](http://msdn.microsoft.com/library/windows/desktop/aa375365)檔案，並包含這些 Dll 的並存組件的搜尋。  
  
 根據預設，Visual Studio 中，以建立 DLL 時其具有[應用程式資訊清單](http://msdn.microsoft.com/library/windows/desktop/aa374191)內嵌做為 RT_MANIFEST 資源 ID 等於 2。 只適用於可執行檔，此資訊清單描述這個 DLL 的相依性的其他組件。 這會假設 DLL 不是由並存組件的一部分，而且相依於此 DLL 的應用程式不會使用應用程式資訊清單載入它，而是依賴作業系統載入器上找不到此 DLL 的系統路徑。  
  
> [!NOTE]
>  請務必針對使用應用程式資訊清單有資訊清單內嵌為資源 id 等於 2 的 DLL。 如果在執行階段動態載入的 DLL (例如，使用[LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)函式)，作業系統載入器載入 DLL 的資訊清單中指定的相依組件。 Dll 的外部應用程式資訊清單不會檢查期間`LoadLibrary`呼叫。 如果沒有內嵌資訊清單，則載入器可能會嘗試載入的組件的版本不正確或無法找到相依組件。  
  
 一或多個相關可以重新封裝到-並存組件中相對應的 Dll[組件資訊清單](http://msdn.microsoft.com/library/windows/desktop/aa374219)，用來描述哪些檔案形成上其他的並存組件，以及組件的相依性組件。  
  
> [!NOTE]
>  如果組件包含一個 DLL 時，建議您組件資訊清單嵌入此 DLL 做為資源 id 等於 1，並提供私用組件 DLL 相同的名稱。 例如，如果 DLL 的名稱是 mylibrary.dll，名稱屬性的值中使用\<assemblyIdentity > 資訊清單的項目也可以是 mylibrary。 在某些情況下，當媒體櫃具有以外.dll 副檔名 （例如，MFC ActiveX 控制項專案建立.ocx 程式庫） 可以建立外部組件資訊清單。 在此情況下，組件和其資訊清單的名稱必須是不同的 DLL （例如，MyAssembly、 MyAssembly.manifest 和 mylibrary.ocx） 名稱。 不過仍建議命名 extension.dll，然後再將資訊清單內嵌為資源，以降低未來的維護成本，這個組件的這類程式庫。 如需有關系統如何搜尋私用組件的詳細資訊，請參閱[組件搜尋序列](http://msdn.microsoft.com/library/windows/desktop/aa374224)。  
  
 這項變更可能會允許部署為相對應的 Dll[私用組件](http://msdn.microsoft.com/library/windows/desktop/aa370850)在應用程式的本機資料夾，或做為[共用組件](http://msdn.microsoft.com/library/windows/desktop/aa371839)WinSxS 組件快取。 遵循才能達到正確的執行階段行為的這個新的組件; 有幾個步驟將描述這些[指導方針建立為並存組件](http://msdn.microsoft.com/library/windows/desktop/aa375155)。 正確地撰寫組件之後可以為其中一個共用或私用組件相依於它的應用程式一起部署。 安裝時的並存組件做為共用組件，貴用戶中所述的指導方針是遵循[安裝在 Windows XP 上的並行所共用的 Win32 組](http://msdn.microsoft.com/library/windows/desktop/aa369532)或使用[合併模組](http://msdn.microsoft.com/library/windows/desktop/aa369820). 安裝時的並存組件做為私用組件，您可能只複製相對應的 DLL、 資源和組件資訊清單，做為安裝程序的一部分應用程式本機資料夾的目標電腦上，確定這個組件可以在執行階段載入器找到 (請參閱[組件搜尋序列](http://msdn.microsoft.com/library/windows/desktop/aa374224))。 另一種方式是使用[Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688)並遵循所述的指導方針[安裝在 Windows XP 上的應用程式私用用於 Win32 組件](http://msdn.microsoft.com/library/windows/desktop/aa369534)。  
  
## <a name="see-also"></a>請參閱  
 [部署範例](../ide/deployment-examples.md)   
 [建置 C/c + + 隔離應用程式](../build/building-c-cpp-isolated-applications.md)   
 [建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)