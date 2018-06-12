---
title: 其他語言的精靈支援 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332438"
---
# <a name="wizard-support-for-other-languages"></a>其他語言的精靈支援
當您安裝 Visual Studio 時，安裝應用程式會偵測到您系統中所列的地區設定，並安裝該地區設定的適當語言範本。 例如，對於西歐地區設定，安裝程式會安裝英文、法文、義大利文、西班牙文和德文。 這些語言會出現在 [MFC 應用程式精靈] 之[應用程式類型](../mfc/reference/application-type-mfc-application-wizard.md)頁面的 [資源語言] 清單中。  
  
## <a name="language-templates"></a>語言範本  
 並非所有系統上都會安裝所有範本，因為範本是以 ANSI 編碼方式為基礎，而且並非所有的資源都可在所有系統上編輯。 例如，根據預設，您無法在法文系統上編輯日文資源。  
  
 如果您使用 Windows 2000 或更新版本，且您想要以另一種語言建立 MFC 應用程式，則您必須從 Visual Studio 安裝程式媒體 (磁碟 1) 將適當語言的範本目錄複製到您的系統。  
  
> [!NOTE]
>  若要編輯建立的專案，您必須將系統地區設定設為所選取語言的適當地區設定。  
  
 每個範本都會被指派 \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\ 目錄中的一個資料夾，如下表中所列。 若要存取所需的語言範本，請將適當的資料夾複製到您電腦上的 \mfcappwiz\templates\ 目錄。 複製資料夾之後，語言便會出現在 MFC 應用程式精靈之**應用程式類型**頁面的 [資源語言] 清單中。  
  
### <a name="language-templates-provided-in-visual-studio-net"></a>Visual Studio .NET 中提供的語言範本  
  
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
  
## <a name="format-of-visual-c-wizard-generated-files"></a>Visual C++ 精靈產生之檔案的格式  
 Visual Studio 的已安裝語言版本不符合系統地區設定時，Visual C++ 精靈會以 Unicode 產生專案。 例如，日文版的 Visual Studio 安裝在已設定為日文以外任何語言之地區設定的電腦上時，Visual C++ 精靈會產生由 Unicode 檔案所組成的專案。 這常見於已安裝 Windows 多語系 (MUI) 套件的電腦上。  
  
 此行為不同於設定時使得系統地區設定與 Visual Studio 語言版本相同的系統。 在此情況下，專案檔將以系統字碼頁的 ANSI 建立。  
  
## <a name="see-also"></a>請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [建立和管理 Visual C++ 專案](../ide/creating-and-managing-visual-cpp-projects.md)