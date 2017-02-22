---
title: "MFC 應用程式中的當地語系化資源：附屬 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 當地語系化 MFC"
  - "當地語系化 [C++], MFC 資源"
  - "當地語系化資源 [C++]"
  - "MFC DLL [C++], 當地語系化"
  - "多重語言支援 [C++]"
  - "僅含資源的 DLL [C++]"
  - "僅含資源的 DLL [C++], MFC 應用程式"
  - "資源 [MFC], 當地語系化"
  - "附屬 DLL [C++]"
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC 應用程式中的當地語系化資源：附屬 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 7.0 \(含\) 以後版本提供附屬 DLL \(Satellite DLL\) 的增強支援，即協助建立當地語系化成多國語言的應用程式的功能。  附屬 DLL 是指[僅含資源的 DLL](../build/creating-a-resource-only-dll.md)，其中包含當地語系化為某特定語言的應用程式資源。  當該應用程式開始執行時，MFC 會自動地載入最適合該作業環境的當地語系化資源。  例如，您可以讓包含英語資源的應用程式具有兩個附屬 DLL，其中一個包含法語翻譯的資源，另一個則包含德語翻譯的資源。  當這個應用程式在英語作業系統環境上執行時，它就會使用英語資源。  如果是在法語作業系統上執行，它就會使用法語資源；如果是在德語作業系統上執行，它就會使用德語資源。  
  
 為了在 MFC 應用程式中支援當地語系化資源，MFC 會嘗試載入一個包含已當地語系化為特定語言資源的附屬 DLL。  附屬 DLL 的命名方式是 *ApplicationNameXXX* .dll，其中 *ApplicationName* 是使用 MFC 的 .exe 或 .dll 的名稱，而 *XXX* 是資源所使用語言的三個字母代碼 \(例如 'ENU' 或 'DEU'\)。  
  
 MFC 會嘗試根據下列語言順序載入資源 DLL，並在找到該 DLL 後停止作業：  
  
1.  \(僅適用於 Windows 2000 或更新的版本\) 目前使用者的預設 UI 語言，由 GetUserDefaultUILanguage\(\) Win32 API 傳回。  
  
2.  \(僅適用於 Windows 2000 或更新的版本\) 不包含其他特定次語言 \(Sublanguage\) 的目前使用者的預設 UI 語言 \(也就是說，ENC \[Canadian English\] 會變成 ENU \[U.S.   English\]\)。  
  
3.  系統的預設 UI 語言。  在 Windows 2000 \(含\) 以後版本中，GetSystemDefaultUILanguage\(\) API 會傳回這個設定。  若在其他平台，便是指作業系統本身所使用的語言。  
  
4.  不包含其他特定次語言時的系統預設 UI 語言。  
  
5.  包含 3 個字母代碼 LOC 的仿造語言。  
  
 MFC 會在找不到任何附屬 DLL 時，使用該應用程式本身所包含的任何一種資源。  
  
 舉例來說，假設有個使用 MFC 的應用程式 LangExample.exe，正執行於 Windows 2000 多使用者介面系統；該系統 UI 語言是 ENU \[U.S.   English\]，而目前使用者的 UI 語言設定是 FRC \[Canadian French\]。  MFC 將會依照下列順序尋找下列的 DLL：  
  
1.  LangExampleFRC.dll \(使用者的 UI 語言\)。  
  
2.  LangExampleFRA.dll \(不包含次語言時的使用者 UI 語言，在這個範例中是指法語 \(法國\)\)。  
  
3.  LangExampleENU.dll \(系統的 UI 語言\)。  
  
4.  LangExampleLOC.dll.  
  
 如果找不到這些 DLL 的任何一個，MFC 就會使用 LangExample.exe 的資源。  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)   
 [TN057：MFC 元件的當地語系化](../mfc/tn057-localization-of-mfc-components.md)