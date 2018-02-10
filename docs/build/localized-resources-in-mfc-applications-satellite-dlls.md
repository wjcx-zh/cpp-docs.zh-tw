---
title: "MFC 應用程式中的當地語系化資源： 附屬 Dll |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc97e73998c581a40ed7d344b1ade5ca90b94ac2
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC 應用程式中的當地語系化資源：附屬 DLL
MFC 7.0 和更新的版本會提供對附屬 Dll，協助建立當地語系化成多國語言的應用程式的功能的增強的支援。 附屬 dll[資源專用 DLL](../build/creating-a-resource-only-dll.md) ，其中包含特定語言的當地語系化的應用程式的資源。 當應用程式開始執行時，MFC 會自動載入當地語系化的資源，則最適合的環境。 例如，您可能會有兩個附屬 Dll，其中包含您的資源和另一個包含德文轉譯法文翻譯的英文語言資源的應用程式。 在英文語言的系統上執行應用程式時，它會使用英文的資源。 如果法文的系統上執行，它會使用法文的資源;如果安裝德文系統上執行，它會使用德文的資源。  
  
 若要支援 MFC 應用程式時，MFC 會嘗試載入附屬 DLL 中的當地語系化的資源包含已當地語系化資源設定特定的語言。 附屬 Dll 會名為*ApplicationNameXXX*.dll，其中*ApplicationName* .exe 或.dll 使用 MFC，名稱和*XXX*是語言的三個字母代碼資源 （例如，'繁體中文' 或 '德文'）。  
  
 MFC 會嘗試依序停止時發現下列語言的每個載入的資源 DLL:  
  
1. 目前使用者的預設 UI 語言，傳回的 GetUserDefaultUILanguage() Win32 API。  
  
2.  沒有任何特定次語言，目前使用者的預設 UI 語言 （也就是 ENC [加拿大英文] 變成 [美國繁體中文英文]）。  
  
3.  系統的預設 UI 語言，傳回的 GetSystemDefaultUILanguage() API。 在其他平台，這是作業系統本身的語言。  
  
4.  系統的預設 UI 語言，沒有任何特定次語言。  
  
5.  具有 3 個字母代碼 LOC 假語言  
  
 如果 MFC 找不到任何附屬 Dll，它會使用任何資源都包含在應用程式本身。  
  
 例如，假設 LangExample.exe 應用程式使用 MFC，並會在系統上執行多個使用者介面。系統 UI 語言是繁體中文 [美國英文] 和目前使用者的 UI 語言設定為 FRC [加拿大法文]。 MFC 會尋找下列 Dll 順序如下：  
  
1.  LangExampleFRC.dll （使用者的 UI 語言）。  
  
2.  LangExampleFRA.dll （不含次語言，在此範例為法文 （法國） 使用者的 UI 語言。  
  
3.  LangExampleENU.dll （系統 UI 語言）。  
  
4.  LangExampleLOC.dll。  
  
 如果找到任何這些 Dll，MFC 會 LangExample.exe 中使用的資源。  
  
## <a name="see-also"></a>請參閱  
 [Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)   
 [TN057：MFC 元件的當地語系化](../mfc/tn057-localization-of-mfc-components.md)