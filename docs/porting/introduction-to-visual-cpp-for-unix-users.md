---
title: "針對 UNIX 使用者的 Visual C++ 簡介 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7c75629d56e6d8e5291b7d1f7cca9995ab9a50da
ms.openlocfilehash: d8515fc613f95ae5d6395e33b49482488bcc488d
ms.lasthandoff: 02/24/2017

---
# <a name="introduction-to-visual-c-for-unix-users"></a>針對 UNIX 使用者的 Visual C++ 簡介
本主題提供資訊給剛開始使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]，並想更有效率使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 的 UNIX 使用者。  
  
## <a name="getting-started-on-the-command-line"></a>從命令列開始使用  
 您可以透過與使用 UNIX 命令列環境類似的方式，從命令列使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]。 您可以從命令提示字元，使用命令列 C 和 C++ 編譯器 (CL.EXE) 和工具進行編譯，包括 Microsoft 版的 UNIX make 公用程式 NMAKE.EXE。  
  
 在 UNIX 中，命令會安裝在通用資料夾中，例如 /usr/bin。 在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 中，命令列工具會安裝在您的安裝目錄 VC\bin 中 (Program Files\Microsoft Visual Studio 8\VC\bin 的一般安裝位置)。 若要使用命令列工具，請執行位於安裝目錄 Common7\Tools 中的 vsvars32.bat。 這會將 bin 目錄加入您的路徑，並設定從命令列編譯 Visual C++ 程式所需的其他路徑。 如需詳細資訊，請參閱[在命令列中建置](../build/building-on-the-command-line.md)和[逐步解說：在命令列上編譯原生 C++ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。  
  
> [!NOTE]
>  如果您從 [開始] 功能表使用 [Visual Studio 命令列提示字元] 開啟命令提示字元，系統會為您執行 vsvars32.bat。  
  
 為了利用 Visual Studio 偵錯工具、陳述式完成等更強大的功能，您需要使用這個開發環境。  
  
## <a name="debugging-your-code"></a>偵錯您的程式碼  
 如果您使用命令列並在開發工作站上執行應用程式，當您的程式碼遇到記憶體存取違規、未處理的例外狀況或其他無法復原的錯誤時，便會顯示一個可執行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 偵錯工具的對話方塊。 如果您按一下 [確定]，則會啟動 Visual Studio 開發環境，並將偵錯工具開啟到失敗點。 您可以透過這個方式來偵錯應用程式，在這種情況下，只有在以 [/Z7、/Zi、/ZI (偵錯資訊格式)](../build/reference/z7-zi-zi-debug-information-format.md) 參數編譯時，才能使用原始程式碼。 如需詳細資訊，請參閱[偵錯原生程式碼](/visualstudio/debugger/debugging-native-code)和[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
## <a name="using-the-development-environment"></a>使用開發環境  
 使用開發環境編輯和建置「專案」中的原始程式碼會比較容易。 專案是來源和相關檔案的集合，這些檔案會編譯成一個單位，例如程式庫或可執行檔。 專案也包含檔案建置方式的相關資訊。 專案的相關資訊會儲存在副檔名為 .prj 的專案檔中。  
  
 應用程式是由多個程式庫和可執行檔所組成，並儲存在屬於單一「方案」的多個專案中，其中每個程式庫和可執行檔可能是以一組不同的編譯器選項，或甚至不同的語言所建置。 方案是將多個專案群組在一起的抽象容器。 方案的相關資訊會儲存在副檔名為 .sln 的方案檔中。 如需詳細資訊，請參閱 [Visual Studio 中的方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)和[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
## <a name="importing-your-existing-code"></a>匯入現有的程式碼  
 您可以透過 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 來使用現有的程式碼，並將其設定為以 Makefile 或不以 Makefile 編譯，再放入 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 專案。 如需詳細資訊，請參閱**從現有程式碼檔建立專案精靈**。 如需詳細資訊，請參閱[如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)。  
  
## <a name="creating-a-new-project"></a>建立新專案  
 您可以在開發環境中建立新專案。 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 提供許多樣板，其中的標準程式碼適用於各種常見專案。 您可以使用應用程式精靈，來產生具有適用於各種應用程式類型之程式碼大綱的專案。  
  
 您可以使用 [主控台應用程式 (Win32) 精靈]，從空專案開始。 選取 [空專案] 核取方塊。 您可以稍後再將新的和現有的檔案加入專案。  
  
 當您建立專案時，您必須命名專案。 根據預設，專案名稱等於從專案建置之動態連結程式庫 (DLL) 或可執行檔的名稱。 如需詳細資訊，請參閱[建立方案與專案](/visualstudio/ide/creating-solutions-and-projects)。  
  
## <a name="microsoft-specific-modifiers"></a>Microsoft 專有的修飾詞  
 Visual C++ 包含標準 C++ 程式語言的幾個擴充功能。 這些擴充功能可用來指定儲存類別屬性、函式呼叫慣例和基底定址等。 如需所有 Visual C++ 延伸模組的完整清單，請參閱 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)。  
  
 您可以使用 **/Za** 編譯器選項，來停用 C++ 的所有 Microsoft 特定延伸模組。 如果您想要撰寫程式碼以在多個平台上執行，建議使用這個選項。 如需 **/Za** 編譯器選項的詳細資訊，請參閱 [/Za、/Ze (停用語言延伸模組)](../build/reference/za-ze-disable-language-extensions.md)。 如需 Visual C++ 一致性的詳細資訊，請參閱[非標準行為](../cpp/nonstandard-behavior.md)。  
  
## <a name="precompiled-headers"></a>先行編譯標頭檔  
 Microsoft C 和 C++ 編譯器提供對任何 C 或 C++ 程式碼進行先行編譯的選項，包括內嵌程式碼。 您可以使用這項效能功能來編譯穩定的程式碼主體，並將程式碼的編譯狀態儲存在檔案中，然後在後續編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。 由於穩定的程式碼不需要重新編譯，因此每個後續編譯的速度會更快。  
  
 預設會在 **stdafx.h** 和 **stdafx.cpp** 檔案中指定所有先行編譯的程式碼。 除非您取消選取 [先行編譯標頭檔] 選項，否則 [新增專案精靈] 會自動為您建立這些檔案。 如需先行編譯標頭檔的詳細資訊，請參閱[建立先行編譯標頭檔](../build/reference/creating-precompiled-header-files.md)。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊，請參閱[從 UNIX 移植到 Win32](../porting/porting-from-unix-to-win32.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 導覽](http://msdn.microsoft.com/en-us/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)
