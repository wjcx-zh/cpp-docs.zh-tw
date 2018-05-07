---
title: 其他語言的精靈支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.EastAsianLanguages
dev_langs:
- C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75aafd7177c3799c17b75419fd5ab9f54af91d35
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="wizard-support-for-other-languages"></a>其他語言的精靈支援
當您安裝 Visual Studio 時，安裝應用程式偵測到您的系統中所列的地區設定，並安裝適當的語言或多個樣板的地區設定。 例如，如西歐地區設定，安裝程式會安裝英文、 法文、 義大利文、 西班牙文和德文。 這些語言會出現在**資源語言**清單[應用程式類型](../mfc/reference/application-type-mfc-application-wizard.md)MFC 應用程式精靈頁面。  
  
## <a name="language-templates"></a>語言的範本  
 範本是 ANSI 編碼方式為基礎，且並非所有的資源可供編輯所有系統上所有的系統上安裝不是所有範本。 例如，根據預設，您無法編輯法文的系統上的日文資源。  
  
 如果您使用的 Windows 2000 或更新版本，而且您想要建立 MFC 應用程式中另一種語言，則您必須複製適當的語言的範本目錄從 Visual Studio 安裝程式媒體 (磁碟 1) 您的系統。  
  
> [!NOTE]
>  若要編輯建立的專案，您必須設定您的系統地區設定所選取語言的適當地區設定。  
  
 此範本是每個指派的資料夾 \Microsoft Visual Studio.NET 2003\Vc7\VCWizards\mfcappwiz\templates\ 目錄中，如下表中所列。 若要存取的所需的語言的範本，將複製到您的電腦上的 \mfcappwiz\templates\ 目錄的適當的資料夾。 一旦複製資料夾的語言會出現在**資源語言**清單**應用程式類型**MFC 應用程式精靈頁面。  
  
### <a name="language-templates-provided-in-visual-studio-net"></a>Visual Studio.NET 中提供的語言範本  
  
|語言|範本|  
|--------------|--------------|  
|和 SharePoint 2010 顯示的|1028|  
|中文 (簡體)|2052|  
|英文|1033|  
|法文|1036|  
|德文|1031|  
|義大利文|1040|  
|日文|1041|  
|韓文|1042|  
|西班牙文|3082|  
  
## <a name="format-of-visual-c-wizard-generated-files"></a>Visual c + + 精靈產生的檔案格式  
 Visual c + + 精靈會以 Unicode 產生專案，Visual Studio 的已安裝的語言版本不相符的系統地區設定時。 例如，已設定為日文以外任何語言的地區設定的電腦上安裝日文版的 Visual Studio 時，則 Visual c + + 精靈會產生專案 Unicode 檔案所組成。 這是常見使用 Windows 多語系 (MUI) 套件設定的電腦上。  
  
 此行為不同於系統的系統地區設定是語言版本的 Visual Studio 相同設定。 在此情況下，專案檔將 ANSI 中建立，在系統字碼頁。  
  
## <a name="see-also"></a>另請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [建立和管理 Visual C++ 專案](../ide/creating-and-managing-visual-cpp-projects.md)