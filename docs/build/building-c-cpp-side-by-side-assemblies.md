---
title: "建置 C/C++ 並存組件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "並存應用程式 [C++]"
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
caps.latest.revision: 18
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建置 C/C++ 並存組件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[並存組件](_win32_side_by_side_assemblies)是資源的集合，是一組 DLL、Windows 類別、COM 伺服器、型別程式庫或介面，可供應用程式在執行階段使用。  將 DLL 重新封裝在組件中的主要優點在於應用程式可以同時使用多個版本的組件，而且如果有了版本更新，就可以提供目前新安裝的組件的服務。  
  
 Visual C\+\+ 應用程式可能會在應用程式的各個不同部位使用一個或數個 DLL。  在執行階段，DLL 會載入到主處理序中，而且會執行必要的程式碼。  應用程式依賴作業系統來尋找所要求的 DLL，因此，要了解必須載入哪些其他的相依 DLL，然後將這些 DLL 與要求的 DLL 一起載入。  在早於 Windows XP、Windows Server 2003 和 Windows Vista 的 Windows 作業系統中，作業系統載入器會在應用程式的本機資料夾或系統路徑所指定的其他資料夾中搜尋相依 DLL。  在 Windows XP、Windows Server 2003 和 Windows Vista 中，作業系統載入器也可以使用[資訊清單](http://msdn.microsoft.com/library/aa375365)檔來搜尋相依 DLL 以及包含這些 DLL 的並存組件。  
  
 根據預設，當使用 Visual Studio 建置 DLL 時，它會有一個內嵌為 RT\_MANIFEST 資源 \(其 ID 等於 2\) 的[應用程式資訊清單](http://msdn.microsoft.com/library/aa374191)。  就像是可執行檔一樣，這個資訊清單會描述這個 DLL 對其他組件的相依性。  這是假設此 DLL 並非並存組件的一部分，而依賴此 DLL 的應用程式也不會使用應用程式資訊清單以載入它，而是依賴作業系統載入器在系統路徑上尋找這個 DLL。  
  
> [!NOTE]
>  DLL 要使用應用程式資訊清單，才能夠將此資訊清單內嵌為資源 \(且 ID 等於 2\)，這一點很重要。  如果在執行階段動態載入此 DLL \(例如，使用 [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175) 函式\)，則作業系統載入器會載入此 DLL 的資訊清單中指定的相依組件。  在 `LoadLibrary` 呼叫期間，並不會查看 DLL 的外部應用程式資訊清單。  如果不是內嵌式的資訊清單，載入器可能會試圖載入不正確的組件版本，或者是無法找到相依組件。  
  
 一個或數個相關的 DLL 可以使用相對應的[應用程式資訊清單](http://msdn.microsoft.com/library/aa374219) \(其可描述哪些檔案組成這個組件，以及這個組件對其他並存組件的相依性\)，而重新封裝成並存組件。  
  
> [!NOTE]
>  如果某個組件包含一個 DLL，建議您將這個組件資訊清單當做資源 \(ID 等於 1\) 內嵌到這個 DLL 中，並為此私用組件提供與此 DLL 相同的名稱。  例如，如果 DLL 的名稱是 mylibrary.dll，則資訊清單的 \<assemblyIdentity\> 項目中所用的名稱屬性的值也可以是 mylibrary。  在某些情況下，如果程式庫的副檔名並不是 .dll \(例如，MFC ActiveX 控制項專案會建立 .ocx 程式庫\)，則可以建立外部組件資訊清單。  在這種情況下，組件與其資訊清單的名稱必須和 DLL 的名稱不同 \(例如，MyAssembly、MyAssembly.manifest 與 mylibrary.ocx\)。  不過，還是要建議您重新命名這樣的程式庫，讓它具有 .dll 的副檔名，並將資訊清單內嵌為資源，以降低未來維護這個組件的成本。  如需作業系統如何搜尋私用組件的詳細資訊，請參閱[組件搜尋序列](http://msdn.microsoft.com/library/aa374224)。  
  
 這項變更可以讓您將相對應的 DLL 當成[私用組件](_win32_private_assemblies)部署在應用程式本機資料夾中，或者是當成[共用組件](https://msdn.microsoft.com/en-us/library/aa375996.aspx)部署在 WinSxS 組件快取區中。  您必須執行數個步驟才能讓這個新的組件達成正確的執行階段行為；這些步驟會在[建立並存組件的方針](http://msdn.microsoft.com/library/aa375155)中加以說明。  正確地撰寫組件之後，就可以和依賴它的應用程式一起將它部署為共用組件或私用組件。  安裝並存組件做為共用組件時，您可以遵循[在 Windows XP 中安裝 Win32 組件以供並存共用](http://msdn.microsoft.com/library/aa369532)中說明的方針，或者使用[合併模組](http://msdn.microsoft.com/library/aa369820)。  安裝並存組件做為私用組件時，您可以在安裝時直接將相對應的 DLL、資源和組件資訊清單複製到目標電腦的應用程式本機資料夾，以確定載入器可以在執行階段找到這個組件 \(請參閱[組件搜尋序列](http://msdn.microsoft.com/library/aa374224)\)。  另外還有一種方式，就是使用 [Windows Installer](http://msdn.microsoft.com/library/cc185688) 並遵循[在 Windows XP 中安裝 Win32 組件以供私人使用應用程式](http://msdn.microsoft.com/library/aa369534)中的方針。  
  
## 請參閱  
 [部署範例](../ide/deployment-examples.md)   
 [建置 C\/C\+\+ 隔離應用程式](../build/building-c-cpp-isolated-applications.md)   
 [建置 C\/C\+\+ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)