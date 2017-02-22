---
title: "其他語言的精靈支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.EastAsianLanguages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 專案的語言支援"
  - "專案 [C++], 語言支援"
  - "精靈 [C++], 語言支援"
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 其他語言的精靈支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您安裝 Visual Studio 時，安裝應用程式會偵測列在系統中的地區設定 \(Locale\) 並安裝適合地區設定的語言範本。  例如，安裝程式會為西歐地區設定安裝英文、法文、義大利文、西班牙文及德文。  這些語言會出現在 MFC 應用程式精靈的[應用程式類型](../mfc/reference/application-type-mfc-application-wizard.md)頁面上 \[資源語言\] 清單。  
  
## 語言範本  
 由於範本是以 ANSI 編碼方式為基礎，而且不是所有資源都可以在所有系統上編輯，因此不會在所有系統上安裝所有範本。  例如，依預設您無法在法文系統上編輯日文資源。  
  
 如果您使用 Windows 2000 或更新的版本，想要建立其他語言的 MFC 應用程式，則必須從 Visual Studio Installer 媒體 \(光碟 1\) 將適當語言的範本目錄複製到您的系統。  
  
> [!NOTE]
>  若要編輯已建立的專案，您必須將系統地區設定 \(locale\) 設定為選取語言的適當地區設定。  
  
 每個範本在 \\Microsoft Visual Studio .NET 2003\\Vc7\\VCWizards\\mfcappwiz\\templates\\ 目錄中都被指派了一個資料夾，如下表所示。  若要存取需要的語言範本，請將適當的資料夾複製到電腦上的 \\mfcappwiz\\templates\\ 目錄。  一旦複製資料夾，語言就會出現在 MFC 應用程式精靈的 \[**應用程式類型**\] 頁面上的 \[資源語言\] 清單當中。  
  
### Visual Studio .NET 中所提供的語言範本  
  
|Language|範本|  
|--------------|--------|  
|中文 \(繁體\)|1028|  
|中文 \(簡體\)|2052|  
|英文|1033|  
|法文|1036|  
|德文|1031|  
|義大利文|1040|  
|日文|1041|  
|韓文|1042|  
|西班牙文|3082|  
  
## Visual C\+\+ 精靈所產生檔案的格式  
 已安裝的 Visual Studio 語言版本與系統地區設定不符時，Visual C\+\+ 精靈將會產生 Unicode 的專案。  例如，當 Visual Studio 日文版是安裝在地區設定設定為日文以外任何語言的電腦上時，Visual C\+\+ 精靈會產生由 Unicode 檔案所組成的專案。  這在有安裝 Windows Multi\-Language \(MUI\) 封裝的機器上是很常見的。  
  
 此行為和系統地區設定與 Visual Studio 語言版本相同之系統的行為不同。  在這種情況下，將以系統字碼頁的 ANSI 建立專案檔。  
  
## 請參閱  
 [為 Visual C\+\+ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [建立和管理 Visual C\+\+ 專案](../ide/creating-and-managing-visual-cpp-projects.md)