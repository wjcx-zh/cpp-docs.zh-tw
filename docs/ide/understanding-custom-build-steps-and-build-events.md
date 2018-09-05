---
title: 了解自訂建置步驟和建置事件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16c1bdf088e0545292a672458c066364b5a47ff4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206291"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>了解自訂建置步驟和建置事件
在 Visual C++ 開發環境中，有三種基本方式可自訂建置流程：  
  
 **自訂建置步驟**  
 自訂建置步驟是與專案建立關聯的建置規則。 自訂建置步驟可以指定要執行的命令列、任何其他輸入或輸出檔案，以及要顯示的訊息。 如需詳細資訊，請參閱[如何：將自訂建置步驟新增至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)。  
  
 **自訂建置工具**  
 自訂建置工具是與一或多個檔案建立關聯的建置規則。 自訂建置步驟可以將輸入檔案傳遞至自訂建置工具，進而導致產生一或多個輸出檔案。 例如，MFC 應用程式中的說明檔是使用自訂建置工具所建置。 如需詳細資訊，請參閱[如何：將自訂建置工具新增至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)和[指定自訂建置工具](../ide/specifying-custom-build-tools.md)。  
  
 **建置事件**  
 建置事件可讓您自訂專案的組建。 有三種建置事件：*建置前*、*連結前*和*建置後*。 建置事件可讓您指定要在建置流程中的特定時間發生的動作。 例如，您可以使用建置事件，在專案完成建置後利用 **regsvr32.exe** 註冊一個檔案。 如需詳細資訊，請參閱[指定建置事件](../ide/specifying-build-events.md)。  
  
 [針對組建自訂進行疑難排解](../ide/troubleshooting-build-customizations.md)可協助您確保自訂建置步驟和建置事件如預期般執行。  
  
 自訂建置步驟或建置事件的輸出格式也可以增強工具的可用性。 如需詳細資訊，請參閱[格式化自訂建置步驟或建置事件的輸出](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md)。  
  
 建置事件和自訂建置步驟會依下列順序與其他建置步驟一起執行：  
  
1.  建置前事件  
  
2.  在個別檔案上自訂建置工具  
  
3.  MIDL  
  
4.  資源編譯器  
  
5.  C/C++ 編譯器  
  
6.  連結前事件  
  
7.  連結器或管理員 (視情況)  
  
8.  資訊清單工具  
  
9. BSCMake  
  
10. 在專案上自訂建置步驟  
  
11. 建置後事件  
  
 `custom build step on the project` 和 `post-build event` 會在所有其他建置流程完成後依序執行。  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中建置 C++ 專案](../ide/building-cpp-projects-in-visual-studio.md)   
 [建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)   
 [工具建置順序對話方塊](https://msdn.microsoft.com/6204c5b1-7ce9-4948-9ff6-0268642ee14c)